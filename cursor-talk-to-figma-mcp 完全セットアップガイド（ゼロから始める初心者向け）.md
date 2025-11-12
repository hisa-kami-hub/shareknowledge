---


---

<h1 id="cursor-talk-to-figma-mcp-完全セットアップガイド（ゼロから始める初心者向け）">cursor-talk-to-figma-mcp 完全セットアップガイド（ゼロから始める初心者向け）</h1>
<p>このガイドは、まだ何もインストールしていない状態から、cursor-talk-to-figma-mcpを使い始めるまでの<strong>全手順</strong>を解説します。</p>
<blockquote>
<p><strong>既にセットアップ済みの方は</strong>: <code>CURSOR_TALK_TO_FIGMA_SETUP_GUIDE.md</code> をご覧ください。</p>
</blockquote>
<hr>
<h2 id="目次">目次</h2>
<ol>
<li>
<p><a href="#%E3%81%93%E3%81%AE%E3%83%84%E3%83%BC%E3%83%AB%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6">このツールについて</a></p>
</li>
<li>
<p><a href="#%E5%BF%85%E8%A6%81%E3%81%AA%E3%82%82%E3%81%AE">必要なもの</a></p>
</li>
<li>
<p><a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%971-bun%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB">ステップ1: Bunのインストール</a></p>
</li>
<li>
<p><a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%972-git%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB">ステップ2: Gitのインストール</a></p>
</li>
<li>
<p><a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%973-%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%AE%E3%82%AF%E3%83%AD%E3%83%BC%E3%83%B3">ステップ3: プロジェクトのクローン</a></p>
</li>
<li>
<p><a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%974-%E4%BE%9D%E5%AD%98%E9%96%A2%E4%BF%82%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB">ステップ4: 依存関係のインストール</a></p>
</li>
<li>
<p><a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%975-%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%AE%E3%83%93%E3%83%AB%E3%83%89">ステップ5: プロジェクトのビルド</a></p>
</li>
<li>
<p><a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%976-cursor-mcp%E8%A8%AD%E5%AE%9A">ステップ6: Cursor MCP設定</a></p>
</li>
<li>
<p><a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%977-%E4%BD%BF%E7%94%A8%E9%96%8B%E5%A7%8B">ステップ7: 使用開始</a></p>
</li>
<li>
<p><a href="#%E3%83%88%E3%83%A9%E3%83%96%E3%83%AB%E3%82%B7%E3%83%A5%E3%83%BC%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0">トラブルシューティング</a></p>
</li>
<li>
<p><a href="#%E5%8F%82%E8%80%83%E3%83%AA%E3%83%B3%E3%82%AF">参考リンク</a></p>
</li>
</ol>
<hr>
<h2 id="このツールについて">このツールについて</h2>
<p><strong>cursor-talk-to-figma-mcp</strong> は、Cursor AIから自然言語でFigmaデザインを操作できるツールです。</p>
<h3 id="特徴">特徴</h3>
<ul>
<li>
<p>Cursorから直接Figmaを操作</p>
</li>
<li>
<p>自然言語でデザイン変更</p>
</li>
<li>
<p>50以上のMCPツールを提供</p>
</li>
<li>
<p>リアルタイムでデザインに反映</p>
</li>
</ul>
<h3 id="システム構成">システム構成</h3>
<pre><code>
┌─────────────┐ WebSocket ┌──────────────┐ MCP ┌──────────┐

│ Figma │ ←───(3055)────→ │ WebSocket │ ←────→ │ Cursor │

│ プラグイン │ │ Server │ │ AI │

└─────────────┘ └──────────────┘ └──────────┘

</code></pre>
<hr>
<h2 id="必要なもの">必要なもの</h2>
<p>セットアップを始める前に、以下を準備してください：</p>
<ul>
<li>
<p>✅ <strong>Windows 10 (version 1809以降)</strong></p>
</li>
<li>
<p>✅ <strong>Cursor エディタ</strong> がインストール済み</p>
</li>
<li>
<p>✅ <strong>Figmaアカウント</strong> （無料でOK）</p>
</li>
<li>
<p>✅ <strong>インターネット接続</strong></p>
</li>
<li>
<p>✅ <strong>PowerShell</strong> （Windowsに標準搭載）</p>
</li>
</ul>
<hr>
<h2 id="ステップ1-bunのインストール">ステップ1: Bunのインストール</h2>
<p><strong>Bun</strong> は高速なJavaScriptランタイムです。このプロジェクトの実行に必須です。</p>
<h3 id="powershellを開く">1.1 PowerShellを開く</h3>
<ol>
<li>
<p><strong>Windowsキー</strong> を押して検索</p>
</li>
<li>
<p>「<strong>PowerShell</strong>」と入力</p>
</li>
<li>
<p>「<strong>Windows PowerShell</strong>」を右クリック</p>
</li>
<li>
<p>「<strong>管理者として実行</strong>」を選択</p>
</li>
</ol>
<h3 id="bunをインストール">1.2 Bunをインストール</h3>
<p>PowerShellで以下のコマンドを実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
powershell <span class="token operator">-</span>c <span class="token string">"irm bun.sh/install.ps1|iex"</span>

</code></pre>
<h3 id="インストール確認">1.3 インストール確認</h3>
<p>新しいPowerShellウィンドウを開いて、以下を実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
bun <span class="token operator">--</span>version

</code></pre>
<p><strong>表示例</strong>:</p>
<pre><code>
1.3.1

</code></pre>
<blockquote>
<p><strong>注意</strong>: バージョンが表示されない場合は、<a href="#bun%E3%81%8C%E8%AA%8D%E8%AD%98%E3%81%95%E3%82%8C%E3%81%AA%E3%81%84%E5%A0%B4%E5%90%88">トラブルシューティング</a> をご覧ください。</p>
</blockquote>
<hr>
<h2 id="ステップ2-gitのインストール">ステップ2: Gitのインストール</h2>
<p><strong>Git</strong> はプロジェクトをダウンロードするために必要です。</p>
<h3 id="gitがインストール済みか確認">2.1 Gitがインストール済みか確認</h3>
<p>PowerShellで以下を実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
git <span class="token operator">--</span>version

</code></pre>
<p><strong>バージョンが表示される場合</strong>: 既にインストール済みです。<a href="#%E3%82%B9%E3%83%86%E3%83%83%E3%83%973-%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%AE%E3%82%AF%E3%83%AD%E3%83%BC%E3%83%B3">ステップ3</a> へ進んでください。</p>
<p><strong>「git は認識されません」と表示される場合</strong>: 以下の手順でインストールします。</p>
<h3 id="gitをダウンロード">2.2 Gitをダウンロード</h3>
<ol>
<li>
<p>公式サイトを開く: <a href="https://git-scm.com/download/win">https://git-scm.com/download/win</a></p>
</li>
<li>
<p>「<strong>64-bit Git for Windows Setup</strong>」をダウンロード</p>
</li>
<li>
<p>ダウンロードしたファイルを実行</p>
</li>
</ol>
<h3 id="gitをインストール">2.3 Gitをインストール</h3>
<p>インストーラーが起動したら：</p>
<ol>
<li>
<p>「<strong>Next</strong>」を何度かクリック（基本的にデフォルト設定でOK）</p>
</li>
<li>
<p>重要な設定画面：</p>
</li>
</ol>
<ul>
<li><strong>"Adjusting your PATH environment"</strong>: 「<strong>Git from the command line and also from 3rd-party software</strong>」を選択</li>
</ul>
<ol start="3">
<li>インストール完了まで進める</li>
</ol>
<h3 id="インストール確認-1">2.4 インストール確認</h3>
<p>新しいPowerShellウィンドウを開いて、以下を実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
git <span class="token operator">--</span>version

</code></pre>
<p><strong>表示例</strong>:</p>
<pre><code>
git version 2.43.0.windows.1

</code></pre>
<hr>
<h2 id="ステップ3-プロジェクトのクローン">ステップ3: プロジェクトのクローン</h2>
<h3 id="作業ディレクトリに移動">3.1 作業ディレクトリに移動</h3>
<p>PowerShellで以下を実行（好きなディレクトリに変更してOK）：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
cd C:\Cursorprojects

</code></pre>
<blockquote>
<p><strong>ディレクトリが存在しない場合</strong>: 先に作成してください</p>
</blockquote>
<blockquote>
<pre class=" language-powershell"><code class="prism  language-powershell"></code></pre>
</blockquote>
<blockquote>
<p>mkdir C:\Cursorprojects</p>
</blockquote>
<blockquote>
<p>cd C:\Cursorprojects</p>
</blockquote>
<blockquote>
<pre><code></code></pre>
</blockquote>
<h3 id="リポジトリをクローン">3.2 リポジトリをクローン</h3>
<pre class=" language-powershell"><code class="prism  language-powershell">
git clone https:<span class="token operator">/</span><span class="token operator">/</span>github<span class="token punctuation">.</span>com<span class="token operator">/</span>grab<span class="token operator">/</span>cursor<span class="token operator">-</span>talk<span class="token operator">-</span>to<span class="token operator">-</span>figma<span class="token operator">-</span>mcp<span class="token punctuation">.</span>git

</code></pre>
<p><strong>表示例</strong>:</p>
<pre><code>
Cloning into 'cursor-talk-to-figma-mcp'...

remote: Enumerating objects: 150, done.

...

</code></pre>
<h3 id="プロジェクトディレクトリに移動">3.3 プロジェクトディレクトリに移動</h3>
<pre class=" language-powershell"><code class="prism  language-powershell">
cd cursor<span class="token operator">-</span>talk<span class="token operator">-</span>to<span class="token operator">-</span>figma<span class="token operator">-</span>mcp

</code></pre>
<hr>
<h2 id="ステップ4-依存関係のインストール">ステップ4: 依存関係のインストール</h2>
<h3 id="セットアップコマンドを実行">4.1 セットアップコマンドを実行</h3>
<p>プロジェクトディレクトリ内で以下を実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
bun setup

</code></pre>
<p>このコマンドは以下を自動的に実行します：</p>
<ul>
<li>
<p>依存パッケージのインストール</p>
</li>
<li>
<p>プロジェクトのビルド</p>
</li>
<li>
<p>Cursor MCP設定の準備</p>
</li>
</ul>
<p><strong>表示例</strong>:</p>
<pre><code>
bun install v1.3.1

...

Installing dependencies...

✓ Installed [XX] packages

</code></pre>
<h3 id="手動でインストール（bun-setupが失敗した場合）">4.2 手動でインストール（bun setupが失敗した場合）</h3>
<pre class=" language-powershell"><code class="prism  language-powershell">
bun install

</code></pre>
<hr>
<h2 id="ステップ5-プロジェクトのビルド">ステップ5: プロジェクトのビルド</h2>
<h3 id="ビルドを実行">5.1 ビルドを実行</h3>
<pre class=" language-powershell"><code class="prism  language-powershell">
bun run build

</code></pre>
<p><strong>表示例</strong>:</p>
<pre><code>
Building...

✓ Build completed

</code></pre>
<h3 id="ビルド確認">5.2 ビルド確認</h3>
<p><code>dist</code> フォルダが作成されたことを確認：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
<span class="token function">ls</span> dist

</code></pre>
<p><strong>表示例</strong>:</p>
<pre><code>
Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 2025/11/07 10:30 12345 server.js

...

</code></pre>
<hr>
<h2 id="ステップ6-cursor-mcp設定">ステップ6: Cursor MCP設定</h2>
<h3 id="設定ディレクトリを作成">6.1 設定ディレクトリを作成</h3>
<p>Cursorプロジェクトのルートディレクトリ（例: <code>C:\Cursorprojects\figmaxcursor01</code>）で以下を実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
<span class="token comment"># プロジェクトディレクトリに移動</span>

cd C:\Cursorprojects\figmaxcursor01

  

<span class="token comment"># .cursor ディレクトリを作成（既に存在する場合はスキップ）</span>

mkdir <span class="token punctuation">.</span>cursor

</code></pre>
<h3 id="mcp設定ファイルを作成">6.2 MCP設定ファイルを作成</h3>
<p><code>.cursor</code> ディレクトリ内に <code>mcp.json</code> ファイルを作成します。</p>
<p>PowerShellで以下を実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
@<span class="token string">"

{

"</span>mcpServers<span class="token string">": {

"</span>TalkToFigma<span class="token string">": {

"</span>command<span class="token string">": "</span>bun<span class="token string">",

"</span>args<span class="token string">": ["</span>C:\\Cursorprojects\\cursor<span class="token operator">-</span>talk<span class="token operator">-</span>to<span class="token operator">-</span>figma<span class="token operator">-</span>mcp\\dist\\server<span class="token punctuation">.</span>js<span class="token string">"]

}

}

}

"</span>@ <span class="token punctuation">|</span> <span class="token function">Out-File</span> <span class="token operator">-</span>FilePath <span class="token string">".\.cursor\mcp.json"</span> <span class="token operator">-</span>Encoding utf8

</code></pre>
<blockquote>
<p><strong>重要</strong>: パスは実際にクローンした場所に合わせて変更してください。</p>
</blockquote>
<h3 id="設定確認">6.3 設定確認</h3>
<pre class=" language-powershell"><code class="prism  language-powershell">
<span class="token function">cat</span> <span class="token punctuation">.</span>\<span class="token punctuation">.</span>cursor\mcp<span class="token punctuation">.</span>json

</code></pre>
<p>以下のような内容が表示されればOK：</p>
<pre class=" language-json"><code class="prism  language-json">
<span class="token punctuation">{</span>

<span class="token string">"mcpServers"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>

<span class="token string">"TalkToFigma"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>

<span class="token string">"command"</span><span class="token punctuation">:</span> <span class="token string">"bun"</span><span class="token punctuation">,</span>

<span class="token string">"args"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token string">"C:\\Cursorprojects\\cursor-talk-to-figma-mcp\\dist\\server.js"</span><span class="token punctuation">]</span>

<span class="token punctuation">}</span>

<span class="token punctuation">}</span>

<span class="token punctuation">}</span>

</code></pre>
<h3 id="代替設定（グローバルインストール版）">6.4 代替設定（グローバルインストール版）</h3>
<p>npm経由でグローバルにインストールする場合：</p>
<pre class=" language-json"><code class="prism  language-json">
<span class="token punctuation">{</span>

<span class="token string">"mcpServers"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>

<span class="token string">"TalkToFigma"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>

<span class="token string">"command"</span><span class="token punctuation">:</span> <span class="token string">"bunx"</span><span class="token punctuation">,</span>

<span class="token string">"args"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token string">"cursor-talk-to-figma-mcp@latest"</span><span class="token punctuation">]</span>

<span class="token punctuation">}</span>

<span class="token punctuation">}</span>

<span class="token punctuation">}</span>

</code></pre>
<hr>
<h2 id="ステップ7-使用開始">ステップ7: 使用開始</h2>
<p>これでセットアップは完了です！実際に使ってみましょう。</p>
<h3 id="websocketサーバーを起動">7.1 WebSocketサーバーを起動</h3>
<p>新しいPowerShellウィンドウを開き、プロジェクトディレクトリに移動：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
cd C:\Cursorprojects\cursor<span class="token operator">-</span>talk<span class="token operator">-</span>to<span class="token operator">-</span>figma<span class="token operator">-</span>mcp

bun socket

</code></pre>
<p><strong>正常起動時の表示</strong>:</p>
<pre><code>
WebSocket server running on port 3055

</code></pre>
<blockquote>
<p><strong>重要</strong>: このターミナルウィンドウは<strong>閉じないでください</strong>。作業中は常に起動しておく必要があります。</p>
</blockquote>
<h3 id="figmaプラグインをインストール">7.2 Figmaプラグインをインストール</h3>
<h4 id="方法a-コミュニティからインストール（推奨）">方法A: コミュニティからインストール（推奨）</h4>
<ol>
<li>
<p><strong>Figmaを開く</strong></p>
</li>
<li>
<p>メニューバー → <code>Plugins</code> → <code>Find more plugins</code></p>
</li>
<li>
<p>検索ボックスに「<strong>Cursor Talk To Figma MCP Plugin</strong>」と入力</p>
</li>
<li>
<p>「<strong>Install</strong>」をクリック</p>
</li>
</ol>
<p>直接リンク: <a href="https://www.figma.com/community/plugin/1485687494525374295">https://www.figma.com/community/plugin/1485687494525374295</a></p>
<h4 id="方法b-ローカル開発版をインストール">方法B: ローカル開発版をインストール</h4>
<ol>
<li>
<p><strong>Figmaを開く</strong></p>
</li>
<li>
<p>メニューバー → <code>Plugins</code> → <code>Development</code> → <code>Import plugin from manifest</code></p>
</li>
<li>
<p>以下のファイルを選択：</p>
</li>
</ol>
<pre><code>
C:\Cursorprojects\cursor-talk-to-figma-mcp\src\cursor_mcp_plugin\manifest.json

</code></pre>
<h3 id="figmaでプラグインを起動">7.3 Figmaでプラグインを起動</h3>
<ol>
<li>
<p>Figmaで新規ファイルまたは既存ファイルを開く</p>
</li>
<li>
<p>メニューバー → <code>Plugins</code> → <code>Cursor Talk To Figma MCP Plugin</code> → <code>Run</code></p>
</li>
<li>
<p>モーダルで「<strong>Use localhost</strong>」を選択</p>
</li>
<li>
<p>「<strong>Connect</strong>」ボタンをクリック</p>
</li>
</ol>
<p><strong>接続成功時の表示</strong>:</p>
<pre><code>
✅ Connected to WebSocket

Channel: abc-def-ghi-jkl

</code></pre>
<blockquote>
<p><strong>チャネル名をメモしてください</strong>。Cursorから接続する際に必要です。</p>
</blockquote>
<h3 id="cursorから接続">7.4 Cursorから接続</h3>
<ol>
<li>
<p><strong>Cursorを再起動</strong>（MCP設定を読み込むため）</p>
</li>
<li>
<p>Cursorで新しいチャットを開始</p>
</li>
<li>
<p>以下のように入力：</p>
</li>
</ol>
<pre><code>
join_channelツールを使って、チャネル "abc-def-ghi-jkl" に接続してください

</code></pre>
<p>（チャネル名はFigmaプラグインに表示されたものを使用）</p>
<p><strong>Cursorの応答例</strong>:</p>
<pre><code>
join_channelツールでチャネル "abc-def-ghi-jkl" に接続しました

</code></pre>
<h3 id="figmaを操作してみる">7.5 Figmaを操作してみる</h3>
<p>接続が完了したら、自然言語でFigmaを操作できます！</p>
<p><strong>試してみる例</strong>:</p>
<pre><code>
「現在のFigmaページにある全てのレイヤーを教えて」

</code></pre>
<pre><code>
「中央に赤い正方形を作成して」

</code></pre>
<pre><code>
「"Hello"というテキストを"こんにちは"に変更して」

</code></pre>
<hr>
<h2 id="トラブルシューティング">トラブルシューティング</h2>
<h3 id="bunが認識されない場合">Bunが認識されない場合</h3>
<p><strong>原因</strong>: 環境変数PATHが設定されていない</p>
<p><strong>解決方法</strong>:</p>
<p>PowerShellで以下を実行：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
<span class="token namespace">[System.Environment]</span>::SetEnvironmentVariable<span class="token punctuation">(</span>

<span class="token string">"Path"</span><span class="token punctuation">,</span>

<span class="token namespace">[System.Environment]</span>::GetEnvironmentVariable<span class="token punctuation">(</span><span class="token string">"Path"</span><span class="token punctuation">,</span> <span class="token string">"User"</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token string">";<span class="token variable">$env</span>:USERPROFILE\.bun\bin"</span><span class="token punctuation">,</span>

<span class="token namespace">[System.EnvironmentVariableTarget]</span>::User

<span class="token punctuation">)</span>

</code></pre>
<p>その後、PowerShellを再起動して、再度確認：</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
bun <span class="token operator">--</span>version

</code></pre>
<hr>
<h3 id="websocketサーバーが起動しない">WebSocketサーバーが起動しない</h3>
<p><strong>エラー</strong>: 「Port 3055 is already in use」</p>
<p><strong>原因</strong>: ポート3055が既に使用中</p>
<p><strong>解決方法</strong>:</p>
<ol>
<li>使用中のプロセスを確認：</li>
</ol>
<pre class=" language-powershell"><code class="prism  language-powershell">
netstat <span class="token operator">-</span>ano <span class="token punctuation">|</span> findstr :3055

</code></pre>
<ol start="2">
<li>表示されたプロセスIDを終了：</li>
</ol>
<pre class=" language-powershell"><code class="prism  language-powershell">
taskkill <span class="token operator">/</span>PID <span class="token punctuation">[</span>プロセスID<span class="token punctuation">]</span> <span class="token operator">/</span>F

</code></pre>
<ol start="3">
<li>再度サーバーを起動：</li>
</ol>
<pre class=" language-powershell"><code class="prism  language-powershell">
bun socket

</code></pre>
<hr>
<h3 id="figmaプラグインが接続できない">Figmaプラグインが接続できない</h3>
<p><strong>確認項目</strong>:</p>
<ol>
<li>✅ WebSocketサーバーが起動しているか？</li>
</ol>
<ul>
<li>ターミナルに「WebSocket server running on port 3055」と表示されているか確認</li>
</ul>
<ol start="2">
<li>
<p>✅ Figmaプラグインで「Use localhost」を選択しているか？</p>
</li>
<li>
<p>✅ ファイアウォールでポート3055がブロックされていないか？</p>
</li>
</ol>
<ul>
<li>Windows Defender ファイアウォールの設定を確認</li>
</ul>
<ol start="4">
<li>✅ WSL環境の場合は <code>src/socket.ts</code> で <code>hostname: "0.0.0.0"</code> のコメントを解除</li>
</ol>
<hr>
<h3 id="cursorがチャネルに接続できない">Cursorがチャネルに接続できない</h3>
<p><strong>確認項目</strong>:</p>
<ol>
<li>✅ Cursorを再起動したか？</li>
</ol>
<ul>
<li>MCP設定を読み込むには再起動が必要です</li>
</ul>
<ol start="2">
<li>✅ <code>.cursor/mcp.json</code> が正しく設定されているか？</li>
</ol>
<ul>
<li>ファイルの存在とパスを確認</li>
</ul>
<ol start="3">
<li>✅ <code>bun</code> コマンドがシステムPATHに含まれているか？</li>
</ol>
<pre class=" language-powershell"><code class="prism  language-powershell">
bun <span class="token operator">--</span>version

</code></pre>
<ol start="4">
<li>✅ ビルドが正常に完了しているか？</li>
</ol>
<pre class=" language-powershell"><code class="prism  language-powershell">
<span class="token function">ls</span> C:\Cursorprojects\cursor<span class="token operator">-</span>talk<span class="token operator">-</span>to<span class="token operator">-</span>figma<span class="token operator">-</span>mcp\dist

</code></pre>
<hr>
<h3 id="bun-setupが失敗する場合">bun setupが失敗する場合</h3>
<p><strong>解決方法</strong>: 手動で各ステップを実行</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
<span class="token comment"># 依存関係のインストール</span>

bun install

  

<span class="token comment"># ビルド</span>

bun run build

  

<span class="token comment"># MCP設定は手動で作成（ステップ6参照）</span>

</code></pre>
<hr>
<h3 id="gitクローンが失敗する場合">Gitクローンが失敗する場合</h3>
<p><strong>エラー</strong>: 「Permission denied (publickey)」</p>
<p><strong>原因</strong>: SSH認証が設定されていない</p>
<p><strong>解決方法</strong>: HTTPSでクローン</p>
<pre class=" language-powershell"><code class="prism  language-powershell">
git clone https:<span class="token operator">/</span><span class="token operator">/</span>github<span class="token punctuation">.</span>com<span class="token operator">/</span>grab<span class="token operator">/</span>cursor<span class="token operator">-</span>talk<span class="token operator">-</span>to<span class="token operator">-</span>figma<span class="token operator">-</span>mcp<span class="token punctuation">.</span>git

</code></pre>
<hr>
<h2 id="参考リンク">参考リンク</h2>
<ul>
<li>
<p><strong>公式GitHub</strong>: <a href="https://github.com/grab/cursor-talk-to-figma-mcp">https://github.com/grab/cursor-talk-to-figma-mcp</a></p>
</li>
<li>
<p><strong>Figmaプラグイン</strong>: <a href="https://www.figma.com/community/plugin/1485687494525374295">https://www.figma.com/community/plugin/1485687494525374295</a></p>
</li>
<li>
<p><strong>Zenn記事（日本語解説）</strong>: <a href="https://zenn.dev/makumaaku/articles/4531ddbb67edd5">https://zenn.dev/makumaaku/articles/4531ddbb67edd5</a></p>
</li>
<li>
<p><strong>デモ動画</strong>: <a href="https://www.youtube.com/watch?v=j05gGT3xfCs">https://www.youtube.com/watch?v=j05gGT3xfCs</a></p>
</li>
<li>
<p><strong>Bun公式サイト</strong>: <a href="https://bun.sh/">https://bun.sh/</a></p>
</li>
<li>
<p><strong>Git for Windows</strong>: <a href="https://git-scm.com/download/win">https://git-scm.com/download/win</a></p>
</li>
</ul>
<hr>
<h2 id="次のステップ">次のステップ</h2>
<p>セットアップが完了したら：</p>
<ol>
<li>
<p><strong>簡単な操作から試す</strong>: 「赤い円を作成して」など</p>
</li>
<li>
<p><strong>複雑な操作にチャレンジ</strong>: レイヤーの一括変更など</p>
</li>
<li>
<p><strong>ワークフローに組み込む</strong>: デザインの自動化タスクに活用</p>
</li>
</ol>
<hr>
<h2 id="まとめ">まとめ</h2>
<ul>
<li>
<p>✅ Bun インストール</p>
</li>
<li>
<p>✅ Git インストール</p>
</li>
<li>
<p>✅ プロジェクトクローン</p>
</li>
<li>
<p>✅ 依存関係インストール</p>
</li>
<li>
<p>✅ ビルド</p>
</li>
<li>
<p>✅ Cursor MCP設定</p>
</li>
</ul>
<p>これでCursorから自然言語でFigmaを操作できるようになります。</p>
<p>何か問題が発生した場合は、<a href="#%E3%83%88%E3%83%A9%E3%83%96%E3%83%AB%E3%82%B7%E3%83%A5%E3%83%BC%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0">トラブルシューティング</a> セクションを参照するか、公式GitHubのIssuesページで質問してください。</p>
<p>Happy Designing! 🎨</p>
