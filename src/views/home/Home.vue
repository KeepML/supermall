<<template>
    <div>
        <NavBar class="home-nav"><div slot="center">购物街</div> </NavBar>
        <HomeSwiper :banners="banners"/>
        <RecommendView :recommends="recommends"/>
    </div>
</template>

<script>
import NavBar from '@/components/common/navbar/NavBar';
import HomeSwiper from './childcomps/HomeSwiper';
import RecommendView from './childcomps/RecommendView';
import { getHomeMultiData } from '@/network/home';

    export default ({
        name:"Home",
        components: {
            NavBar,
            HomeSwiper,
            RecommendView
        },

        data() {
            return {
                banners: [],
                recommends: []
            }
        },

        //组件加载完成后执行
        created() {
            //发送请求
            getHomeMultiData().then(res => {
                this.banners = res.data.banner.list;
                this.recommends = res.data.recommend.list
            })
        }
    })
</script>



<style scoped>
    .home-nav {
        background-color: var(--color-tint);
        color: #fff;
    }
</style>