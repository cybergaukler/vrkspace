<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

const count = ref(0)
</script>

<template>
         <div class="content">
            <div class="configHead">
                <span>Before you take a seat...</span>
                <div class="selectConfig">
                    <select id="selectedConfig" title="select your configuration">
                        <option value="Default" selected="selected">Please configure</option>
                        <option value="HTCViveBasic">Vive Basic</option>
                    </select>
                </div>
            </div>
            <div class="configBody">

                <div class="configSteps None">
                    Hello VRKSPace
                </div>

                <div class="configSteps HTCViveBasic">
                    Please place the VIVE Controllers on either side of your physical desk, close to the front edge as shown above.<br />
                    <ul>
                        <li>The controllers must be active.</li>
                        <li>Left Controller should be on the left side of the desk, right controller on the right side.</li>
                    </ul>
                    Then click enterVR with your mouse and put on the headset.<br />
                    In VR, to align the desk to your physical desk, push both GRIP and MENU on both controllers simultaneously.
                </div>

            </div>

        </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
