<template>
  <b-row class="header">
        <b-col cols="12">
            <h1 class="title m-0">TâchesMaker</h1>
        </b-col>
  </b-row>
</template>

<script>
export default {
    name: "Header"

}
</script>

<style scoped>
    .header {
        background-color: #d3f3cf;
        width: fit-content;
        padding: 15px 35px 15px 35px;
        margin: 15px 0px 75px 0px;
        border-radius: 15px;
        display: flex;
        justify-content: start;
        align-items: center;
        box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    }

    .title {
        font-size: 2.5rem;
        font-weight: bold;
        font-family: 'Rancho', cursive;
        color: rgb(39, 39, 39);
    }
    @media screen and (max-width: 768px) {
        .header {
            padding: 7px 20px 7px 20px;
            margin: 15px 0px 25px 0px;
        }
    }   
</style>