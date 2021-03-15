<template>
  <Page>
    <ActionBar title="Welcome to NativeScript-Vue!"/>
    <GridLayout columns="*" rows="*, 50">
      <NewComponent row="0" col="0" src="https://picsum.photos/200" stretch="aspectFit"/>
      <GridLayout row="1" columns="*, *">
        <Button col="0" text="Go Back" @tap="navigateBack()"/>
        <Button col="1" text="Next Page" @tap="nextPage()"/>
      </GridLayout>
    </GridLayout>
  </Page>
</template>

<script >
  // Components
  import ListItem from './ListItem'
  import Main from './Home'
  import NewComponent from './NewComponent'
  import {GC} from 'utils/utils'

  export default {
    components: {
      ListItem,
      NewComponent
    },
    data() {
      return {
        msg: 'Hello World!',
        items: new Array(1045),
        indexkk: 0
      }
    },
    
    methods: {
      nextPage() {
        
        this.$navigateTo(Main, {
          //clearHistory: true
        })
      },
      navigateBack() {
        console.log(this.$refs.myphoto)
        this.$refs.myphoto.nativeView.destroy()
        
        this.$navigateBack()
        GC()
      }
    },
    beforeDestroy() {
        console.log('beforeDestroy called')
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>
