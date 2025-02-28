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
        <div class="text-center mb-6 sm:mb-8">
          <h1 class="text-2xl sm:text-4xl font-bold tracking-tight bg-gradient-to-r from-blue-600 via-indigo-600 to-purple-600 bg-clip-text text-transparent">
            LiveChat Performans Hesaplama
          </h1>
          <p class="mt-2 sm:mt-3 text-sm sm:text-base text-gray-600 font-light px-4">
            MMA ve ACHT değerlerinizi girerek performans puanınızı hesaplayın
          </p>
        </div>

        <!-- Ana Kart -->
        <div class="bg-white rounded-xl sm:rounded-2xl shadow-lg overflow-visible mx-auto">
          <!-- Input Alanları -->
          <div class="p-4 sm:p-6 lg:p-8">
            
            <div class="grid gap-4 sm:gap-6 sm:grid-cols-2">
              <!-- MMA Input -->
              <div class="w-full">
                <label class="block text-sm font-medium text-gray-700 mb-1">
                  MMA Değeri
                  <span class="ml-1 inline-flex items-center px-2 py-0.5 rounded text-xs font-medium bg-blue-50 text-blue-800">
                    Hedef: 4.10
                  </span>
                </label>
                <div class="relative mt-1">
                  <input 
                    type="number" 
                    v-model="mmaValue" 
                    step="0.01"
                    placeholder="Örn: 4.10"
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
              <div class="bg-purple-100 border-l-4 border-purple-200 text-purple-800 p-4 mb-4 rounded-xl shadow-md" role="alert">
                <p class="font-bold text-lg">SGS ve UOH'a Karşı ExtraJet Var!</p>
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
                <div v-if="hasSGS && selectedSGSReason.length > 0" class="mt-2 text-sm text-gray-600 font-bold">
                  Seçilen SGS reason sayısı: {{ selectedSGSReason.length }}
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
                <div v-if="hasUOH && selectedUOHReason.length > 0" class="mt-2 text-sm text-gray-600 font-bold">
                  Seçilen UOH reason sayısı: {{ selectedUOHReason.length }}
                </div>
              </div>
            </div>

            <!-- Hesapla Butonu -->
            <button 
              @click="calculatePerformance"
              class="mt-4 sm:mt-6 w-full inline-flex justify-center items-center px-4 sm:px-6 py-3 border border-transparent text-base font-medium rounded-lg text-white bg-gradient-to-r from-blue-600 to-indigo-600 hover:from-blue-700 hover:to-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 transition-all duration-150 transform hover:scale-[1.02] active:scale-[0.98] shadow-sm"
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
              <div class="bg-gradient-to-br from-gray-50 to-gray-100 rounded-lg sm:rounded-xl p-4 sm:p-6">
                <div class="flex items-center justify-between mb-3 sm:mb-4">
                  <h4 class="text-sm font-medium text-gray-900">Girilen Değerler</h4>
                  <div class="text-gray-400 bg-white rounded-full p-2 shadow-sm">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h.01M12 12h.01M19 12h.01M6 12a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0z" />
                    </svg>
                  </div>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 sm:gap-4">
                  <div class="bg-white rounded-lg p-4 shadow-sm">
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
                  <div class="bg-white rounded-lg p-4 shadow-sm">
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
                  <div class="bg-white rounded-lg p-4 shadow-sm">
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
                <div class="bg-blue-50 rounded-xl p-4 sm:p-6">
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

                <div class="bg-indigo-50 rounded-xl p-4 sm:p-6">
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

                <div class="bg-red-50 rounded-xl p-4 sm:p-6">
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
              <div class="bg-gradient-to-r from-blue-500 to-indigo-600 rounded-lg sm:rounded-xl p-4 sm:p-6 text-white">
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
        <div class="mt-6 rounded-lg sm:rounded-xl bg-white shadow-lg p-4 sm:p-6 border border-gray-100">
          <div class="flex items-center gap-2 mb-4">
            <svg class="h-5 w-5 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
            </svg>
            <h4 class="text-base sm:text-lg font-medium text-gray-900">Performans Seviyeleri</h4>
          </div>

          <!-- Grid Container -->
          <div class="grid grid-cols-2 lg:grid-cols-4 gap-2 sm:gap-3">
            <!-- BS -->
            <div class="rounded-lg bg-red-50 p-3 sm:p-4 flex flex-col justify-between">
              <div class="text-lg font-semibold text-red-600">BS</div>
              <div class="text-sm sm:text-base font-medium text-red-900 mt-1">0 - 95 puan</div>
            </div>
            <!-- BA -->
            <div class="rounded-lg bg-orange-50 p-3 sm:p-4 flex flex-col justify-between">
              <div class="text-lg font-semibold text-orange-600">BA</div>
              <div class="text-sm sm:text-base font-medium text-orange-900 mt-1">96 - 99 puan</div>
            </div>
            <!-- B1 -->
            <div class="rounded-lg bg-yellow-50 p-3 sm:p-4 flex flex-col justify-between">
              <div class="text-lg font-semibold text-yellow-600">B1</div>
              <div class="text-sm sm:text-base font-medium text-yellow-900 mt-1">100 - 106 puan</div>
            </div>
            <!-- B2 -->
            <div class="rounded-lg bg-blue-50 p-3 sm:p-4 flex flex-col justify-between">
              <div class="text-lg font-semibold text-blue-600">B2</div>
              <div class="text-sm sm:text-base font-medium text-blue-900 mt-1">107 - 112 puan</div>
            </div>
            <!-- B3 -->
            <div class="rounded-lg bg-indigo-50 p-3 sm:p-4 flex flex-col justify-between">
              <div class="text-lg font-semibold text-indigo-600">B3</div>
              <div class="text-sm sm:text-base font-medium text-indigo-900 mt-1">113 - 116 puan</div>
            </div>
            <!-- ÜB -->
            <div class="rounded-lg bg-violet-50 p-3 sm:p-4 flex flex-col justify-between">
              <div class="text-lg font-semibold text-violet-600">ÜB</div>
              <div class="text-sm sm:text-base font-medium text-violet-900 mt-1">117 - 121 puan</div>
            </div>
            <!-- OB -->
            <div class="rounded-lg bg-purple-50 p-3 sm:p-4 flex flex-col justify-between col-span-2">
              <div class="text-lg font-semibold text-purple-600">OB</div>
              <div class="text-sm sm:text-base font-medium text-purple-900 mt-1">122+ puan</div>
            </div>
          </div>
        </div>

        <!-- Bilgi Kartları -->
        <div class="mt-4 sm:mt-6 space-y-3 sm:space-y-4 mx-auto">
          <!-- Mevcut Bilgi Kartı -->
          <div class="rounded-xl bg-white shadow-sm p-4 border border-gray-100">
            <div class="flex items-start">
              <div class="flex-shrink-0">
                <svg class="h-5 w-5 text-blue-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                </svg>
              </div>
              <div class="ml-3 space-y-2">
                <!-- Hedef Değerler -->
                <div class="flex items-center gap-2">
                  <svg class="w-3 h-3 text-gray-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  <p class="text-sm text-gray-600">
                    <span class="font-bold text-blue-600">MMA</span> hedef değeri <span class="font-medium text-blue-600">4.10 (100 puan)</span> ve 
                    <span class="font-bold text-indigo-600">ACHT</span> hedef değeri <span class="font-bold text-indigo-600">500 saniye</span> olarak belirlenmiştir.
                  </p>
                </div>

                <!-- MMA Açıklaması -->
                <div class="flex items-center gap-2">
                  <svg class="w-3 h-3 text-gray-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  <p class="text-sm text-gray-600">
                    <span class="font-bold text-blue-600">MMA</span> için <span class="font-medium text-blue-600">4.10</span> değeri <span class="font-bold text-yellow-600">B hedefi (100 puan)</span> olarak kabul edilir. Bu değerin üzerine çıkıldıkça puan <span class="font-bold text-purple-600">130 puana</span> kadar yükselir.
                  </p>
                </div>

                <!-- ACHT Açıklaması -->
                <div class="flex items-center gap-2">
                  <svg class="w-3 h-3 text-gray-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
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
        <footer class="relative mt-6 sm:mt-8 py-4 sm:py-6 text-center">
          <p class="text-sm text-gray-600 flex flex-wrap items-center justify-center gap-2 px-4 sm:px-6">
            <span>Bu proje</span>
            <a href="https://biyik.dev" target="_blank" rel="noopener noreferrer" class="text-rose-600 hover:text-rose-700 font-medium transition-colors inline-flex items-center gap-1">
              <span class="inline-flex items-center justify-center bg-rose-100 text-rose-700 rounded w-5 h-5 text-xs font-bold">M</span>
              Metin Bıyık
            </a> 
            <span>tarafından</span>
            <span class="inline-flex items-center text-emerald-600 font-medium bg-white/50 rounded-full px-2 py-1">
              <svg class="w-4 h-4 mr-1" viewBox="0 0 128 128">
                <path fill="currentColor" d="M0 0h128v128H0z"/>
                <path fill="#fff" d="M32 32.6l32 55.4 32-55.4h-12.8L64 67.2 44.8 32.6z"/>
              </svg>
              Vue.js
            </span>
            <span>ve</span>
            <span class="inline-flex items-center text-sky-600 font-medium bg-white/50 rounded-full px-2 py-1">
              <svg class="w-4 h-4 mr-1" viewBox="0 0 54 33">
                <path fill="currentColor" d="M27 0c-7.2 0-11.7 3.6-13.5 10.8 2.7-3.6 5.85-4.95 9.45-4.05 2.054.513 3.522 2.004 5.147C30.744 13.09 33.808 16.2 40.5 16.2c7.2 0 11.7-3.6 13.5-10.8-2.7 3.6-5.85 4.95-9.45 4.05-2.054-.513-3.522-2.004-5.147-3.653C36.756 3.11 33.692 0 27 0zM13.5 16.2C6.3 16.2 1.8 19.8 0 27c2.7-3.6 5.85-4.95 9.45-4.05 2.054.514 3.522 2.004 5.147 3.653C17.244 29.29 20.308 32.4 27 32.4c7.2 0 11.7-3.6 13.5-10.8-2.7 3.6-5.85 4.95-9.45 4.05-2.054-.513-3.522-2.004-5.147-3.653C23.256 19.31 20.192 16.2 13.5 16.2z"/>
              </svg>
              TailwindCSS
            </span>
            <span>kullanılarak oluşturulmuştur.</span>
          </p>
        </footer>
      </div>
    </div>
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
  // MMA değer aralıkları ve performans puanları
  const mmaRanges = [
    { min: 0, max: 2.93, score: 56.0 },
    { min: 2.93, max: 3.01, score: 56.0 },
    { min: 3.01, max: 3.10, score: 60.0 },
    { min: 3.10, max: 3.18, score: 64.0 },
    { min: 3.18, max: 3.26, score: 68.0 },
    { min: 3.26, max: 3.35, score: 72.0 },
    { min: 3.35, max: 3.43, score: 72.0 },
    { min: 3.43, max: 3.52, score: 76.0 },
    { min: 3.52, max: 3.60, score: 76.0 },
    { min: 3.60, max: 3.68, score: 76.8 },
    { min: 3.68, max: 3.77, score: 77.6 },
    { min: 3.77, max: 3.85, score: 78.4 },
    { min: 3.85, max: 3.93, score: 78.4 },
    { min: 3.93, max: 4.02, score: 79.2 },
    { min: 4.02, max: 4.10, score: 79.2 },
    { min: 4.10, max: 4.14, score: 80.0 },
    { min: 4.14, max: 4.17, score: 82.4 },
    { min: 4.17, max: 4.21, score: 84.0 },
    { min: 4.21, max: 4.24, score: 85.6 },
    { min: 4.24, max: 4.28, score: 87.2 },
    { min: 4.28, max: 4.31, score: 89.6 },
    { min: 4.31, max: 4.35, score: 90.4 },
    { min: 4.35, max: 4.39, score: 92.0 },
    { min: 4.39, max: 4.42, score: 92.8 },
    { min: 4.42, max: 4.46, score: 94.4 },
    { min: 4.46, max: 4.49, score: 96.0 },
    { min: 4.49, max: 4.53, score: 96.8 },
    { min: 4.53, max: 4.56, score: 99.2 },
    { min: 4.56, max: 4.60, score: 101.6 },
    { min: 4.60, max: Infinity, score: 104.0 }
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
    alert('Lütfen MMA ve ACHT değerlerini giriniz.')
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
    opacity: 1;
  }
  50% {
    opacity: .7;
  }
}

.bg-gradient-radial {
  background: radial-gradient(circle 800px at 50% 200px, #C9EBFF, transparent);
  animation: pulse 8s cubic-bezier(0.4, 0, 0.6, 1) infinite;
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
</style> 