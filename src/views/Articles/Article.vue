<template>
    <div class="Rect">
    <div class="rect1">
        <h1>ARTICLES</h1>
        <div class="inrect">
            <div v-if="Articles.length">
                <div v-for="Article in Articles" :key="Article.id" class="Article">
                    <nav>
                    <router-link :to="{ name: 'ArticleDetails', params: {id: Article.id}}">
                     <h2>{{ Article.title }}</h2>
                    </router-link>
                    </nav>
                    <p>SUMMARY</p>
                    <p> Lorem, ipsum dolor sit amet consectetur adipisicing elit. Omnis eaque quos inventore at vel corrupti maxime deleniti nobis quisquam qui odit eum, impedit alias consectetur fugiat quam ducimus dignissimos ipsum! </p>
                </div>
            </div>
        </div>
    </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            Articles: []
        }
    },
    mounted() {
        fetch('http://localhost:3000/Articles')
        .then(res => res.json())
        .then(data => this.Articles = data)
        .catch(err => console.log(err.message))
    }
}
</script>

<style scoped>

.Rect {
    height: 700px;
    width: 1450px;
    background: #ffffff;
    padding: 25px;
    position: relative;
    top: -10px;
    left: -10px;

}

.rect1 {
    height: auto;
    width: 1450px;
    background: #ffffff;
    padding: 25px;
    position: relative;
    top: -10px;
    left: -10px;

}

.rect1 h1 {
    text-align: left;
    color: #373737;
}

.inrect {
    height: auto;
    width: 1370px;
    border-radius: 25px;
    background: #707070;
    padding: 25px;
    position: relative;
    top: -10px;
    left: 10px;
}

nav {
    position: relative;
    left: -300px;

}

.Article h2{
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;
}


.Article h2:hover {
    background: #ddd;
}
.Article a{
    text-decoration: none;
}

.Article p {
    text-align: left;
    color: #000;
}

</style>