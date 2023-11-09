<!-- @format -->
<script lang="ts">
  import { onMount } from "svelte";

  let time: number = 0;
  let interval: ReturnType<typeof setInterval>; // 使用 TypeScript 的 ReturnType 工具类型

  onMount(() => {
    interval = setInterval(() => {
      time += 1;
    }, 1000);

    // 返回一个清理函数
    return () => {
      if (interval) clearInterval(interval);
    };
  });

  const start = (): void => {
    interval = setInterval(() => {
      time += 1;
    }, 1000);
  };

  // 清除 interval 的函数
  const stop = (): void => {
    if (interval) clearInterval(interval);
  };

  // 重置计时器的函数
  const reset = (): void => {
    time = 0;
  };
</script>
<div class="container">
  <p>Time : <span>{time}</span> seconds</p>

  <button on:click={start}>開始</button>
  <button on:click={stop}>暫停</button>
  <button on:click={reset}>重新</button>
</div>
<style>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 300px;
    height: 400px;
    border: 1px solid rgb(222, 211, 211);
    margin: 15px auto;
  }
  .container button {
    margin: 5px auto;
    width: 30%;
  }
</style>
