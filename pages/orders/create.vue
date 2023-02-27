<template>
  <div class="overflow-y-hidden">
    <div class="2xl:container 2xl:mx-auto">
      <div class="lg:px-20 md:px-6 px-4 md:py-12 py-8">
        <div class="flex justify-between items-center">
          <h1 class="text-3xl lg:text-4xl font-semibold text-gray-800 text-left">Cart</h1>
          <p class="text-base font-semibold text-gray-800 text-right">More items</p>
        </div>
        <div class="container mt-6 flex justify-between">
          <div class="container border-2 border-slate-300">
            <div class="p-6 flex justify-between flex-started">
              <div class="prod">
                <h2 class="text-xl text-gray-800 font-semibold">Product</h2>
                <div class="flex justify-center items-center mt-4 md:mt-19">
                  <img class="max-w-xs w-24" src="https://paguemenos.vtexassets.com/arquivos/ids/312545/fef8c6a27a0372c4cc5e909c9356e1ee_ninho-leite-ninho-forti--380g_lett_2.jpg?v=637592759464200000" alt="A chair with designed back" role="img" />
                </div>
              </div>

              <div class="prod2">
                <h2 class="text-xl text-gray-800 font-semibold">Quantity</h2>
                <div class="flex justify-center items-center mt-4 md:mt-19">
                  <p class="text-2xl lg:text-3xl font-semibold text-gray-600 text-left">5</p>
                </div>
              </div>

              <div class="prod3">
                <h2 class="text-xl text-gray-800 font-semibold">Price</h2>
                <div class="flex justify-center items-center mt-4 md:mt-19">
                  <p class="text-2xl lg:text-3xl font-semibold text-gray-600 text-left">$30</p>
                </div>
              </div>
            </div>
          </div>
          <div class="container w-80 border-2 border-slate-300">
            <div class="p-6">
              <h4 class="text-lg mb-4 text-gray-800 font-semibold">Amount: <b> $1000 </b></h4>
              <button class="px-4 py-2 w-full text-sm rounded text-white bg-teal-500 focus:outline-none hover:bg-teal-400">Checkout</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
