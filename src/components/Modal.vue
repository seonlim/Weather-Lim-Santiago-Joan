<template>
                <div id="myModal" class="modal">
                <div class="modal-content">
                                    <aside>
                                        <span @click="passModal" class="close">&times;</span>
                                    </aside>  
                            {{dayData.astro.sunrise}}

                                
                </div>
            </div>
</template>

<script>
export default {
    props:{
        dayData:Object
    },
    methods:{
        passModal() {
            this.$emit('closeModal',false);
        }
    }
    // data() {

        
    // },
}
</script>
<style scoped>
.modal {
  display: block;
  /* Hidden by default */
  position: fixed;
  /* Stay in place */
  z-index: 1;
  /* Sit on top */
  left: 0;
  top: 0;
  width: 100%;
  /* Full width */
  height: 100%;
  /* Full height */
  overflow: auto;
  /* Enable scroll if needed */
  background-color: rgb(0, 0, 0);
  /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4);
  /* Black w/ opacity */
}

/* Modal Content/Box */
.modal-content {
  background-color: #0b99e5;
  margin: 2% auto;
  /* 15% from the top and centered */
  padding: 25px;
  border: 1px solid #888;
  border-radius: 10px;
  width: 65%;
  /* Could be more or less, depending on screen size */
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 2vh;


}

.modal-content > aside {
    width: 100%;
}

/* The Close Button */
.close {
  color: whitesmoke;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>