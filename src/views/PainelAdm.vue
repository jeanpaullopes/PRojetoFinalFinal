<template>
<section class="home-title">
        
   <div class="container" style="margin-top: 40px;">

            <router-link :to = "{name:'AddCourse', params:{}}" class="btn btn-default" style="margin-bottom: 60px;">+ adicionar novo curso</router-link>

            <div class="row">
                <div class="col-12 col-md-8 d-flex">

                    <table class="table table-sm table-responsive">

                        <thead class="table-thead">
                            <tr>
                                <th colspan="2">Curso</th>
                                <th scope="col">Ações</th>
                            </tr>
                        </thead>

                        <tbody class="table-tbody">

                            <CourseFormList :courses="coursesList"/>
                          
                        </tbody>

                    </table>
                </div>
            </div>
        </div>
        
    </section>

</template>

<script>

import CourseFormList from '../components/CourseFormList.vue';
import STORE from "../store/index"

export default {
    name: "courseformlist",
    components:{
        CourseFormList,
    },
    data(){
        return {
        coursesList: Object
        }
    },
    async created(){
       
        await STORE.dispatch('fetchAllCourses')
        console.log("no created do painel")
        this.coursesList = STORE.getters.getCourses
        
    }
//     methods: {

//     DeleteCourse(courseId) {
//       axios.delete("" + course.id)
//       .then(response => {
//         this.result.splice(id, 1)
//         console.log(this.result);
//       });
//     }
// }
}
</script>

<style>

@import '../../public/BodyCss.css';

</style>