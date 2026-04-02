# Claude 台中小聚官網 — 全站設計系統 PRD

> 版本：v1.0 | 日期：2026-04-03 | 審計者：工程師 + 前端 + UX

---

## 一、問題總覽

| 嚴重度 | 問題數 | 說明 |
| ---- | ---- | ---- |
| P0 | 1 | SectionHeader component 一致性待驗證 |
| P1 | 8 | 品牌/視覺統一危機，需本週處理 |
| P2 | 16 | 細節優化，可下週處理 |

---

## 二、P1 修復清單（本週）

| 序 | 類別 | 問題 | 涉及頁面 | 解法 |
| ---- | ---- | ---- | ---- | ---- |
| P1-1 | Badge | 狀態 badge 顏色語意不明確 | 全站 | 統一狀態色盤（見下表） |
| P1-2 | 顏色 | Hero glow 背景任意選色 | index/about/community | 限制 glow 用 primary/12 + secondary/8 |
| P1-3 | Card | Border-radius 混亂 | 全站 | standard=rounded-lg, featured=rounded-2xl, avatar=rounded-full |
| P1-4 | Card | Shadow depth 無系統 | 全站 | base=shadow-sm, hover=shadow-md, featured=shadow-lg |
| P1-5 | Card | Hover 效果不一致 | index/events/resources | 統一：border-primary + shadow-primary/10 + optional:-translate-y-1 |
| P1-6 | 按鈕 | 按鈕變體語意混淆 | 全站 | CTA=primary, 次要=outline, 更次=ghost |
| P1-7 | Hero | Community hero 高度明顯更小 | community | 統一 min-h-[50vh] 以上 |
| P1-8 | Hero | H1 大小不統一 | community vs others | 統一 text-5xl md:text-6xl |

##### 狀態 Badge 色盤

| 狀態 | Class | 說明 |
| ---- | ---- | ---- |
| 即將登場 | `badge-primary badge-outline` | 主色，帶框 |
| 登記候補 | `badge-primary badge-outline` | 同上 |
| 已完售 | `badge-error badge-outline` | 紅，帶框 |
| 已結束 | `badge-neutral badge-outline` | 中性灰，帶框 |
| 籌備中 | `badge-neutral badge-outline` | 中性灰，帶框 |
| 規劃中 | `badge-ghost` | 無框，最淡 |

---

## 三、P2 優化清單（下週）

| 序 | 類別 | 問題 | 解法 |
| ---- | ---- | ---- | ---- |
| P2-1 | 顏色 | 背景色層級無系統 | 統一：overlay 用 primary/10 或 /12 |
| P2-2 | 顏色 | Timeline phase 色彩無語意 | 定義 phase 1-4 循環色 |
| P2-3 | 顏色 | Platform badge 無色 | YouTube=red/10, Podcast=purple/10 等 |
| P2-4 | Card | 卡片 bg 規則不明 | 交互=base-100, 背景區=base-200 |
| P2-5 | Card | Padding 混亂（p-4/5/6/7） | standard=p-5, featured=p-6, dense=p-4 |
| P2-6 | Badge | Size 不統一 | status=badge-xs, category=badge-sm |
| P2-7 | 間距 | Section py 混搭 | normal=py-16, feature=py-20, cta=py-24 |
| P2-8 | 間距 | Grid gap 無規則 | card=gap-5, dense=gap-4 |
| P2-9 | 間距 | Hero margin 不一致 | 所有 hero：px-6, max-w-3xl/4xl 統一 |
| P2-10 | 字體 | Overline 沒用語意 class | 建立 .overline 用 pixel font |
| P2-11 | 字體 | Card title 大小混亂 | 統一 text-base font-bold |
| P2-12 | Badge | Outline 應用不一致 | 狀態=outline, category=無 outline |
| P2-13 | RWD | Breakpoint 混亂 | 三層：mobile / md(768) / lg(1024) |
| P2-14 | Hero | About hero 無分隔線 | 補 border-t border-base-300 |
| P2-15 | 連結 | Hover 樣式混亂 | 統一：text-primary hover:underline |
| P2-16 | 空狀態 | 只有一頁有設計 | 複製 dashed border pattern |

---

## 四、設計規範（工程師實作基準）

##### 顏色系統

```css
/* 背景層級 */
--color-base-100: #FAF8F5;   /* 主內容區 */
--color-base-200: #F2EDE6;   /* 次要區塊 */
--color-base-300: #E6DDD3;   /* 邊框 */

/* Hero glow（固定組合，不自由發揮） */
bg-primary/12 + bg-secondary/8
```

##### 排版層級

| 層級 | Tailwind class | 字體 |
| ---- | ---- | ---- |
| H1 | text-5xl md:text-6xl font-black | serif |
| H2 | text-3xl font-black | serif |
| H3 | text-lg font-bold | serif |
| Overline | text-xs uppercase font-bold text-primary | pixel |
| Body | clamp（global.css） | sans |
| Card title | text-base font-bold | sans-rounded |

##### 間距系統

| 用途 | Class |
| ---- | ---- |
| Normal section | py-16 |
| Featured section | py-20 |
| CTA section | py-24 |
| Card（standard） | p-5 |
| Card（featured） | p-6 |
| Grid（normal） | gap-5 |
| Grid（dense） | gap-4 |

##### Card 規格

| 屬性 | Standard | Featured |
| ---- | ---- | ---- |
| Border-radius | rounded-lg | rounded-2xl |
| Border | border border-base-300 | border-2 border-primary |
| Shadow | shadow-sm | shadow-lg |
| Shadow hover | shadow-md | — |
| Hover border | hover:border-primary | — |
| Padding | p-5 | p-8 md:p-10 |

##### 按鈕規範

| 語意 | Class |
| ---- | ---- |
| 主要 CTA | btn btn-primary |
| 次要 | btn btn-outline |
| 更次要 | btn btn-ghost |

---

## 五、UX 驗收清單

- [x] 全站 badge 顏色：同狀態同色，截圖逐一對照（2026-04-03 完成）
- [ ] Card shadow：hover 深度一致（dev tool 量 box-shadow）
- [x] Hero 高度：index / about / community 統一 min-h-[50vh]（2026-04-03 完成）
- [x] H1 字號：三頁 text-5xl md:text-6xl 統一（2026-04-03 完成）
- [x] 按鈕：無例外使用 primary / outline / ghost 以外的變體（2026-04-03 驗證）
- [ ] Mobile(375) / Tablet(768) / Desktop(1440) 三視圖截圖驗收

---

## 六、實施路線圖

| Phase | 時間 | 工作項 |
| ---- | ---- | ---- |
| Phase 1 | 本週 | Badge 色盤 + Hero 統一 + Card shadow |
| Phase 2 | 下週 | Card padding/radius + Hover 統一 + 間距系統 |
| Phase 3 | 第 3 週 | Breakpoint 規範 + 字體系統 + 設計規範文件化 |
| Phase 4 | 第 4 週 | UX 驗收 + 截圖 QA + 遺漏修正 |
