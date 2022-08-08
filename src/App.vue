<template>
    <div id="box">
        <ProgressBar title="傻了吧唧" :total="168" :recent="37"/>
    </div>
</template>

<script>
import ProgressBar from "@/components/ProgressBar";

export default {
    name: 'App',
    components: {ProgressBar},
}
</script>

<style>
*{
    margin: 0;
    padding: 0;
}

html,
body,
#app,
#box {
    width: 100%;
    height: 100%;
}

#box {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
