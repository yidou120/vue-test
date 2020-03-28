<template>
    <div>
        <table>
            <tr>
                <td>ID</td>
                <td>Name</td>
                <td>Author</td>
            </tr>
            <tr v-for="item in books">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.author}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: "Book",
        data() {
            return {
                msg: 'test',
                books:[
                    {
                        id:1,
                        name:'张一',
                        author:'张一啊'
                    },
                    {
                        id:2,
                        name:'张二',
                        author:'张二啊'
                    },
                    {
                        id:3,
                        name:'张三',
                        author:'张三啊'
                    }
                ]
            }
        },
        created() {
            var _this = this;
            axios.get("http://localhost:8082/books/findAll").then(function (resp) {
                _this.books = resp.data;
                console.log(resp)
            })
        }
    }
</script>

<style scoped>

</style>