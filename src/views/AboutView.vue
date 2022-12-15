<template>
  <div class="about">
    <div>
            <label for="Heading">Heading : </label>
            <input type="text" id="Heading" ref="head" v-model="title" placeholder="Give an Awesome Label">
            <!-- <button style="margin: 15px"  @click="head_fn" >Save Heading</button> -->
        </div>
       <br><br>

      
        <div>
            <label for="Tasks"> Tasks : </label>
            <input type="text" id="Tasks" name="task" v-model="task_input_val" placeholder="Enter Task">
            <button style="margin: 15px" @click="addTask">Add Task</button>
            <div id="task_view">

            </div>
        </div>
        
        <br>

        <ul>
            <li v-for="(value,key) in task_" v-bind:key="key">
                <span>{{ value }}</span> <button @click="remove_(key)">  x</button>
                <br><br>
            </li>
          </ul>
          <br>
        <button id="saveList" v-if="title" @click="save_to_list">Save</button>
        <p>Heading : {{ title }}</p>
        <p>Task : {{task_input_val}}</p>
        <p>Complete Tasks : {{task_}}</p>

        <button @click="show_list">View Tasks</button>
  <div v-if="this.flag">
          <ul v-for="(val,ky) in List_" v-bind:key="ky">
                <span>{{ val }}</span> 
                <br><br>
          </ul>
  </div>

        <!-- <li :v-for="value in object">
          {{ value }}
        </li> -->

        <!-- <div class="block_view" :v-for="item in this.List_">
          console.log(item)
          Title : {{item.title_}}
          Task : {{obj.tasks}}

        </div>  -->
  </div>
</template>

<script>
export default {
  // name: 'App',
  // props: [List_],
  data () {
    return {
      show_save_btn : false,
            title : "",
            task_input_val : "",
            task_ : [],
            List_ : [
                // {title:"",tasks : []} // This is the master List of all newly created lists.
            ],
            flag : false
    }
  },

  mounted(){
    this.$refs.head.focus()
  },
  methods : {
addTask(){
            
            this.task_.push(this.task_input_val)
            console.log(`task_ = ${this.task_}`)
            this.task_input_val = ""
        },

        remove_(k){
            
        this.task_.splice(k, 1);
    
        },

        delTask(){
            console.log("del")
        },

        save_to_list(){
            this.List_.push({
                title_ : this.title,
                tasks : this.task_
            })
            console.log(this.List_[0].tasks)
            this.title = ""
            this.task_ = []
        },

        show_list(){
            console.log("called show_list")
            var len_ = this.List_.length
            this.flag = true
            for (let i = 0; i<len_; i++){
                console.log("inside for loop")
                console.log(`Title : ${this.List_[i].title_}, Tasks : ${this.List_[i].tasks}`)
                
            }
            // return {
            //   true
            // }

        }
    }
}

  

</script>

<style scoped>
    .block_view{
        padding: 100px 0; /* padding top and bottom are 10px, right and left are 0 */ 
        width: 400px;
        text-align: center;
        background: #ddd;
        margin: 20px; /*Margin for all sides of the element*/
        display: inline-block;
    }

    ul {
 text-align: center;
 list-style-position: inside;
}
</style>
