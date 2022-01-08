<template>
    <div class="literature">
        <div class="literature__form">
            <el-input v-model.trim="keyWord" placeholder="请输入关键词"></el-input>
            <el-button type="primary" @click="generate">生成文献</el-button>
        </div>
        <p v-for="(item,index) in result" :key="item.author">{{`[${index+1}]`}} {{item.author}}. {{item.title}}. {{item.date}}.</p>
    </div>
</template>

<script>
import Mock from "mockjs";
export default {
    data() {
        return {
            keyWord: "",
            result: [],
            num: 5,
        };
    },
    methods: {
        generate() {
            this.result = [];
            let title = [
                `${this.keyWord}管理[M].北京：企业管理出版社`,
                `创造学习${this.keyWord}的新思路［N］.人民日报`,
                `关于中国学术期刊标准化${this.keyWord}进展［EB/OL］`,
                `${this.keyWord}与${this.keyWord}服务国际研讨会论文集：A集［C］.北京：中国社会科学出版社`,
                `中国${this.keyWord}关系型企业分销渠道的变革与创新[J].${this.keyWord}经济与管理,`,
                `西方${this.keyWord}文论选[C]. 上海：上海译文出版社`,
                `高等学校毕业论文关于${this.keyWord}教学情况调研报告[J].高等教育，`,
                `${this.keyWord}识别方式的理论和实证研究[D].北京：北京师范大学`,
                `中华人民共和国${this.keyWord}委员会.科学技术期刊管理办法[Z]`,
                `现代西方${this.keyWord}理论[M].厦门：厦门大学出版社`,
                `${this.keyWord}全球化的重要性[N]. 光明日报`,
            ];
            const titleIndex = Mock.Random.range(0, title.length - 1);
            for (let i = 1; i < titleIndex.length; i++) {
                const random = Math.floor(Math.random() * (i + 1));
                [titleIndex[i], titleIndex[random]] = [
                    titleIndex[random],
                    titleIndex[i],
                ];
            }
            console.log(titleIndex);
            for (let i = 0; i < this.num; i++) {
                this.result.push({
                    author: Mock.mock("@cname"),
                    title: title[titleIndex[i]],
                    date: Mock.mock('@date("yyyy-MM-dd")'),
                });
            }
        },
    },
};
</script>

<style lang="less">
.literature {
    display: flex;
    width: 700px;
    margin-top: 250px;
    margin-left: 200px;
    flex-direction: column;
    align-items:flex-start;
    justify-items: center;
    &__form {
        width: 300px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
}
</style>