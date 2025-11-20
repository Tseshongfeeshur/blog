---
title: 动态
---

<script data-swup-reload-script type="text/javascript">
    function buildItem(dateEnDash, content) {
        return `<li class="w-full flex flex-row relative"><div class="w-10 h-10 mr-4 rounded-lg overflow-hidden border border-border-color p-[1px] shrink-0"><img src="/images/favicon.jpg" class="w-full h-full rounded-[6.2px]"></div><div class="w-full border-border-color rounded-xl rounded-tl-none shadow-redefine-flat overflow-hidden"><div class="essay-date px-4 py-1.5 text-sm border-b border-border-color bg-zinc-50 dark:bg-zinc-800 text-third-text-color" data-date="${dateEnDash}T10:00:00+08:00"></div><div id="shuoshuo-content" class="px-4 py-2"><p>${content}</p></div></div><div class="absolute left-[50.5px] top-3 transform w-2 h-2 border-solid border-t border-l bg-zinc-50 -rotate-45 border-border-color dark:bg-zinc-800"></div></li>`;
    }

    function main() {
        const container = document.querySelector(".page-template-container");
        container.innerHTML += `<ul id="moments-list" class="flex flex-col mb-4 gap-6">`;

        content = "测试"
        dateEnDash = "2013-09-02"
        container.innerHTML += buildItem(dateEnDash, content);

        container.innerHTML += `</ul>`;
    }

    main();
</script>