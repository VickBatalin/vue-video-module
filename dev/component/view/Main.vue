<template lang="html">
    <div class="main-container">
        <top></top>
        <div class="banner">
            <h4 class="title">Simple video component bulit for vue</h4>
            <ul class="actions">
                <li class="action" v-for="action,index in actions" :key="action">
                    <a :href="action.href" target="_blank">
                        <md-button :class="action.class">{{ action.name }}</md-button>
                    </a>
                </li>
            </ul>
        </div>
        <div class="examples">
            <md-card-header>
                <div class="md-title">
                    <span>Simple demos to preview Or Click</span>
                    <md-button href="#/test" class="md-accent">
                        Test Page
                    </md-button>
                    <span>for further explore</span>
                </div>
            </md-card-header>
            <md-card v-for="example,index in examples" :key="example">
                <md-card-header>
                    <div class="md-subhead">{{ example.title }}</div>
                    <a :href="`https://github.com/iapYang/vue-video-module/blob/master/dev/component/example/${examples[index].title}.vue`" target="_blank">
                        <md-icon>code</md-icon>    
                    </a>
                </md-card-header>
                <div class="md-card-main">
                    <div :is="example.name"></div>
                </div>
            </md-card>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue';
    import VueMaterial from 'vue-material';
    import 'vue-material/dist/vue-material.css';
    
    import example01 from '../example/01-default.vue';
    import example02 from '../example/02-autoPlay.vue';
    import example03 from '../example/03-fullscreen.vue';
    import example04 from '../example/04-aspect.vue';
    import example05 from '../example/05-bufferingBar.vue';
    import Top from '../common/Top.vue';
    
    Vue.use(VueMaterial);
    
    export default {
        data() {
            return {
                actions: [{
                    name: 'view on github',
                    href: 'https://github.com/iapYang/vue-video-module',
                    class: 'md-primary',
                }, {
                    name: 'github issues',
                    href: 'https://github.com/iapYang/vue-video-module/issues',
                    class: 'md-accent',
                }, {
                    name: 'example',
                    href: 'https://github.com/iapYang/vue-video-module/tree/master/dev/component/example',
                    class: 'md-primary',
                }, {
                    name: 'API',
                    href: 'https://github.com/iapYang/vue-video-module/blob/master/README.md',
                    class: 'md-primary',
                }],
                examples: [{
                    title: '01-default',
                    name: 'example01',
                }, {
                    title: '02-autoPlay',
                    name: 'example02',
                }, {
                    title: '03-fullscreen',
                    name: 'example03',
                }, {
                    title: '04-aspect',
                    name: 'example04',
                }, {
                    title: '05-bufferingBar',
                    name: 'example05',
                }],
            };
        },
        components: {
            example01,
            example02,
            example03,
            example04,
            example05,
            Top,
        },
    };
</script>

<style lang="scss">
    .banner {
        h2 {
            // font-family: "Lato-Regular";
            text-transform: uppercase;
            font-size: 35px;
            text-align: center;
            color: #000;
            line-height: 1;
        }
        h4 {
            // font-family: "Lato-Regular";
            text-transform: capitalize;
            font-size: 25px;
            text-align: center;
            color: #a5a5a5;
            line-height: 1;
            margin-bottom: 0;
        }
        .actions {
            position: relative;
            text-align: center;
            li {
                display: inline-block;
            }
        }
    }
    
    .examples {
        position: relative;
        width: 100%;
        max-width: 1024px;
        margin: 0 auto;
        .md-card-header .md-title {
            display: flex;
            align-items: center;
            a {
                font-size: 20px;
                font-weight: bold;
                margin: 0;
            }
        }
        .md-card {
            margin-top: 20px;
            &:nth-child(1) {
                margin-top: 0;
            }
            .md-card-header {
                display: flex;
                justify-content: space-between;
                a {
                    display: inline-block;
                    margin: 0;

                    .md-icon {
                        display: inline-block;
                        margin: 0;
                        color: rgba(0, 0, 0, 0.7);
                    }
                }
                .md-subhead {
                    text-transform: capitalize;
                }
            }
            .md-card-main {
                position: relative;
                display: flex;
                flex-direction: row;
                justify-content: space-between;
                flex-wrap: nowrap;
                align-items: flex-start;
            }
        }
    }
</style>
