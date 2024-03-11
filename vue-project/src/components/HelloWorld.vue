<script setup>
import { ref, computed } from "vue";
const store = ref([
  {
    label: "Debut",
    type: "vinyl",
    cost: 80,
    quantity: 300
  },
  {
    label: "Fearless Taylor's Version",
    type: "vinyl",
    cost: 700,
    quantity: 150
  },
  {
    label: "Speak Now Taylor's Version",
    type: "vinyl",
    cost: 120,
    quantity: 80
  },
  {
    label: "Red Taylor's Version",
    type: "vinyl",
    cost: 120,
    quantity: 80
  },
  {
    label: "Folklore",
    type: "vinyl",
    cost: 120,
    quantity: 80
  },
  {
    label: "Midnights",
    type: "vinyl",
    cost: 120,
    quantity: 80
  },
  {
    label: "Evermore",
    type: "vinyl",
    cost: 120,
    quantity: 80
  },
  {
    label: "The Tortured Poets Department",
    type: "vinyl",
    cost: 120,
    quantity: 80
  },
  {
    label: "Reputation",
    type: "vinyl",
    cost: 200,
    quantity: 80
  },
  {
    label: "1989",
    type: "vinyl",
    cost: 120,
    quantity: 80
  },
  {
    label: "Lover",
    type: "vinyl",
    cost: 100,
    quantity: 80
  },
]);
const cart = ref([]);

function transferValue(source, destination) {
  if (source.length > 0) {
    const value = source.pop();
    destination.push(value);
  }
}

const filteredCart = computed(() => {
  return cart.filter((item) => item.cost > 100);
});
const totalCost = computed(() => {
  return cart.reduce((accumulator, current) => accumulator + current.cost, 0);
});
</script>
<template>
  <main>
    <section>
      <div>
        <h3>Store</h3>
        <ul>
          <li v-for="item in store" :key="item.label">
           <span @click="transferValue(store, cart)"> {{ item.label }} -- {{item.type}} -- ${{ item.cost }}</span>
          </li>
        </ul>

        <button @click="transferValue(store, cart)">Add to Cart</button>
      </div>
      <div>
        <h3>Cart</h3>
        <p v-if="cart.length === 0" class="warn">Nothing in cart</p>
        <ul>
          <li v-for="item in cart" :key="item.label">{{ item.label }}</li>
        </ul>

        <button @click="transferValue(cart, store)">Return to Store</button>
      </div>
    </section>
    </main>
</template>