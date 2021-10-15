<template>
    <div>
       <h1>Home</h1> 
       <FirstComponet />
       <LifeCicle />
    </div>
</template>

<script>
import FirstComponet from '../components/FirstComponent.vue'
import LifeCicle from '../components/LifeCicle.vue'

export default {
    name: 'Home',
    components: {
        FirstComponet,
        LifeCicle,
    }
}
</script>