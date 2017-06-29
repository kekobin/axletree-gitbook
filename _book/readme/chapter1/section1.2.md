# 目录结构

axletree project会构建出client和server目录，其中，client是前端工程目录，包含整个前端的基础框架和样例文件，server是node层基于express的项目目录。

## client目录

    ├─<span class="hljs-keyword">client</span>                 <span class="hljs-preprocessor"># 前端代码  </span>
    │  ├─page                <span class="hljs-preprocessor"># 前端页面  </span>
    │  ├─<span class="hljs-keyword">static</span>              <span class="hljs-preprocessor"># 前端非模块化静态资源  </span>
    │  │  ├─css  
    │  │  └─js  
    │  └─widget              <span class="hljs-preprocessor"># 前端组件  </span>
    ├─fis-conf.js            <span class="hljs-preprocessor"># FIS编译配置</span>
    