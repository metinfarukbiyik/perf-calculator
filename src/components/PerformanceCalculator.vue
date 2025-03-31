<template>
  <div class="min-h-screen bg-[#fafafa] relative overflow-hidden">
    <!-- Background Pattern -->
    <div class="fixed inset-0 bg-[linear-gradient(to_right,#8080800a_1px,transparent_1px),linear-gradient(to_bottom,#8080800a_1px,transparent_1px)] bg-[size:24px_24px]"></div>
    <div class="fixed inset-0 bg-gradient-radial"></div>

    <div class="relative container mx-auto">
      <!-- Title -->
      <title>LiveChat Performans Hesaplama</title>

      <div class="max-w-3xl mx-auto py-4 px-4 sm:py-8 sm:px-6 lg:px-8">
        <!-- Header -->
        <div class="text-center mb-6 sm:mb-10">
          <h1 class="text-2xl sm:text-4xl font-bold tracking-tight bg-gradient-to-r from-blue-600 via-indigo-600 to-purple-600 bg-clip-text text-transparent">
            LiveChat Performans Hesaplama
          </h1>
          <p class="mt-2 sm:mt-3 text-sm sm:text-base text-gray-600 font-light px-4 max-w-xl mx-auto">
            MMA ve ACHT değerlerinizi girerek performans puanınızı hesaplayın
          </p>
        </div>

        <!-- Ana Kart -->
        <div class="bg-white rounded-xl sm:rounded-2xl shadow-lg overflow-visible mx-auto border border-gray-100">
          <!-- Input Alanları -->
          <div class="p-4 sm:p-6 lg:p-8">
            
            <div class="grid gap-4 sm:gap-6 sm:grid-cols-2">
              <!-- MMA Input -->
              <div class="w-full">
                <label class="block text-sm font-medium text-gray-700 mb-1">
                  MMA Değeri
                  <span class="ml-1 inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-blue-50 text-blue-800">
                    Hedef: 4.15
                  </span>
                </label>
                <div class="relative mt-1">
                  <input 
                    type="number" 
                    v-model="mmaValue" 
                    step="0.01"
                    placeholder="Örn: 4.15"
                    class="block w-full pl-4 pr-24 py-2.5 text-gray-900 placeholder-gray-400 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent transition duration-150 font-medium"
                  />
                  <div class="absolute inset-y-0 right-0 flex items-center">
                    <div class="h-full pr-3 flex items-center border-l border-gray-300 w-[100px] justify-end">
                      <div class="flex flex-col -space-y-px">
                        <button 
                          @click="mmaValue = (Number(mmaValue) + 0.01).toFixed(2)"
                          class="px-1.5 py-1 text-gray-500 hover:text-blue-600 focus:outline-none"
                        >
                          <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
                          </svg>
                        </button>
                        <button 
                          @click="mmaValue = (Number(mmaValue) - 0.01).toFixed(2)"
                          class="px-1.5 py-1 text-gray-500 hover:text-blue-600 focus:outline-none"
                        >
                          <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                          </svg>
                        </button>
                      </div>
                      <span class="text-sm text-gray-500 font-medium ml-2 w-12 text-center">MMA</span>
                    </div>
                  </div>
                </div>
              </div>

              <!-- ACHT Input -->
              <div class="w-full">
                <label class="block text-sm font-medium text-gray-700 mb-1">
                  ACHT Değeri
                  <span class="ml-1 inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-indigo-50 text-indigo-800">
                    Hedef: 500
                  </span>
                </label>
                <div class="relative mt-1">
                  <input 
                    type="number" 
                    v-model="achtValue"
                    step="1"
                    placeholder="Örn: 500"
                    class="block w-full pl-4 pr-24 py-2.5 text-gray-900 placeholder-gray-400 border border-gray-300 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition duration-150 font-medium"
                  />
                  <div class="absolute inset-y-0 right-0 flex items-center">
                    <div class="h-full pr-3 flex items-center border-l border-gray-300 w-[100px] justify-end">
                      <div class="flex flex-col -space-y-px">
                        <button 
                          @click="achtValue = (Number(achtValue) + 1).toString()"
                          class="px-1.5 py-1 text-gray-500 hover:text-indigo-600 focus:outline-none"
                        >
                          <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
                          </svg>
                        </button>
                        <button 
                          @click="achtValue = (Number(achtValue) - 1).toString()"
                          class="px-1.5 py-1 text-gray-500 hover:text-indigo-600 focus:outline-none"
                        >
                          <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                          </svg>
                        </button>
                      </div>
                      <span class="text-sm text-gray-500 font-medium ml-2 w-12 text-center">ACHT</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Devamsızlık Input -->
            <div class="mt-4 sm:mt-6 w-full">
              <label class="block text-sm font-medium text-gray-700 mb-1">
                Devamsızlık
                <span class="ml-1 inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-red-50 text-red-800">
                  Hedef: 0 gün
                </span>
              </label>
              <div class="relative mt-1">
                <input 
                  type="number" 
                  v-model="devamsizlik"
                  min="0"
                  step="1"
                  placeholder="Örn: 0"
                  class="block w-full pl-4 pr-24 py-2.5 text-gray-900 placeholder-gray-400 border border-gray-300 rounded-lg focus:ring-2 focus:ring-red-500 focus:border-transparent transition duration-150 font-medium"
                />
                <div class="absolute inset-y-0 right-0 flex items-center">
                  <div class="h-full pr-3 flex items-center border-l border-gray-300 w-[100px] justify-end">
                    <div class="flex flex-col -space-y-px">
                      <button 
                        @click="devamsizlik = Number(devamsizlik) + 1"
                        class="px-1.5 py-1 text-gray-500 hover:text-red-600 focus:outline-none"
                      >
                        <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
                        </svg>
                      </button>
                      <button 
                        @click="devamsizlik = Number(devamsizlik) - 1"
                        class="px-1.5 py-1 text-gray-500 hover:text-red-600 focus:outline-none"
                      >
                        <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                        </svg>
                      </button>
                    </div>
                    <span class="text-sm text-gray-500 font-medium ml-2 w-12 text-center">Gün</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- SGS ve UOH Checkbox'ları -->
            <div class="mt-4 sm:mt-6 space-y-4">
              <!-- SGS -->
              <div class="bg-gradient-to-r from-purple-50 to-indigo-50 border border-indigo-100 p-3 mb-4 rounded-xl text-center shadow-sm" role="alert">
                <div class="flex items-center justify-center">
                  <svg class="h-5 w-5 mr-2 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                  </svg>
                  <p class="font-semibold text-base text-indigo-700">SGS ve UOH'a Karşı ExtraJet Var!</p>
                </div>
              </div>
                  <div class="space-y-2">
                <div class="flex items-center">
                      <input
                        type="checkbox"
                    v-model="hasSGS"
                        class="h-4 w-4 text-orange-600 focus:ring-orange-500 border-gray-300 rounded transition-colors cursor-pointer"
                      />
                      
                  <label class="ml-2 block text-sm text-gray-700">
                    SGS Kesintisi
                    <span class="ml-1 inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-orange-50 text-orange-800">
                      -5 ile -60 puan arası
                    </span>
                  </label>
                </div>
                <div v-if="hasSGS" class="ml-6">
                  <div class="relative">
                    <button 
                      @click="(event) => toggleSGSDropdown(event)"
                      type="button"
                      class="relative w-full cursor-default rounded-lg bg-white py-1.5 sm:py-2.5 pl-3 sm:pl-4 pr-8 sm:pr-10 text-left border border-gray-300 focus:ring-2 focus:ring-orange-500 focus:border-transparent transition duration-150 text-xs sm:text-sm font-normal sm:font-medium"
                    >
                      <span v-if="selectedSGSReason.length > 0" class="flex items-center justify-between w-full">
                        <span class="block truncate text-gray-900">
                          {{ selectedSGSReason.map(id => sgsReasons.find(r => r.id === id)?.text).join(', ') }}
                        </span>
                        <span class="text-orange-600 ml-1 sm:ml-2">
                          -{{ selectedSGSReason.reduce((total, reasonId) => total + (sgsReasons.find(r => r.id === reasonId)?.puan || 0), 0) }}p
                        </span>
                      </span>
                      <span v-else class="block truncate text-gray-500">
                        Reason Seçiniz
                      </span>
                      <span class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-2 sm:pr-3">
                        <svg class="h-4 w-4 sm:h-5 sm:w-5 text-gray-400" viewBox="0 0 20 20" fill="none" stroke="currentColor">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 8l4 4 4-4" />
                        </svg>
                      </span>
                    </button>
                    <div 
                      v-if="isSGSOpen"
                      class="absolute z-50 mt-1 max-h-[300px] w-full overflow-auto rounded-lg bg-white py-1 shadow-xl ring-1 ring-black ring-opacity-5 focus:outline-none"
                      style="position: absolute; top: 100%; left: 0;"
                    >
                      <div 
                        v-for="reason in sgsReasons" 
                        :key="reason.id"
                        @click="(event) => selectSGSReason(reason.id, event)"
                        class="relative cursor-pointer select-none py-1.5 sm:py-2.5 pl-3 sm:pl-4 pr-8 sm:pr-10 hover:bg-orange-50 text-gray-900"
                        :class="{ 'bg-orange-50 text-orange-900': selectedSGSReason.includes(reason.id) }"
                      >
                        <span class="block truncate text-xs sm:text-sm font-normal sm:font-medium">{{ reason.text }}</span>
                        <span class="absolute inset-y-0 right-0 flex items-center pr-2 sm:pr-8 text-orange-600 text-xs sm:text-sm font-normal sm:font-medium">
                          -{{ reason.puan }}p
                        </span>
                      </div>
                    </div>
                  </div>
                </div>
                <div v-if="hasSGS && selectedSGSReason.length > 0" class="mt-2 text-sm text-gray-700 bg-orange-50 px-3 py-1.5 rounded-lg inline-block">
                  <span class="font-medium">Seçilen SGS reason sayısı:</span> {{ selectedSGSReason.length }}
                </div>
              </div>

              <!-- UOH -->
              <div class="space-y-2">
                <div class="flex items-center">
                  <input 
                    type="checkbox" 
                    v-model="hasUOH"
                    class="h-4 w-4 text-amber-600 focus:ring-amber-500 border-gray-300 rounded transition-colors cursor-pointer"
                  />
                  <label class="ml-2 block text-sm text-gray-700">
                    UOH Kesintisi
                    <span class="ml-1 inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-amber-50 text-amber-800">
                      -1 ile -60 puan arası
                    </span>
                      </label>
                </div>
                <div v-if="hasUOH" class="ml-6">
                  <div class="relative">
                    <button 
                      @click="(event) => toggleUOHDropdown(event)"
                      type="button"
                      class="relative w-full cursor-default rounded-lg bg-white py-1.5 sm:py-2.5 pl-3 sm:pl-4 pr-8 sm:pr-10 text-left border border-gray-300 focus:ring-2 focus:ring-amber-500 focus:border-transparent transition duration-150 text-xs sm:text-sm font-normal sm:font-medium"
                    >
                      <span v-if="selectedUOHReason.length > 0" class="flex items-center justify-between w-full">
                        <span class="block truncate text-gray-900">
                          {{ selectedUOHReason.map(id => uohReasons.find(r => r.id === id)?.text).join(', ') }}
                        </span>
                        <span class="text-amber-600 ml-1 sm:ml-2">
                          -{{ selectedUOHReason.reduce((total, reasonId) => total + (uohReasons.find(r => r.id === reasonId)?.puan || 0), 0) }}p
                        </span>
                      </span>
                      <span v-else class="block truncate text-gray-500">
                        Reason Seçiniz
                      </span>
                      <span class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-2 sm:pr-3">
                        <svg class="h-4 w-4 sm:h-5 sm:w-5 text-gray-400" viewBox="0 0 20 20" fill="none" stroke="currentColor">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 8l4 4 4-4" />
                        </svg>
                      </span>
                    </button>
                    <div 
                      v-if="isUOHOpen"
                      class="absolute z-50 mt-1 max-h-[300px] w-full overflow-auto rounded-lg bg-white py-1 shadow-xl ring-1 ring-black ring-opacity-5 focus:outline-none"
                      style="position: absolute; top: 100%; left: 0;"
                    >
                      <div 
                        v-for="reason in uohReasons" 
                        :key="reason.id"
                        @click="(event) => selectUOHReason(reason.id, event)"
                        class="relative cursor-pointer select-none py-1.5 sm:py-2.5 pl-3 sm:pl-4 pr-8 sm:pr-10 hover:bg-amber-50 text-gray-900"
                        :class="{ 'bg-amber-50 text-amber-900': selectedUOHReason.includes(reason.id) }"
                      >
                        <span class="block truncate text-xs sm:text-sm font-normal sm:font-medium">{{ reason.text }}</span>
                        <span class="absolute inset-y-0 right-0 flex items-center pr-2 sm:pr-8 text-amber-600 text-xs sm:text-sm font-normal sm:font-medium">
                          -{{ reason.puan }}p
                        </span>
                      </div>
                    </div>
                  </div>
                </div>
                <div v-if="hasUOH && selectedUOHReason.length > 0" class="mt-2 text-sm text-gray-700 bg-amber-50 px-3 py-1.5 rounded-lg inline-block">
                  <span class="font-medium">Seçilen UOH reason sayısı:</span> {{ selectedUOHReason.length }}
                </div>
              </div>
            </div>

            <!-- Hesapla Butonu -->
            <button 
              @click="calculatePerformance"
              class="mt-6 sm:mt-8 w-full inline-flex justify-center items-center px-4 sm:px-6 py-3.5 border border-transparent text-base font-medium rounded-xl text-white bg-gradient-to-r from-blue-600 to-indigo-700 hover:from-blue-700 hover:to-indigo-800 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 transition-all duration-200 transform hover:scale-[1.01] active:scale-[0.99] shadow-md"
            >
              <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 7h6m0 10v-3m-3 3h.01M9 17h.01M9 14h.01M12 14h.01M15 11h.01M12 11h.01M9 11h.01M7 21h10a2 2 0 002-2V5a2 2 0 00-2-2H7a2 2 0 00-2 2v14a2 2 0 002 2z" />
              </svg>
              Hesapla
            </button>
          </div>

          <!-- Sonuçlar -->
          <div v-if="result" class="border-t border-gray-100">
            <div class="p-4 sm:p-6 lg:p-8 space-y-4 sm:space-y-6">
              <!-- Girilen Değerler -->
              <div class="bg-gradient-to-br from-gray-50 to-gray-100 rounded-xl p-4 sm:p-6 shadow-sm hover:shadow-md transition-shadow duration-200">
                <div class="flex items-center justify-between mb-3 sm:mb-4">
                  <h4 class="text-sm sm:text-base font-medium text-gray-900">Girilen Değerler</h4>
                  <div class="text-gray-400 bg-white rounded-full p-2 shadow-sm">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h.01M12 12h.01M19 12h.01M6 12a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0z" />
                    </svg>
                  </div>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 sm:gap-4">
                  <div class="bg-white rounded-lg p-4 shadow-sm hover:shadow-md transition-shadow duration-200">
                    <div class="flex items-center justify-between">
                      <div class="text-sm font-medium text-gray-500">MMA</div>
                      <div class="text-blue-500 bg-blue-50 rounded-full p-1.5">
                        <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
                        </svg>
                      </div>
                    </div>
                    <div class="mt-2 text-xl font-semibold text-gray-900">{{ mmaValue }}</div>
                  </div>
                  <div class="bg-white rounded-lg p-4 shadow-sm hover:shadow-md transition-shadow duration-200">
                    <div class="flex items-center justify-between">
                      <div class="text-sm font-medium text-gray-500">ACHT</div>
                      <div class="text-indigo-500 bg-indigo-50 rounded-full p-1.5">
                        <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
                        </svg>
                      </div>
                    </div>
                    <div class="mt-2 text-xl font-semibold text-gray-900">{{ achtValue }}</div>
                  </div>
                  <div class="bg-white rounded-lg p-4 shadow-sm hover:shadow-md transition-shadow duration-200">
                    <div class="flex items-center justify-between">
                      <div class="text-sm font-medium text-gray-500">Devamsızlık</div>
                      <div class="text-red-500 bg-red-50 rounded-full p-1.5">
                        <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                      </div>
                    </div>
                    <div class="mt-2 text-xl font-semibold text-gray-900">{{ devamsizlik }} gün</div>
                  </div>
                </div>
              </div>

              <!-- Performans Puanları -->
              <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 sm:gap-4">
                <div class="bg-blue-50 rounded-xl p-4 sm:p-6 shadow-sm hover:shadow-md transition-shadow duration-200">
                  <div class="flex items-center justify-between">
                    <div>
                      <div class="text-sm text-blue-600 font-medium">MMA Puanı</div>
                      <div class="mt-1 text-2xl font-semibold text-blue-700">{{ result.mmaPuan.toFixed(1) }}</div>
                    </div>
                    <div class="text-blue-500 bg-blue-100 rounded-full p-2">
                      <svg class="w-4 h-4 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
                      </svg>
                    </div>
                  </div>
                  <div class="mt-1 text-sm text-blue-600 font-medium">Ağırlık: %80</div>
                </div>

                <div class="bg-indigo-50 rounded-xl p-4 sm:p-6 shadow-sm hover:shadow-md transition-shadow duration-200">
                  <div class="flex items-center justify-between">
                    <div>
                      <div class="text-sm text-indigo-600 font-medium">ACHT Puanı</div>
                      <div class="mt-1 text-2xl font-semibold text-indigo-700">{{ result.achtPuan.toFixed(1) }}</div>
                    </div>
                    <div class="text-indigo-500 bg-indigo-100 rounded-full p-2">
                      <svg class="w-4 h-4 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
                      </svg>
                    </div>
                  </div>
                  <div class="mt-1 text-sm text-indigo-600 font-medium">Ağırlık: %20</div>
                </div>

                <div class="bg-red-50 rounded-xl p-4 sm:p-6 shadow-sm hover:shadow-md transition-shadow duration-200">
                  <div class="flex items-center justify-between">
                    <div>
                      <div class="text-sm text-red-600 font-medium">Kesintiler</div>
                      <div class="mt-1 text-2xl font-semibold text-red-700">
                        {{ (result.devamsizlikPuani + result.sgsPuani + result.uohPuani).toFixed(1) }}
                      </div>
                    </div>
                    <div class="text-red-500 bg-red-100 rounded-full p-2">
                      <svg class="w-4 h-4 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20 12H4M12 20V4" />
                      </svg>
                    </div>
                  </div>
                  <div class="mt-1 text-sm text-red-600 font-medium space-y-0.5">
                    <div v-if="devamsizlik > 0">{{ devamsizlik }} gün: -{{ result.devamsizlikPuani.toFixed(1) }}</div>
                    <div v-if="hasSGS && selectedSGSReason.length > 0">
                      SGS: 
                      -{{ result.sgsPuani.toFixed(1) }}
                    </div>
                    <div v-if="hasUOH && selectedUOHReason.length > 0">
                      UOH: 
                      -{{ result.uohPuani.toFixed(1) }}
                    </div>
                  </div>
                </div>
              </div>

              <!-- Toplam Puan -->
              <div class="bg-gradient-to-r from-blue-500 to-indigo-600 rounded-xl p-4 sm:p-6 text-white shadow-md hover:shadow-lg transition-shadow duration-200">
                <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
                  <div>
                    <h4 class="text-sm font-medium text-blue-100">Toplam Performans Puanı</h4>
                    <div class="mt-1 flex flex-wrap items-center gap-2 sm:gap-3">
                      <span class="text-3xl sm:text-4xl font-bold tracking-tight">{{ result.toplamPuan.toFixed(1) }}</span>
                      <span :class="[result.seviyeRenk, 'text-base sm:text-lg bg-white/10 px-3 py-1 rounded-full font-medium']">
                        {{ result.seviye }}
                      </span>
                    </div>
                  </div>
                  <div class="bg-white/10 rounded-full p-2 sm:p-3 self-end sm:self-auto">
                    <svg class="w-6 h-6 sm:w-8 sm:h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Performans Seviyeleri -->
        <div class="mt-6 rounded-lg sm:rounded-xl bg-white shadow-md p-4 sm:p-6 border border-gray-100 hover:shadow-lg transition-shadow duration-300">
          <div class="flex items-center gap-2 mb-4">
            <svg class="h-5 w-5 text-indigo-600 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
            </svg>
            <h4 class="text-base sm:text-lg font-medium text-gray-900">Performans Seviyeleri</h4>
          </div>

          <!-- Grid Container -->
          <div class="grid grid-cols-2 lg:grid-cols-4 gap-2 sm:gap-3">
            <!-- BS -->
            <div class="rounded-lg bg-red-50 p-3 sm:p-4 flex flex-col justify-between shadow-sm hover:shadow-md transition-shadow duration-200 hover:bg-red-100 cursor-pointer">
              <div class="text-lg font-semibold text-red-600">BS</div>
              <div class="text-sm sm:text-base font-medium text-red-900 mt-1">0 - 95 puan</div>
            </div>
            <!-- BA -->
            <div class="rounded-lg bg-orange-50 p-3 sm:p-4 flex flex-col justify-between shadow-sm hover:shadow-md transition-shadow duration-200 hover:bg-orange-100 cursor-pointer">
              <div class="text-lg font-semibold text-orange-600">BA</div>
              <div class="text-sm sm:text-base font-medium text-orange-900 mt-1">96 - 99 puan</div>
            </div>
            <!-- B1 -->
            <div class="rounded-lg bg-yellow-50 p-3 sm:p-4 flex flex-col justify-between shadow-sm hover:shadow-md transition-shadow duration-200 hover:bg-yellow-100 cursor-pointer">
              <div class="text-lg font-semibold text-yellow-600">B1</div>
              <div class="text-sm sm:text-base font-medium text-yellow-900 mt-1">100 - 106 puan</div>
            </div>
            <!-- B2 -->
            <div class="rounded-lg bg-blue-50 p-3 sm:p-4 flex flex-col justify-between shadow-sm hover:shadow-md transition-shadow duration-200 hover:bg-blue-100 cursor-pointer">
              <div class="text-lg font-semibold text-blue-600">B2</div>
              <div class="text-sm sm:text-base font-medium text-blue-900 mt-1">107 - 112 puan</div>
            </div>
            <!-- B3 -->
            <div class="rounded-lg bg-indigo-50 p-3 sm:p-4 flex flex-col justify-between shadow-sm hover:shadow-md transition-shadow duration-200 hover:bg-indigo-100 cursor-pointer">
              <div class="text-lg font-semibold text-indigo-600">B3</div>
              <div class="text-sm sm:text-base font-medium text-indigo-900 mt-1">113 - 116 puan</div>
            </div>
            <!-- ÜB -->
            <div class="rounded-lg bg-violet-50 p-3 sm:p-4 flex flex-col justify-between shadow-sm hover:shadow-md transition-shadow duration-200 hover:bg-violet-100 cursor-pointer">
              <div class="text-lg font-semibold text-violet-600">ÜB</div>
              <div class="text-sm sm:text-base font-medium text-violet-900 mt-1">117 - 121 puan</div>
            </div>
            <!-- OB -->
            <div class="rounded-lg bg-purple-50 p-3 sm:p-4 flex flex-col justify-between col-span-2 shadow-sm hover:shadow-md transition-shadow duration-200 hover:bg-purple-100 cursor-pointer">
              <div class="text-lg font-semibold text-purple-600">OB</div>
              <div class="text-sm sm:text-base font-medium text-purple-900 mt-1">122+ puan</div>
            </div>
          </div>
        </div>

        <!-- Bilgi Kartları -->
        <div class="mt-6 sm:mt-8 space-y-3 sm:space-y-4 mx-auto">
          <!-- Mevcut Bilgi Kartı -->
          <div class="rounded-xl bg-white shadow-md p-4 sm:p-5 border border-gray-100 hover:shadow-lg transition-shadow duration-300">
            <div class="flex items-start">
              <div class="flex-shrink-0">
                <svg class="h-5 w-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                </svg>
              </div>
              <div class="ml-3 space-y-2">
                <!-- Hedef Değerler -->
                <div class="flex items-center gap-2">
                  <svg class="w-3 h-3 text-indigo-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  <p class="text-sm text-gray-600">
                    <span class="font-bold text-blue-600">MMA</span> hedef değeri <span class="font-medium text-blue-600">4.15 (100 puan)</span> ve 
                    <span class="font-bold text-indigo-600">ACHT</span> hedef değeri <span class="font-bold text-indigo-600">500 saniye</span> olarak belirlenmiştir.
                  </p>
                </div>

                <!-- MMA Açıklaması -->
                <div class="flex items-center gap-2">
                  <svg class="w-3 h-3 text-indigo-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  <p class="text-sm text-gray-600">
                    <span class="font-bold text-blue-600">MMA</span> için <span class="font-medium text-blue-600">4.15</span> değeri <span class="font-bold text-yellow-600">B hedefi (100 puan)</span> olarak kabul edilir. Bu değerin üzerine çıkıldıkça puan <span class="font-bold text-purple-600">130 puana</span> kadar yükselir.
                  </p>
                </div>

                <!-- ACHT Açıklaması -->
                <div class="flex items-center gap-2">
                  <svg class="w-3 h-3 text-indigo-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  <p class="text-sm text-gray-600">
                    <span class="font-bold text-indigo-600">ACHT</span> için <span class="font-bold text-indigo-600">460</span> ve <span class="font-bold text-indigo-600">540</span> saniye değerleri <span class="font-bold text-yellow-600">B hedefi (100 puan)</span> olarak kabul edilir. <span class="font-bold text-indigo-600">500 saniye</span> hedef değerine yaklaştıkça puan <span class="font-bold text-purple-600">130 puana</span> kadar yükselir.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Footer -->
        <footer class="relative py-6 sm:py-8">
          <div class="bg-gradient-to-r from-indigo-50 to-blue-50 rounded-xl p-6 shadow-sm border border-indigo-100">
            <p class="text-sm text-gray-600 flex flex-wrap items-center justify-center gap-3 px-4 sm:px-6">
              <span>Bu proje</span>
              <a href="https://biyik.dev" target="_blank" rel="noopener noreferrer" class="text-indigo-600 hover:text-indigo-700 font-medium transition-colors inline-flex items-center gap-1 hover:underline">
                <span class="inline-flex items-center justify-center bg-indigo-100 text-indigo-700 rounded-full w-6 h-6 text-xs font-bold">M</span>
                Metin Bıyık
              </a> 
              <span>tarafından</span>
              <span class="inline-flex items-center text-emerald-600 font-medium bg-emerald-50 rounded-full px-3 py-1 shadow-sm border border-emerald-100">
                <svg class="w-4 h-4 mr-1" viewBox="0 0 128 128">
                  <path fill="currentColor" d="M0 0h128v128H0z"/>
                  <path fill="#fff" d="M32 32.6l32 55.4 32-55.4h-12.8L64 67.2 44.8 32.6z"/>
                </svg>
                Vue.js
              </span>
              <span>ve</span>
              <span class="inline-flex items-center text-sky-600 font-medium bg-sky-50 rounded-full px-3 py-1 shadow-sm border border-sky-100">
                <img src="../assets/tailwind.svg" alt="TailwindCSS" class="w-5 h-5 mr-1.5" />
                TailwindCSS
              </span>
              <span>kullanılarak oluşturulmuştur.</span>
            </p>
          </div>
        </footer>
      </div>
    </div>

    <!-- Modal Uyarı -->
    <Transition name="modal-backdrop">
      <div v-if="showModal" class="fixed inset-0 bg-black bg-opacity-50 z-40" @click="showModal = false"></div>
    </Transition>
    <Transition name="modal">
      <div v-if="showModal" class="fixed inset-0 flex items-center justify-center z-50">
        <div class="bg-white rounded-xl shadow-xl max-w-md w-full mx-4 transform" @click.stop>
          <div class="p-5 border-b border-gray-200">
            <div class="flex items-center justify-between">
              <h3 class="text-lg font-medium text-gray-900">Uyarı</h3>
              <button @click="showModal = false" class="text-gray-400 hover:text-gray-500 focus:outline-none">
                <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                </svg>
              </button>
            </div>
          </div>
          <div class="p-5">
            <div class="flex items-start">
              <div class="flex-shrink-0">
                <svg class="h-6 w-6 text-amber-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
                </svg>
              </div>
              <div class="ml-3">
                <p class="text-sm text-gray-700">{{ modalMessage }}</p>
              </div>
            </div>
          </div>
          <div class="p-4 bg-gray-50 rounded-b-xl flex justify-end">
            <button
              @click="showModal = false"
              class="px-4 py-2 bg-indigo-600 text-white font-medium rounded-lg hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition-colors"
            >
              Tamam
            </button>
          </div>
        </div>
      </div>
    </Transition>
    
    <!-- Bilgi Modalı -->
    <Transition name="modal-backdrop">
      <div v-if="showInfoModal" class="fixed inset-0 bg-black bg-opacity-50 z-40" @click="showInfoModal = false"></div>
    </Transition>
    <Transition name="info-modal">
      <div v-if="showInfoModal" class="fixed inset-0 flex items-center justify-center z-50">
        <div class="bg-white rounded-xl shadow-xl max-w-lg w-full mx-4 transform" @click.stop>
          <div class="py-4 px-5 border-b border-gray-200 bg-gradient-to-r from-blue-50 to-indigo-50">
            <div class="flex items-center justify-between">
              <h3 class="text-xl font-semibold text-gray-800 flex items-center">
                <svg class="w-6 h-6 mr-2 text-indigo-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                </svg>
                LiveChat Performans Hesaplama
              </h3>
              <button @click="showInfoModal = false" class="text-gray-400 hover:text-gray-500 focus:outline-none">
                <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                </svg>
              </button>
            </div>
          </div>
          <div class="p-5">
            <div class="space-y-5">
              <!-- Hedef Değerler ve Ağırlıklar -->
              <div class="bg-gradient-to-r from-gray-50 to-gray-100 rounded-xl p-4 shadow-sm">
                <h4 class="text-lg font-medium text-gray-800 mb-3 border-b border-gray-200 pb-2">Hedef Değerler ve Ağırlıklar</h4>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                  <!-- MMA Bilgisi -->
                  <div class="bg-white rounded-lg p-3 shadow-sm border border-blue-100">
                    <div class="flex items-center">
                      <div class="w-12 h-12 bg-blue-50 rounded-full flex items-center justify-center mr-3 border border-blue-200">
                        <span class="text-blue-600 font-bold">MMA</span>
                      </div>
                      <div>
                        <div class="text-sm text-gray-700">Hedef: <span class="font-semibold text-blue-600">4.15</span></div>
                        <div class="text-sm text-gray-700">Ağırlık: <span class="font-semibold text-blue-600">%80</span></div>
                      </div>
                    </div>
                  </div>
                  
                  <!-- ACHT Bilgisi -->
                  <div class="bg-white rounded-lg p-3 shadow-sm border border-indigo-100">
                    <div class="flex items-center">
                      <div class="w-12 h-12 bg-indigo-50 rounded-full flex items-center justify-center mr-3 border border-indigo-200">
                        <span class="text-indigo-600 font-bold">ACHT</span>
                      </div>
                      <div>
                        <div class="text-sm text-gray-700">Hedef: <span class="font-semibold text-indigo-600">500 sn</span></div>
                        <div class="text-sm text-gray-700">Ağırlık: <span class="font-semibold text-indigo-600">%20</span></div>
                      </div>
                    </div>
                  </div>
                </div>
                
                <!-- Hesaplama Formülü -->
               
              </div>
              
              <!-- Performans Bilgileri -->
              <div class="space-y-3">
                <h4 class="text-base font-medium text-gray-800">Önemli Bilgiler</h4>
                
                <div class="flex items-start bg-white p-3 rounded-lg shadow-sm border border-gray-100">
                  <div class="flex-shrink-0 mt-0.5">
                    <svg class="w-4 h-4 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                    </svg>
                  </div>
                  <p class="text-sm text-gray-600 ml-2">
                    MMA için <span class="font-medium text-blue-600">4.15</span> değeri <span class="font-medium text-yellow-600">B hedefi (100 puan)</span> olarak kabul edilir.
                  </p>
                </div>
                
                <div class="flex items-start bg-white p-3 rounded-lg shadow-sm border border-gray-100">
                  <div class="flex-shrink-0 mt-0.5">
                    <svg class="w-4 h-4 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                    </svg>
                  </div>
                  <p class="text-sm text-gray-600 ml-2">
                    ACHT için <span class="font-medium text-indigo-600">460-540</span> saniye arası değerler <span class="font-medium text-yellow-600">B hedefi (100 puan)</span> olarak kabul edilir.
                  </p>
                </div>
                
                <div class="flex items-start bg-white p-3 rounded-lg shadow-sm border border-gray-100">
                  <div class="flex-shrink-0 mt-0.5">
                    <svg class="w-4 h-4 text-indigo-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                    </svg>
                  </div>
                  <p class="text-sm text-gray-600 ml-2">
                    Kesintiler: devamsızlık, SGS ve UOH puanları toplam puandan düşülür.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="p-4 bg-gray-50 rounded-b-xl flex justify-end border-t border-gray-100">
            <button
              @click="showInfoModal = false"
              class="px-4 py-2 bg-gradient-to-r from-blue-600 to-indigo-600 text-white font-medium rounded-lg hover:from-blue-700 hover:to-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition-colors shadow-sm"
            >
              Anladım
            </button>
          </div>
        </div>
      </div>
    </Transition>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface PerformanceResult {
  mmaPuan: number
  achtPuan: number
  devamsizlikPuani: number
  sgsPuani: number
  uohPuani: number
  toplamPuan: number
  seviye: string
  seviyeRenk: string
}

const mmaValue = ref('')
const achtValue = ref('')
const devamsizlik = ref(0)
const hasSGS = ref(false)
const hasUOH = ref(false)
const result = ref<PerformanceResult | null>(null)
const showModal = ref(false)
const modalMessage = ref('')
const showInfoModal = ref(true)

// Reason tabloları
const sgsReasons = [
  { id: 1, text: 'Hatalı bilgi', puan: 5 },
  { id: 2, text: 'Hatalı İşlem', puan: 5 },
  { id: 3, text: 'Eksik bilgi', puan: 5 },
  { id: 4, text: 'Eksik işlem', puan: 5 },
  { id: 5, text: 'Bekletme', puan: 5 },
  { id: 6, text: 'Güvenlik Teyidi', puan: 5 },
  { id: 7, text: 'PTD', puan: 10 },
  { id: 8, text: 'Hizmet ve Kalite Politikalarına Uygun olmayan Çağrı Yönetimi', puan: 10 },
  { id: 9, text: 'Rakip Operator ve hat iptal Talabine Karşı Duyarsız Kalma', puan: 10 },
  { id: 10, text: 'Görüşme Sonlandırma', puan: 60 },
  { id: 11, text: 'Tarz', puan: 60 }
]

const uohReasons = [
  { id: 1, text: 'Hatalı bilgi', puan: 1 },
  { id: 2, text: 'Hatalı İşlem', puan: 1 },
  { id: 3, text: 'Eksik bilgi', puan: 1 },
  { id: 4, text: 'Eksik işlem', puan: 1 },
  { id: 5, text: 'Bekletme', puan: 1 },
  { id: 6, text: 'Güvenlik Teyidi', puan: 1 },
  { id: 7, text: 'PTD', puan: 5 },
  { id: 8, text: 'Hizmet ve Kalite Politikalarına Uygun olmayan Çağrı Yönetimi', puan: 5 },
  { id: 9, text: 'Rakip Operator ve hat iptal Talabine Karşı Duyarsız Kalma', puan: 5 },
  { id: 10, text: 'Görüşme Sonlandırma', puan: 60 },
  { id: 11, text: 'Tarz', puan: 60 }
]

const selectedSGSReason = ref<number[]>([])
const selectedUOHReason = ref<number[]>([])

// Dropdown durumları için ref'ler
const isSGSOpen = ref(false)
const isUOHOpen = ref(false)

// Dropdown toggle fonksiyonlarını güncelle
const toggleSGSDropdown = (event: Event) => {
  event.stopPropagation() // Event'in parent elementlere yayılmasını engelle
  isSGSOpen.value = !isSGSOpen.value
  isUOHOpen.value = false
}

const toggleUOHDropdown = (event: Event) => {
  event.stopPropagation() // Event'in parent elementlere yayılmasını engelle
  isUOHOpen.value = !isUOHOpen.value
  isSGSOpen.value = false
}

// Dropdown dışına tıklandığında kapanması için event listener
onMounted(() => {
  document.addEventListener('click', () => {
    isSGSOpen.value = false
    isUOHOpen.value = false
  })
  
  // Sayfa yüklendiğinde bilgi modalını göster
  showInfoModal.value = true
})

// Reason seçme fonksiyonları
const selectSGSReason = (id: number, event: Event) => {
  event.stopPropagation()
  if (selectedSGSReason.value.includes(id)) {
    selectedSGSReason.value = selectedSGSReason.value.filter(reasonId => reasonId !== id)
  } else {
    selectedSGSReason.value.push(id)
  }
  isSGSOpen.value = false
}

const selectUOHReason = (id: number, event: Event) => {
  event.stopPropagation()
  if (selectedUOHReason.value.includes(id)) {
    selectedUOHReason.value = selectedUOHReason.value.filter(reasonId => reasonId !== id)
  } else {
    selectedUOHReason.value.push(id)
  }
  isUOHOpen.value = false
}

const calculateMMAScore = (value: number) => {
  // MMA değer aralıkları ve performans puanları (görseldeki tabloya göre güncellendi)
  const mmaRanges = [
    { min: 0, max: 2.98, score: 56.0 },
    { min: 2.98, max: 3.06, score: 56.0 },
    { min: 3.06, max: 3.15, score: 60.0 },
    { min: 3.15, max: 3.23, score: 64.0 },
    { min: 3.23, max: 3.31, score: 68.0 },
    { min: 3.31, max: 3.40, score: 72.0 },
    { min: 3.40, max: 3.48, score: 72.0 },
    { min: 3.48, max: 3.57, score: 76.0 },
    { min: 3.57, max: 3.65, score: 76.0 },
    { min: 3.65, max: 3.73, score: 76.8 },
    { min: 3.73, max: 3.82, score: 77.6 },
    { min: 3.82, max: 3.90, score: 78.4 },
    { min: 3.90, max: 3.98, score: 78.4 },
    { min: 3.98, max: 4.07, score: 79.2 },
    { min: 4.07, max: 4.15, score: 79.2 },
    { min: 4.15, max: 4.19, score: 80.0 },
    { min: 4.19, max: 4.22, score: 82.4 },
    { min: 4.22, max: 4.26, score: 84.0 },
    { min: 4.26, max: 4.29, score: 85.6 },
    { min: 4.29, max: 4.33, score: 87.2 },
    { min: 4.33, max: 4.36, score: 89.6 },
    { min: 4.36, max: 4.40, score: 90.4 },
    { min: 4.40, max: 4.44, score: 92.0 },
    { min: 4.44, max: 4.47, score: 92.8 },
    { min: 4.47, max: 4.51, score: 94.4 },
    { min: 4.51, max: 4.54, score: 96.0 },
    { min: 4.54, max: 4.58, score: 96.8 },
    { min: 4.58, max: 4.61, score: 99.2 },
    { min: 4.61, max: 4.65, score: 101.6 },
    { min: 4.65, max: Infinity, score: 104.0 }
  ]

  for (const range of mmaRanges) {
    if (value >= range.min && value < range.max) {
      return range.score // Direkt performans puanını döndür
    }
  }
  return 0
}

const calculateACHTScore = (value: number) => {
  // ACHT değer aralıkları ve skala puanları
  const achtRanges = [
    { value: 575, skala: 70, score: 14.0 },
    { value: 570, skala: 74, score: 14.8 },
    { value: 565, skala: 79, score: 15.8 },
    { value: 560, skala: 83, score: 16.6 },
    { value: 555, skala: 87, score: 17.4 },
    { value: 550, skala: 92, score: 18.4 },
    { value: 545, skala: 96, score: 19.2 },
    { value: 540, skala: 100, score: 20.0 },
    { value: 535, skala: 105, score: 21.0 },
    { value: 530, skala: 109, score: 21.8 },
    { value: 525, skala: 113, score: 22.6 },
    { value: 520, skala: 118, score: 23.6 },
    { value: 515, skala: 122, score: 24.4 },
    { value: 510, skala: 126, score: 25.2 },
    { value: 505, skala: 128, score: 25.6 },
    { value: 500, skala: 130, score: 26.0 },
    { value: 495, skala: 128, score: 25.6 },
    { value: 490, skala: 126, score: 25.2 },
    { value: 485, skala: 122, score: 24.4 },
    { value: 480, skala: 118, score: 23.6 },
    { value: 475, skala: 113, score: 22.6 },
    { value: 470, skala: 109, score: 21.8 },
    { value: 465, skala: 105, score: 21.0 },
    { value: 460, skala: 100, score: 20.0 },
    { value: 455, skala: 96, score: 19.2 },
    { value: 450, skala: 92, score: 18.4 },
    { value: 445, skala: 87, score: 17.4 },
    { value: 440, skala: 83, score: 16.6 },
    { value: 435, skala: 79, score: 15.8 },
    { value: 430, skala: 74, score: 14.8 },
    { value: 425, skala: 70, score: 14.0 }
  ]

  // En yakın ACHT değerini bul
  let closestRange = achtRanges[0]
  let minDiff = Math.abs(value - achtRanges[0].value)

  for (const range of achtRanges) {
    const diff = Math.abs(value - range.value)
    if (diff < minDiff) {
      minDiff = diff
      closestRange = range
    }
  }

  return closestRange.score // Performans puanını döndür
}

// Performans seviyesini hesaplama fonksiyonunu güncelle
const calculatePerformanceLevel = (totalScore: number) => {
  if (totalScore >= 122) return { level: 'OB', color: 'text-purple-600' }
  if (totalScore >= 117) return { level: 'ÜB', color: 'text-violet-600' }
  if (totalScore >= 113) return { level: 'B3', color: 'text-indigo-600' }
  if (totalScore >= 107) return { level: 'B2', color: 'text-blue-600' }
  if (totalScore >= 100) return { level: 'B1', color: 'text-yellow-600' }
  if (totalScore >= 96) return { level: 'BA', color: 'text-orange-600' }
  if (totalScore >= 0) return { level: 'BS', color: 'text-red-600' }
  return { level: '-', color: 'text-gray-400' }
}

const calculateDevamsizlikPuani = (gunSayisi: number) => {
  const devamsizlikTablosu = [
    { gun: 0, puan: 0 },
    { gun: 1, puan: -1.5 },
    { gun: 2, puan: -3.6 },
    { gun: 3, puan: -6 },
    { gun: 4, puan: -13 }
  ]

  const devamsizlikBilgisi = devamsizlikTablosu.find(d => d.gun === Math.min(gunSayisi, 4))
  return devamsizlikBilgisi ? devamsizlikBilgisi.puan : -13 // 4 günden fazlası için -13 puan
}

const calculatePerformance = () => {
  const mma = Number(mmaValue.value)
  const acht = Number(achtValue.value)

  if (!mma || !acht) {
    modalMessage.value = 'Lütfen MMA ve ACHT değerlerini giriniz.'
    showModal.value = true
    return
  }

  const mmaPuan = calculateMMAScore(mma)
  const achtPuan = calculateACHTScore(acht)
  const devamsizlikPuani = calculateDevamsizlikPuani(Number(devamsizlik.value))
  
  // SGS ve UOH puanlarını seçilen reason'a göre hesapla
  const sgsPuani = hasSGS.value ? 
    selectedSGSReason.value.reduce((total, reasonId) => {
    const reason = sgsReasons.find(r => r.id === reasonId)
      return total + (reason ? reason.puan : 0)
    }, 0) : 0
  
  const uohPuani = hasUOH.value ? 
    selectedUOHReason.value.reduce((total, reasonId) => {
      const reason = uohReasons.find(r => r.id === reasonId)
      return total + (reason ? reason.puan : 0)
    }, 0) : 0

  const toplamPuan = mmaPuan + achtPuan - Math.abs(devamsizlikPuani) - sgsPuani - uohPuani
  const performanceLevel = calculatePerformanceLevel(toplamPuan)

  result.value = {
    mmaPuan,
    achtPuan,
    devamsizlikPuani: Math.abs(devamsizlikPuani),
    sgsPuani,
    uohPuani,
    toplamPuan,
    seviye: performanceLevel.level,
    seviyeRenk: performanceLevel.color
  }
}
</script>

<style>
.transition-all {
  transition-property: all;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}

.transform {
  transform: translateZ(0);
  transform-origin: center;
  backface-visibility: hidden;
}

/* Arkaplan animasyonu */
@keyframes pulse {
  0%, 100% {
    opacity: 0.9;
  }
  50% {
    opacity: 0.6;
  }
}

.bg-gradient-radial {
  background: radial-gradient(circle 800px at 50% 200px, #C9EBFF, transparent);
  animation: pulse 10s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

/* Input Hover Efektleri */
input:hover {
  border-color: rgba(99, 102, 241, 0.4);
}

input:focus {
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.2);
}

/* Scrollbar'ı gizle */
::-webkit-scrollbar {
  display: none;
}

/* Firefox için scrollbar'ı gizle */
* {
  scrollbar-width: none;
}

/* Select element stilleri */
select {
  appearance: none;
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 20 20'%3e%3cpath stroke='%236b7280' stroke-linecap='round' stroke-linejoin='round' stroke-width='1.5' d='M6 8l4 4 4-4'/%3e%3c/svg%3e");
  background-position: right 0.5rem center;
  background-repeat: no-repeat;
  background-size: 1.5em 1.5em;
}

select option {
  padding: 0.5rem;
  font-size: 0.875rem;
}

/* SGS için özel renkler */
select:focus.ring-orange-500 {
  box-shadow: 0 0 0 2px rgba(249, 115, 22, 0.2);
}

/* UOH için özel renkler */
select:focus.ring-amber-500 {
  box-shadow: 0 0 0 2px rgba(217, 119, 6, 0.2);
}

/* Modal Animasyonları */
.modal-enter-active, .modal-leave-active {
  transition: all 0.3s ease;
}
.modal-enter-from, .modal-leave-to {
  opacity: 0;
  transform: scale(0.9);
}
.modal-backdrop-enter-active, .modal-backdrop-leave-active {
  transition: opacity 0.3s ease;
}
.modal-backdrop-enter-from, .modal-backdrop-leave-to {
  opacity: 0;
}

/* Bilgi Modal Animasyonları */
.info-modal-enter-active {
  animation: modal-in 0.4s ease-out forwards;
}
.info-modal-leave-active {
  animation: modal-out 0.3s ease-in forwards;
}
@keyframes modal-in {
  0% {
    opacity: 0;
    transform: translateY(15px) scale(0.95);
  }
  70% {
    opacity: 1;
    transform: translateY(-5px) scale(1.02);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
@keyframes modal-out {
  0% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
  100% {
    opacity: 0;
    transform: translateY(15px) scale(0.95);
  }
}
</style> 