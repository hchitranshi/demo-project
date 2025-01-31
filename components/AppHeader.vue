<template>
 <div class="routing-div">
  <!-- <UButton color="black" variant="solid">Category</UButton>

  <UButton color="black" variant="solid">Project</UButton> -->


    </div>
   
</template>

<script>
export default {
  name: "AppHeader",
};


</script>

<style scoped>
/* Routing Buttons Div */
.routing-div {
display: flex;
justify-content: flex-start;
background-color: #ffffff;
padding: 10px 20px;
border-bottom: 4px solid #ffffff;
}

.routing-button {
margin-right: 5px;
padding: 8px 15px;
background-color: #ffffff;
color: rgb(11, 10, 10);
border: none;
border-radius: 5px;
cursor: pointer;
}
</style>