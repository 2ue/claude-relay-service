<template>
  <div class="card tutorial-container p-3 sm:p-6">
    <div class="mb-4 sm:mb-8">
      <h3
        class="mb-3 flex items-center text-xl font-bold text-gray-900 dark:text-gray-100 sm:mb-4 sm:text-2xl"
      >
        <i class="fas fa-graduation-cap mr-2 text-blue-600 sm:mr-3" />
        使用教程
      </h3>
      <p class="text-sm text-gray-600 dark:text-gray-400 sm:text-lg">
        按以下步骤依次完成配置与使用，即可开始体验。
      </p>
    </div>

    <div class="tutorial-content space-y-6">
      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <div>
          <h4 class="text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
            GMN API
          </h4>
          <p class="text-sm text-slate-600 dark:text-slate-300 sm:text-base">使用教程</p>
          <p class="text-sm text-slate-600 dark:text-slate-300 sm:text-base">统计查询使用教程</p>
        </div>
      </section>

      <section
        class="rounded-xl border border-blue-100 bg-gradient-to-r from-blue-50 to-indigo-50 p-4 dark:border-blue-500/40 dark:from-blue-950/30 dark:to-indigo-950/30 sm:p-6"
      >
        <h4 class="mb-2 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          配置教程
        </h4>
        <p class="text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          这里整理了 Codex CLI / OpenCode / Cherry Studio / Droid CLI / VS Code Codex 插件
          的配置教程，按步骤依次操作即可完成配置。
        </p>
      </section>

      <section
        class="rounded-xl border border-emerald-100 bg-white p-4 shadow-sm dark:border-emerald-500/40 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          环境要求
        </h4>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          在使用 Codex / OpenCode / Droid CLI 等 CLI 工具前，请先确认系统已安装 Node.js 环境。
        </p>
        <div
          class="mb-3 rounded-lg border border-emerald-200 bg-emerald-50 p-3 text-sm text-emerald-800 dark:border-emerald-500/40 dark:bg-emerald-950/30 dark:text-emerald-200"
        >
          如遇 npm 网络较慢，可设置镜像：
          <code class="rounded bg-white px-1 py-0.5 text-emerald-700 dark:bg-emerald-900/60">
            npm config set registry https://registry.npmmirror.com/
          </code>
        </div>
        <a
          class="text-sm font-semibold text-blue-600 underline dark:text-blue-400"
          href="https://nodejs.org/zh-cn/download"
          rel="noreferrer"
          target="_blank"
        >
          前往 Node.js 官网
        </a>
      </section>

      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          API 直连建议（Clash 配置直连教程）
        </h4>
        <details
          class="rounded-lg border border-slate-200 bg-slate-50 p-3 dark:border-slate-600 dark:bg-slate-900"
        >
          <summary
            class="inline-flex cursor-pointer items-center rounded-full border border-slate-200 bg-slate-50 px-3 py-1 text-sm font-medium text-slate-700 shadow-sm transition hover:bg-slate-100 dark:border-slate-600 dark:bg-slate-800 dark:text-slate-200 dark:hover:bg-slate-700"
          >
            点击展开
          </summary>
          <div class="mt-4 space-y-4 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
            <p>
              建议优先直连本站 API。如果你在 Clash Verge Rev v1.7.x 及以上版本里把
              <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-800">prepend-rules</code>
              写进 Merge Template/扩展配置，很可能根本没有应用到最终规则，导致依旧走代理。
            </p>

            <div>
              <h5 class="mb-2 text-base font-semibold text-slate-800 dark:text-slate-100">
                原因说明
              </h5>
              <p>
                Clash Verge Rev v1.7.x 起，“Merge
                配置”改名为“扩展配置”，扩展配置只做配置项覆写/合并；往规则数组里 prepend/append
                已迁移到订阅右键菜单的“编辑规则”。直接写
                <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-800">rules:</code>
                会整段覆盖规则，容易导致规则丢失或异常。
              </p>
            </div>

            <div>
              <h5 class="mb-2 text-base font-semibold text-slate-800 dark:text-slate-100">
                方案 A（推荐）：编辑规则添加前置规则
              </h5>
              <ol class="list-decimal space-y-1 pl-5">
                <li>在 Profiles/订阅 列表右键当前订阅 → 选择“编辑规则”。</li>
                <li>选择“前置规则 / prepend”。</li>
                <li>添加下面这条规则并保存，模式保持 Rule 即可。</li>
              </ol>
              <pre
                class="mt-3 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
              ><code>{{ domainSuffixRule }}</code></pre>
              <p class="mt-2 text-xs text-slate-500 dark:text-slate-400">
                提示：<code class="rounded bg-white px-1 py-0.5 dark:bg-slate-800"
                  >DOMAIN-SUFFIX,{{ domainSuffix }}</code
                >
                已包含
                <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-800">{{ wwwDomain }}</code
                >。
              </p>
            </div>

            <div>
              <h5 class="mb-2 text-base font-semibold text-slate-800 dark:text-slate-100">
                方案 B：扩展脚本强行插入规则
              </h5>
              <p>如需使用文本配置，可在订阅扩展脚本或全局扩展脚本中写入：</p>
              <pre
                class="mt-3 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
              ><code>{{ clashScript }}</code></pre>
            </div>

            <div>
              <h5 class="mb-2 text-base font-semibold text-slate-800 dark:text-slate-100">
                如何确认“真的直连”
              </h5>
              <ul class="list-disc space-y-1 pl-5">
                <li>打开 Connections/连接，访问 {{ wwwRootUrl }}/。</li>
                <li>
                  在连接详情查看 Rule 是否命中
                  <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-800"
                    >DOMAIN-SUFFIX,{{ domainSuffix }}</code
                  >
                  ，Chain 是否为 DIRECT。
                </li>
                <li>
                  若仍走代理，说明真实 Host 不是 {{ domainSuffix }}；按 Connections 里显示的 Host
                  再补一条
                  <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-800"
                    >DOMAIN-SUFFIX,实际域名,DIRECT</code
                  >。
                </li>
              </ul>
              <p class="mt-2">
                其他代理软件同样在“规则 / 分流 / 绕过代理（No Proxy）”里把
                <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-800">{{
                  domainSuffix
                }}</code>
                加入直连即可。
              </p>
            </div>
          </div>
        </details>
      </section>

      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          Codex CLI 配置（手动）
        </h4>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          适合习惯手动配置的用户，直接修改配置文件。
        </p>
        <p class="mb-2 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          首先安装 Codex 及其依赖插件：
        </p>
        <pre class="overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm">
<code>npm i -g @openai/codex</code>
        </pre>
        <p class="mt-4 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          在 <code class="rounded bg-slate-100 px-1 dark:bg-slate-800">~/.codex/config.toml</code>
          文件开头加入以下配置：
        </p>
        <pre
          class="mt-2 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
        >
<code>{{ codexConfigBlock }}</code>
        </pre>
        <p class="mt-4 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          在
          <code class="rounded bg-slate-100 px-1 dark:bg-slate-800">~/.codex/auth.json</code>
          文件中配置 API 密钥：
        </p>
        <pre
          class="mt-2 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
        >
<code>{
  "OPENAI_API_KEY": "替换为你的key"
}</code>
        </pre>
      </section>

      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          Codex 配置（CC Switch）推荐
        </h4>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          适合不想手动改配置文件的同学，按步骤填写即可。
        </p>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          在 CC Switch 中创建 Codex Provider，按下面参数填写即可。
        </p>
        <a
          class="text-sm font-semibold text-blue-600 underline dark:text-blue-400"
          href="https://github.com/farion1231/cc-switch/releases"
          rel="noreferrer"
          target="_blank"
        >
          下载 CC Switch
        </a>
        <ol
          class="mt-4 list-decimal space-y-2 pl-5 text-sm text-slate-600 dark:text-slate-300 sm:text-base"
        >
          <li>安装后，在应用顶部 Tab 选择 Codex，然后添加 Codex Provider。</li>
          <li>按下方参数填入并保存。</li>
        </ol>
        <div class="mt-4 grid gap-3">
          <div
            class="rounded-lg border border-slate-200 bg-slate-50 p-3 dark:border-slate-600 dark:bg-slate-800"
          >
            <div class="text-xs font-semibold text-slate-500 dark:text-slate-300">供应商名称</div>
            <div class="text-sm text-slate-700 dark:text-slate-100">GMN API</div>
          </div>
          <div
            class="rounded-lg border border-slate-200 bg-slate-50 p-3 dark:border-slate-600 dark:bg-slate-800"
          >
            <div class="text-xs font-semibold text-slate-500 dark:text-slate-300">API Key</div>
            <div class="text-sm text-slate-700 dark:text-slate-100">cr_******** 你的 key</div>
            <p class="mt-1 text-xs text-slate-500 dark:text-slate-400">
              填入分发给你的
              <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-900">cr_</code> 开头的 key。
            </p>
          </div>
          <div
            class="rounded-lg border border-slate-200 bg-slate-50 p-3 dark:border-slate-600 dark:bg-slate-800"
          >
            <div class="text-xs font-semibold text-slate-500 dark:text-slate-300">API 请求地址</div>
            <div class="text-sm text-slate-700 dark:text-slate-100">{{ openaiBaseUrl }}</div>
          </div>
        </div>
      </section>

      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          OpenCode 配置教程
        </h4>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          OpenCode 与 Codex 的配置相互独立，请按下方内容单独配置。
        </p>

        <div
          class="rounded-xl border border-slate-200 bg-slate-50 p-4 dark:border-slate-600 dark:bg-slate-800"
        >
          <h5 class="mb-2 text-base font-semibold text-slate-800 dark:text-slate-100">
            OpenCode CLI 配置 OpenCode
          </h5>
          <p class="mb-3 text-sm text-slate-600 dark:text-slate-300">
            适合使用 OpenCode CLI 的用户（已适配 OpenAI Compatible Provider）。
          </p>
          <a
            class="text-sm font-semibold text-blue-600 underline dark:text-blue-400"
            href="https://opencode.ai"
            rel="noreferrer"
            target="_blank"
          >
            OpenCode 官网
          </a>
          <ol class="mt-4 list-decimal space-y-2 pl-5 text-sm text-slate-600 dark:text-slate-300">
            <li>
              安装 OpenCode CLI：
              <pre
                class="mt-2 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
              >
<code>npm install -g opencode-ai
opencode auth login</code>
              </pre>
            </li>
            <li>登录时选择 Other，并设置 gmn 供应商信息。</li>
            <li>编辑配置文件，把 API Key 与 baseURL 替换为你的信息。</li>
          </ol>

          <div class="mt-4 grid gap-2">
            <div class="text-xs font-semibold text-slate-500 dark:text-slate-300">配置文件路径</div>
            <div class="text-sm text-slate-700 dark:text-slate-100">
              ~/.config/opencode/opencode.json
            </div>
            <div class="mt-2 text-xs font-semibold text-slate-500 dark:text-slate-300">baseURL</div>
            <div class="text-sm text-slate-700 dark:text-slate-100">{{ openaiV1Url }}</div>
            <p class="text-xs text-slate-500 dark:text-slate-400">
              提示：OpenCode 的 OpenAI Compatible Provider 通常使用
              <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-900">/openai/v1</code> 作为
              baseURL，我们这里进行了兼容，使用openai就行。
            </p>
          </div>

          <p class="mt-4 text-sm text-slate-600 dark:text-slate-300">
            opencode.json 示例（请替换 apiKey）
          </p>
          <pre
            class="mt-2 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
          >
<code>{{ openCodeConfigExample }}</code>
          </pre>
          <p class="mt-3 text-xs text-slate-500 dark:text-slate-400">
            小技巧：在 OpenCode 中按
            <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-900">Ctrl + T</code>
            可切换不同的推理强度（variants）。
          </p>
        </div>
      </section>

      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          Cherry Studio 接入教程
        </h4>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          这里仅提供 Codex（Openai-Response）接入方式。
        </p>
        <div class="space-y-2 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          <p>Codex 接入</p>
          <p>供应商类型：Openai-Response</p>
          <p>
            API 地址：<span class="font-semibold">{{ openaiBaseUrl }}</span>
          </p>
          <p>API Key：后台创建的 API 密钥（cr_ 开头）。重要：Codex 只支持 Openai-Response 标准。</p>
          <p>模型 ID（固定）：<span class="font-semibold">gpt-5</span></p>
        </div>
        <div
          class="mt-4 rounded-lg border border-amber-200 bg-amber-50 p-3 text-sm text-amber-800 dark:border-amber-500/40 dark:bg-amber-950/30 dark:text-amber-200"
        >
          <p class="font-semibold">Cherry Studio 地址格式重要说明</p>
          <p class="mt-2">推荐格式（不加结尾 /）：{{ openaiBaseUrl }}</p>
          <p class="mt-1">错误格式（单独以 / 结尾）：{{ openaiBaseUrl }}/</p>
          <p class="mt-2 text-xs">
            提示：推荐格式可让 Cherry Studio 自动拼接 v1；单独的 “/” 结尾可能导致 v1 被忽略。
          </p>
        </div>
      </section>

      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          Droid CLI 配置教程
        </h4>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          Droid CLI 读取
          <code class="rounded bg-slate-100 px-1 dark:bg-slate-800">~/.factory/config.json</code>
          ，可在其中添加 custom_models 指向本服务端点即可。
        </p>
        <div
          class="rounded-lg border border-rose-200 bg-rose-50 p-3 text-sm text-rose-800 dark:border-rose-500/40 dark:bg-rose-950/30 dark:text-rose-200"
        >
          注意：为避免冲突，如果你的
          <code class="rounded bg-white px-1 py-0.5 dark:bg-rose-900/60"
            >~/.factory/settings.json</code
          >
          中存在旧的 gmn 配置，请先清除后再按本教程配置并重启 Droid CLI，否则新配置可能不会生效。
        </div>
        <p class="mt-4 text-sm text-slate-600 dark:text-slate-300 sm:text-base">配置文件路径</p>
        <p class="text-sm font-semibold text-slate-700 dark:text-slate-100">
          ~/.factory/config.json
        </p>
        <p class="mt-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          config.json 示例（请替换 api_key）
        </p>
        <pre
          class="mt-2 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
        >
<code>{{ droidConfigExample }}</code>
        </pre>
        <p class="mt-2 text-xs text-slate-500 dark:text-slate-400">
          提示：将示例中的
          <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-900">api_key</code>
          替换为后台创建的
          <code class="rounded bg-white px-1 py-0.5 dark:bg-slate-900">cr_</code> 开头密钥即可。
        </p>
      </section>

      <section
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <h4 class="mb-3 text-lg font-semibold text-slate-900 dark:text-slate-100 sm:text-xl">
          Visual Studio Code 插件安装教程
        </h4>
        <p class="mb-3 text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          适合通过 VS Code 图形界面安装 Codex 插件的用户。
        </p>
        <ol
          class="list-decimal space-y-5 pl-5 text-sm text-slate-600 dark:text-slate-300 sm:text-base"
        >
          <li>打开 VS Code 后先选择任意项目文件夹进入工作区。</li>
          <li>
            打开左侧插件扩展界面进入扩展面板。
            <img
              alt="VS Code 插件扩展入口"
              class="tutorial-media"
              :src="tutorialImages.vsCodeEntry"
            />
          </li>
          <li>
            搜索 Codex，出现如图所示结果后点击安装。
            <img
              alt="搜索 Codex 并安装"
              class="tutorial-media"
              :src="tutorialImages.vsCodeSearch"
            />
          </li>
          <li>
            安装完成后侧栏会出现 Codex 入口。
            <img
              alt="侧栏出现 Codex 入口"
              class="tutorial-media"
              :src="tutorialImages.vsCodeSidebar"
            />
          </li>
          <li>
            安装完成后，继续配置 Codex 的全局配置文件。在
            <code class="rounded bg-slate-100 px-1 dark:bg-slate-800">~/.codex/config.toml</code>
            在文件开头加入以下配置：
            <pre
              class="mt-3 overflow-x-auto rounded-lg bg-slate-900 p-3 text-xs text-green-200 sm:text-sm"
            ><code>{{ codexConfigBlock }}</code></pre>
          </li>
          <li>
            若之前使用官方或其他平台登录过，请先按图退出登录。
            <img alt="退出已有登录" class="tutorial-media" :src="tutorialImages.vsCodeLogout" />
          </li>
          <li>
            选择 Use API Key 方式进行登录。
            <img
              alt="选择 Use API Key"
              class="tutorial-media"
              :src="tutorialImages.vsCodeUseApiKey"
            />
          </li>
          <li>
            输入发货时提供的 cr 开头 key，然后点击 OK。
            <img alt="输入 API Key" class="tutorial-media" :src="tutorialImages.vsCodeInputKey" />
          </li>
          <li>
            点击 Continue 完成登录流程。
            <img alt="点击 Continue" class="tutorial-media" :src="tutorialImages.vsCodeContinue" />
          </li>
          <li>
            登录成功后即可开始对话，底部可切换模型与强度。
            <img alt="登录成功界面" class="tutorial-media" :src="tutorialImages.vsCodeSuccess" />
          </li>
        </ol>
      </section>

      <section
        v-if="false"
        class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/40 sm:p-6"
      >
        <p class="text-sm text-slate-600 dark:text-slate-300 sm:text-base">
          其他 Codex 使用教程可自行在搜索引擎中搜索“Codex使用方式”。
        </p>
        <img
          alt="售后QQ群二维码"
          class="mt-4 w-full rounded-lg border border-slate-200 dark:border-slate-600"
          :src="tutorialImages.supportQr"
        />
      </section>
    </div>
  </div>
</template>

<script setup>
const resolveBaseOrigin = () => {
  const customPrefix = import.meta.env.VITE_API_BASE_PREFIX
  if (customPrefix) {
    return customPrefix.replace(/\/$/, '')
  }

  if (typeof window !== 'undefined' && window.location) {
    if (window.location.origin) {
      return window.location.origin
    }
    if (window.location.protocol && window.location.host) {
      return `${window.location.protocol}//${window.location.host}`
    }
  }

  return ''
}

const baseOrigin = resolveBaseOrigin()
let parsedOrigin = null

try {
  parsedOrigin = baseOrigin ? new URL(baseOrigin) : null
} catch (error) {
  parsedOrigin = null
}

const locationHost = typeof window !== 'undefined' && window.location ? window.location.host : ''
const locationProtocol =
  typeof window !== 'undefined' && window.location && window.location.protocol
    ? window.location.protocol
    : 'https:'

const baseHost = parsedOrigin && parsedOrigin.host ? parsedOrigin.host : locationHost
const baseProtocol =
  parsedOrigin && parsedOrigin.protocol ? parsedOrigin.protocol : locationProtocol
const baseRootUrl = baseHost ? `${baseProtocol}//${baseHost}` : ''
const normalizedRootUrl = (baseOrigin || baseRootUrl).replace(/\/$/, '')

const domainSuffix = baseHost.replace(/:\d+$/, '')
const wwwDomain = domainSuffix.startsWith('www.') ? domainSuffix : `www.${domainSuffix}`
const wwwRootUrl = `${baseProtocol}//${wwwDomain}`

const openaiBaseUrl = `${normalizedRootUrl}/openai`
const openaiV1Url = `${normalizedRootUrl}/openai`
const domainSuffixRule = `DOMAIN-SUFFIX,${domainSuffix},DIRECT`

const clashScript = `function main(config, profileName) {\n  const rule = '${domainSuffixRule}'\n  const rules = Array.isArray(config.rules) ? config.rules : []\n  if (!rules.includes(rule)) {\n    config.rules = [rule, ...rules]\n  }\n  return config\n}`

const codexConfigBlock = `model_provider = "custom"\nmodel = "gpt-5.2-codex"\nmodel_reasoning_effort = "high"\ndisable_response_storage = true\n\n[model_providers.custom]\nname = "custom"\nbase_url = "${openaiBaseUrl}"\nwire_api = "responses"\nrequires_openai_auth = true`

const openCodeConfigExample = `{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "gmn": {
      "npm": "@ai-sdk/openai",
      "name": "GMN",
      "options": {
        "baseURL": "${openaiV1Url}",
        "apiKey": "替换为你的key"
      },
      "models": {
        "gpt-5.2-codex": {
          "variants": {
            "xhigh": {
              "reasoningEffort": "xhigh",
              "textVerbosity": "low",
              "reasoningSummary": "auto"
            },
            "high": {
              "reasoningEffort": "high",
              "textVerbosity": "low",
              "reasoningSummary": "auto"
            },
            "medium": {
              "reasoningEffort": "medium",
              "textVerbosity": "low",
              "reasoningSummary": "auto"
            },
            "low": {
              "reasoningEffort": "low",
              "textVerbosity": "low",
              "reasoningSummary": "auto"
            }
          }
        }
      }
    }
  }
}`

const droidConfigExample = `{
  "custom_models": [
    {
      "model_display_name": "GPT-5.2-Codex [gmn]",
      "model": "gpt-5.2-codex",
      "base_url": "${openaiBaseUrl}",
      "api_key": "替换为你的key",
      "provider": "openai",
      "max_tokens": 16384,
      "extra_args": {
        "reasoning": {
          "effort": "high"
        }
      }
    }
  ]
}`

const tutorialImages = {
  vsCodeEntry: new URL('../assets/tutorial/img_94434f59_1.png', import.meta.url).href,
  vsCodeSearch: new URL('../assets/tutorial/img_94434f59_2.png', import.meta.url).href,
  vsCodeSidebar: new URL('../assets/tutorial/img_94434f59_3.png', import.meta.url).href,
  vsCodeLogout: new URL('../assets/tutorial/img_94434f59_4.png', import.meta.url).href,
  vsCodeUseApiKey: new URL('../assets/tutorial/img_94434f59_5.png', import.meta.url).href,
  vsCodeInputKey: new URL('../assets/tutorial/img_94434f59_6.png', import.meta.url).href,
  vsCodeContinue: new URL('../assets/tutorial/img_94434f59_7.png', import.meta.url).href,
  vsCodeSuccess: new URL('../assets/tutorial/img_94434f59_8.png', import.meta.url).href,
  supportQr: new URL('../assets/tutorial/img_94434f59_9.png', import.meta.url).href
}
</script>

<style scoped>
.tutorial-container {
  min-height: calc(100vh - 300px);
}

.tutorial-content {
  animation: fadeIn 0.3s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

code {
  font-family: 'Fira Code', 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
}

.tutorial-content h4 {
  scroll-margin-top: 100px;
}

.tutorial-content .bg-gradient-to-r {
  transition: all 0.2s ease;
}

.tutorial-content .bg-gradient-to-r:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.tutorial-media {
  display: block;
  max-width: min(720px, 100%);
  margin: 0.75rem auto 0;
  border-radius: 12px;
  box-shadow: 0 14px 30px rgba(15, 23, 42, 0.12);
}

/* 暗色主题优化 */
/* 顶部标签栏背景 - 增加深度感 */
html.dark :deep(.bg-gray-100) {
  background-color: #1f2937 !important;
  border: 1px solid rgba(75, 85, 99, 0.5);
}

html.dark :deep(.bg-gray-700) {
  background-color: #1a202c !important;
  border: 1px solid rgba(75, 85, 99, 0.6);
}

/* 活动标签页 - 更明显的对比和高亮 */
html.dark :deep(button.bg-gray-800) {
  background-color: #3b82f6 !important;
  border: 1px solid rgba(59, 130, 246, 0.8);
  box-shadow: 0 2px 8px rgba(59, 130, 246, 0.4);
  color: #ffffff !important;
}

/* 非活动标签页文字颜色优化 */
html.dark :deep(button:not(.bg-gray-800).text-gray-600) {
  color: #9ca3af !important;
}

html.dark :deep(button:not(.bg-gray-800).hover\:text-gray-900:hover) {
  color: #d1d5db !important;
}

/* 代码块 - 减少纯黑，增加层次感 */
html.dark :deep(.bg-gray-900) {
  background-color: #1e293b !important;
  border: 1px solid rgba(71, 85, 105, 0.6);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.2);
}

/* 优化链接颜色 - 更亮更突出 */
html.dark :deep(a) {
  color: #60a5fa !important;
  text-decoration: underline;
}

html.dark :deep(a:hover) {
  color: #93c5fd !important;
}

/* 行内代码样式优化 */
html.dark :deep(code.rounded) {
  background-color: #334155 !important;
  border: 1px solid rgba(100, 116, 139, 0.6);
  color: #fbbf24 !important;
  padding: 0.125rem 0.375rem;
}

/* 注意事项框 - 蓝色系列 */
html.dark :deep(.border-blue-200) {
  border-color: rgba(59, 130, 246, 0.5) !important;
}

html.dark :deep(.bg-blue-50) {
  background-color: rgba(37, 99, 235, 0.15) !important;
  border: 1px solid rgba(59, 130, 246, 0.3);
}

/* 成功提示框 - 绿色系列 */
html.dark :deep(.border-green-200) {
  border-color: rgba(34, 197, 94, 0.5) !important;
}

html.dark :deep(.bg-green-50) {
  background-color: rgba(34, 197, 94, 0.15) !important;
  border: 1px solid rgba(34, 197, 94, 0.3);
}

/* 警告提示框 - 黄色系列 */
html.dark :deep(.border-yellow-200) {
  border-color: rgba(250, 204, 21, 0.5) !important;
}

html.dark :deep(.bg-yellow-50) {
  background-color: rgba(250, 204, 21, 0.15) !important;
  border: 1px solid rgba(250, 204, 21, 0.3);
}

/* Indigo 提示框 */
html.dark :deep(.border-indigo-200) {
  border-color: rgba(99, 102, 241, 0.5) !important;
}

html.dark :deep(.bg-indigo-50) {
  background-color: rgba(99, 102, 241, 0.15) !important;
  border: 1px solid rgba(99, 102, 241, 0.3);
}

/* Purple 提示框 */
html.dark :deep(.border-purple-200) {
  border-color: rgba(168, 85, 247, 0.5) !important;
}

/* 渐变背景优化 */
html.dark :deep(.from-purple-50) {
  background: linear-gradient(
    to right,
    rgba(168, 85, 247, 0.15),
    rgba(236, 72, 153, 0.15)
  ) !important;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

html.dark :deep(.from-blue-50) {
  background: linear-gradient(
    to right,
    rgba(59, 130, 246, 0.15),
    rgba(99, 102, 241, 0.15)
  ) !important;
  border: 1px solid rgba(59, 130, 246, 0.3);
}

html.dark :deep(.from-green-50) {
  background: linear-gradient(
    to right,
    rgba(34, 197, 94, 0.15),
    rgba(16, 185, 129, 0.15)
  ) !important;
  border: 1px solid rgba(34, 197, 94, 0.3);
}

/* 文字对比度优化 - 提高可读性 */
html.dark :deep(.text-gray-400) {
  color: #9ca3af !important;
}

html.dark :deep(.text-gray-600) {
  color: #d1d5db !important;
}

html.dark :deep(.text-gray-700) {
  color: #e5e7eb !important;
}

html.dark :deep(.text-gray-800) {
  color: #f3f4f6 !important;
}

/* 彩色文字优化 - 提高亮度 */
html.dark :deep(.text-blue-600) {
  color: #60a5fa !important;
}

html.dark :deep(.text-blue-700) {
  color: #60a5fa !important;
}

html.dark :deep(.text-blue-800) {
  color: #93c5fd !important;
}

html.dark :deep(.text-green-700) {
  color: #4ade80 !important;
}

html.dark :deep(.text-green-800) {
  color: #86efac !important;
}

html.dark :deep(.text-yellow-700) {
  color: #facc15 !important;
}

html.dark :deep(.text-yellow-800) {
  color: #fde047 !important;
}

html.dark :deep(.text-indigo-700) {
  color: #818cf8 !important;
}

html.dark :deep(.text-indigo-800) {
  color: #a5b4fc !important;
}

/* 标题对比度优化 */
html.dark :deep(h3),
html.dark :deep(h4),
html.dark :deep(h5),
html.dark :deep(h6) {
  color: #f9fafb !important;
}

/* 内嵌背景色优化 */
html.dark :deep(.bg-yellow-100) {
  background-color: rgba(250, 204, 21, 0.2) !important;
}

html.dark :deep(.bg-indigo-100) {
  background-color: rgba(99, 102, 241, 0.2) !important;
}

/* 白色背景框体优化 - 选中的标签页 */
html.dark :deep(.bg-white) {
  background-color: #374151 !important;
  border: 1px solid rgba(107, 114, 128, 0.5);
}

/* 边框颜色统一优化 */
html.dark :deep(.border-purple-700) {
  border-color: rgba(168, 85, 247, 0.6) !important;
}

html.dark :deep(.border-blue-100) {
  border-color: rgba(59, 130, 246, 0.4) !important;
}

html.dark :deep(.border-green-100) {
  border-color: rgba(34, 197, 94, 0.4) !important;
}

html.dark :deep(.border-purple-100) {
  border-color: rgba(168, 85, 247, 0.4) !important;
}

/* 代码块内文字颜色优化 */
html.dark :deep(.text-green-400) {
  color: #4ade80 !important;
}

html.dark :deep(.text-gray-300) {
  color: #d1d5db !important;
}
</style>
