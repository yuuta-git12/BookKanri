```html
<style>
  /* 独自定義 @applyが必要 */
  .btn-primasy{
    @apply bg-blue-800 py-2 px-3 rounded-lg text-white hover:bg-blue-700 transition
  }
</style>



<div class="m-8 bg-gray-50 p-8 shadow-2xl">
  <h1 class="text-center font-bold text-red-700 sm:text-2xl md:text-4xl dark:text-6xl">しまぶーのIT大学</h1>
  <ul class="mt-4 list-inside list-disc space-y-2">
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
  </ul>
  <button class="border border-blue-800 py-2 px-3 rounded-lg text-red-500 hover:bg-yellow-700 transition">
    ボタン1
  </button>
  <button class="btn-primasy">
    ボタン2
  </button>
</div>

```

---
# Youtube動画
https://www.youtube.com/watch?v=5TymbaeyV-0

# 動きをつけたい場合
- TailwindCSSは動きのあるUIを単体で作るのは難しい(JavaScriptに依存していないから)
- 動きをつけたい場合は「headless UI」を使用する←TailwindCSSの開発元である Tailwind Labs が作っている
