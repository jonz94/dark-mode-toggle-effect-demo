<script setup lang="ts">
import { reactive } from 'vue'
import CodeBlock from './components/CodeBlock.vue'
import CommandsBlock from './components/CommandsBlock.vue'

const changeCandidateTextFontCommand = `defaults write org.openvanilla.inputmethod.McBopomofo \\
    CandidateTextFontName HiraMinPro-W3`

const changeCandidateKeyLabelFontCommand = `defaults write org.openvanilla.inputmethod.McBopomofo \\
    CandidateKeyLabelFontName Palatino-Roman`

const changeCandidateKeysCommand = `defaults write org.openvanilla.inputmethod.McBopomofo \\
    CandidateKeys "asdfghjkl"`

const resetCommand = `defaults delete org.openvanilla.inputmethod.McBopomofo CandidateTextFontName
defaults delete org.openvanilla.inputmethod.McBopomofo CandidateKeyLabelFontName
defaults delete org.openvanilla.inputmethod.McBopomofo CandidateKeys`

const state = reactive({ enableDarkMode: false })

function toggle() {
  state.enableDarkMode = !state.enableDarkMode
}
</script>

<template>
  <div class="min-w-screen grid min-h-screen place-content-center bg-white">
    <div class="fixed h-screen w-screen overflow-hidden">
      <div class="fixed right-4 top-4 grid h-5 w-5 place-content-center md:right-12 md:top-12">
        <div
          class="relative inset-0 flex h-[max(300vw,300vh)] w-[max(300vw,300vh)] flex-[0_0_auto] rounded-[50%] bg-[#121212] duration-1000 ease-in-out"
          :class="state.enableDarkMode ? 'scale-100' : 'scale-0'"
        ></div>
      </div>
    </div>

    <div
      class="fixed right-4 top-4 z-10 h-5 w-5 cursor-pointer rounded-full duration-1000 ease-in-out md:right-12 md:top-12"
      :class="state.enableDarkMode ? 'bg-white' : 'bg-black'"
      @click="toggle()"
    ></div>

    <main class="flex w-screen max-w-2xl flex-col gap-8 px-4 py-8 text-white mix-blend-difference">
      <section class="flex flex-col gap-2">
        <h1 class="text-2xl font-bold"># 小麥注音的隱藏設定</h1>
        <p>小麥注音從 0.9.4 版開始，多了幾個隱藏設定。這些設定都可以透過指令來調整。</p>
      </section>

      <section>
        <p class="space-x-1">
          <span>🔗</span>
          <span>原文出處：</span>
        </p>
        <p>
          <span>
            <a
              href="https://osxchat.tumblr.com/post/29205181318/mcbopomofo-hidden-settings"
              target="_blank"
              class="break-all underline"
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
          <CodeBlock>HiraMinPro-W3</CodeBlock>
        </p>
        <CommandsBlock :command="changeCandidateTextFontCommand" />
      </section>

      <section class="flex flex-col gap-2">
        <h2 class="text-xl font-bold">## 更改選字窗的選字鍵字型</h2>
        <p>
          以下指令可以將選字鍵字型更改為 Palatino
          <CodeBlock>Palatino-Roman</CodeBlock>
        </p>
        <CommandsBlock :command="changeCandidateKeyLabelFontCommand" />
      </section>

      <section class="flex flex-col gap-2">
        <h2 class="text-xl font-bold">## 更改選字鍵</h2>
        <p>原本的選字鍵預設為 <CodeBlock>123456789</CodeBlock></p>
        <p>
          以下指令可以將可以將選字鍵改為
          <CodeBlock>asdfghjkl</CodeBlock>
        </p>
        <CommandsBlock :command="changeCandidateKeysCommand" />
      </section>

      <section class="flex flex-col gap-2">
        <h2 class="text-xl font-bold">## 還原所有的設定</h2>
        <p>以下指令可以將小麥輸入法的設定還原回預設值</p>
        <CommandsBlock :command="resetCommand" />
      </section>
    </main>
  </div>
</template>
