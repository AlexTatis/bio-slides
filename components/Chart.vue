<script setup lang="ts">
    import { Bar } from 'vue-chartjs'
    import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale, ChartOptions, ChartData } from 'chart.js'
    import { ref, computed, ComputedRef } from 'vue'
    import {
        Combobox,
        ComboboxInput,
        ComboboxOptions,
        ComboboxOption,
        ComboboxButton,
        TransitionRoot
    } from '@headlessui/vue'
    import { useFetch } from '@vueuse/core'

    const {data: countries} = await useFetch('https://api.v2.emissions-api.org/api/v2/countries.json').json<{ [key: string]: string }>()
    const countryNames = computed(() => [...new Set(Object.values(countries.value ?? ""))])

    let selected = ref(countryNames.value[0])
    let query = ref('')
    
    const countryCode = computed(() => Object.keys(countries.value ?? "")[Object.values(countries.value ?? "").indexOf(selected.value)])


    let filteredCountries = computed(() =>
        {
            return query.value === ''
                ? countryNames.value
                : countryNames.value.filter((country) =>
                    country
                    .toLowerCase()
                    .replace(/\s+/g, '')
                    .includes(query.value.toLowerCase().replace(/\s+/g, ''))
                )
        }
    )

    ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

    const coUrl = computed(() => `https://api.v2.emissions-api.org/api/v2/carbonmonoxide/average.json?country=${countryCode.value}&begin=2023-03-01&end=2023-04-01`)
    const o3Url = computed(() => `https://api.v2.emissions-api.org/api/v2/ozone/average.json?country=${countryCode.value}&begin=2023-03-01&end=2023-04-01`)

    type resData = { average: number, end: string, start: string }[]

    const { data: coData } =  await useFetch(coUrl, { refetch: true }).json<resData>()
    const { data: spainData } =  await useFetch('https://api.v2.emissions-api.org/api/v2/carbonmonoxide/average.json?country=ES&begin=2023-03-01&end=2023-04-01').json<resData>()
  
    //const { data: o3Data } =  await useFetch(o3Url, { refetch: true }).json<resData>()

    
    
    const chartOptions: ChartOptions<"bar"> = {
        responsive: true,
        scales: {
            x: {
                title: {
                    display: true,
                    text: "Día"
                }
            },
            y: {
                title: {
                    display: true,
                    text: "Concentración atmosférica (mol/m^2)"
                }
            }
        }
    }
    
    const chartData: ComputedRef<ChartData<"bar">> = computed(() => {
        
        coData.value?.sort((a, b) => a.start.localeCompare(b.start))
        
        coData.value?.forEach(e => {
            console.log(new Date(e.start))
        })

        return {
            labels: coData.value?.map(x => x.start.substring(8, 10)),
            datasets: [
                {
                    label: `CO de ${selected.value} (Marzo de 2023)`,
                    backgroundColor: '#93bd20',
                    // use the average values as data
                    data: (coData.value ?? []).map(x => x.average),
                },
                {
                    label: `CO de España`,
                    backgroundColor: '#f3bd20',
                    // use the average values as data
                    data: (spainData.value ?? []).map(x => x.average),
                }
            ]
        }
    }) 


</script>

<template>
    <div>
        <Combobox v-model="selected">
      <div class="relative mt-1">
        <div
          class="relative w-full overflow-hidden text-left bg-white rounded-lg shadow-md cursor-default focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75 focus-visible:ring-offset-2 focus-visible:ring-offset-teal-300 sm:text-sm"
        >
          <ComboboxInput
            class="w-full py-2 pl-3 pr-10 text-sm leading-5 text-gray-900 border-none focus:ring-0"
            :displayValue="(person: any) => person"
            @change="query = $event.target.value"
          />
          <ComboboxButton
            class="absolute inset-y-0 right-0 flex items-center pr-2"
          >
          </ComboboxButton>
        </div>
        <TransitionRoot
          leave="transition ease-in duration-100"
          leaveFrom="opacity-100"
          leaveTo="opacity-0"
          @after-leave="query = ''"
        >
          <ComboboxOptions
            class="absolute w-full py-1 mt-1 overflow-auto text-base bg-white rounded-md shadow-lg max-h-60 ring-1 ring-black ring-opacity-5 focus:outline-none sm:text-sm"
          >
            <div
              v-if="filteredCountries?.length === 0 && query !== ''"
              class="relative px-4 py-2 text-gray-700 cursor-default select-none"
            >
              Nothing found.
            </div>

            <ComboboxOption
              v-for="country in filteredCountries"
              as="template"
              :key="country"
              :value="country"
              v-slot="{ selected, active }"
            >
              <li
                class="relative py-2 pl-10 pr-4 cursor-default select-none"
                :class="{
                  'bg-teal-600 text-white': active,
                  'text-gray-900': !active,
                }"
              >
                <span
                  class="block truncate"
                  :class="{ 'font-medium': selected, 'font-normal': !selected }"
                >
                  {{ country }}
                </span>
                <span
                  v-if="selected"
                  class="absolute inset-y-0 left-0 flex items-center pl-3"
                  :class="{ 'text-white': active, 'text-teal-600': !active }"
                >
                 
                </span>
              </li>
            </ComboboxOption>
          </ComboboxOptions>
        </TransitionRoot>
      </div>
    </Combobox>
    </div>
    <Bar
    id="my-chart-id"
    :options="chartOptions"
    :data="chartData"
    />
</template>