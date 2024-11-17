<template>
    <navbar/>
    <!--    <router-view />-->

    <transaction-list/>

</template>
<script>

import {defineComponent} from "vue";
import Navbar from "./components/Navbar.vue";
import TransactionList from "./components/TransactionList.vue";

export default defineComponent({
    components: {Navbar, TransactionList},
})
</script>
