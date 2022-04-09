<script setup lang="ts"></script>

<template>
  <div class="min-w-screen grid min-h-screen place-content-center">
    <main class="flex w-screen max-w-2xl flex-col gap-8 px-4 py-8">
      <section class="flex flex-col gap-2">
        <h1 class="text-2xl font-bold"># 小麥注音的隱藏設定</h1>
        <p>小麥注音從 0.9.4 版開始，多了幾個隱藏設定。這些設定都可以透過指令來調整。</p>
      </section>

      <section>
        <p>
          <span>🔗 原文出處：</span>
          <span>
            <a
              href="https://osxchat.tumblr.com/post/29205181318/mcbopomofo-hidden-settings"
              target="_blank"
              class="underline"
              >https://osxchat.tumblr.com/post/29205181318/mcbopomofo-hidden-settings</a
            >
          </span>
        </p>
      </section>

      <section class="flex flex-col gap-2">
        <h2 class="text-xl font-bold">## 更改選字窗的文字字型</h2>
        <p>原本選字窗的文字是用系統預設字型。</p>
        <p>
          以下指令可以將字型更改為日文的 Hiragino 明朝體
          <code class="rounded border bg-slate-200 p-1">HiraMinPro-W3</code>
        </p>
        <div class="overflow-hidden rounded border p-4">
          <pre class="overflow-auto">
defaults write org.openvanilla.inputmethod.McBopomofo \
    CandidateTextFontName HiraMinPro-W3</pre
          >
        </div>
      </section>

      <section class="flex flex-col gap-2">
        <h2 class="text-xl font-bold">## 更改選字窗的選字鍵字型</h2>
        <p>
          以下指令可以將選字鍵字型更改為 Palatino
          <code class="rounded border bg-slate-200 p-1">Palatino-Roman</code>
        </p>
        <div class="overflow-hidden rounded border p-4">
          <pre class="overflow-auto">
defaults write org.openvanilla.inputmethod.McBopomofo \
    CandidateKeyLabelFontName Palatino-Roman</pre
          >
        </div>
      </section>

      <section class="flex flex-col gap-2">
        <h2 class="text-xl font-bold">## 更改選字鍵</h2>
        <p>原本的選字鍵預設為 <code class="rounded border bg-slate-200 p-1">123456789</code></p>
        <p>
          以下指令可以將可以將選字鍵改為
          <code class="rounded border bg-slate-200 p-1">asdfghjkl</code>
        </p>
        <div class="overflow-hidden rounded border p-4">
          <pre class="overflow-auto">
defaults write org.openvanilla.inputmethod.McBopomofo \
    CandidateKeys "asdfghjkl"</pre
          >
        </div>
      </section>

      <section class="flex flex-col gap-2">
        <h2 class="text-xl font-bold">## 還原所有的設定</h2>
        <p>以下指令可以將小麥輸入法的設定還原回預設值</p>
        <div class="overflow-hidden rounded border p-4">
          <pre class="overflow-auto">
defaults delete org.openvanilla.inputmethod.McBopomofo CandidateTextFontName
defaults delete org.openvanilla.inputmethod.McBopomofo CandidateKeyLabelFontName
defaults delete org.openvanilla.inputmethod.McBopomofo CandidateKeys</pre
          >
        </div>
      </section>
    </main>
  </div>
</template>
