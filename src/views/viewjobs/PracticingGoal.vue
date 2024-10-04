<template>
<br>
  <div class="containerPracticingGoal">
        <div class="box">
            <h2>What are your practicing targets?</h2>
            <form>
                <label class="checkbox-label">
                    <input type="checkbox" name="target" value="lose_weight">
                    <span>Lose Weight</span>
                </label>
                <label class="checkbox-label">
                    <input type="checkbox" name="target" value="release_stress">
                    <span>Release Stress</span>
                </label>
                <label class="checkbox-label">
                    <input type="checkbox" name="target" value="healthy_diet">
                    <span>Gain healthy diets</span>
                </label>
                <label class="checkbox-label">
                    <input type="checkbox" name="target" value="tracking_health">
                    <span>Tracking Health</span>
                </label>
                <button type="submit">Confirm</button>
            </form>
        </div>
    </div>
</template>
<script>
export default {
  name: 'PracticingGoal'
}
</script>
<style>
</style>
