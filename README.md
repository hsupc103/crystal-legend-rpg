# CRYSTAL LEGEND WORKS

兩款用 HTML5 Canvas 從零手寫的原創遊戲 —— 沒有遊戲引擎、沒有外部素材、沒有建置步驟。
每個遊戲都是一個自足的 HTML 檔，用瀏覽器打開就能玩。

| | 遊戲 | 檔案 |
|---|---|---|
| 🔮 | **水晶傳說 Crystal Legend** — 致敬《FF4》的幻想 RPG | `rpg.html` |
| 🚀 | **OMEGA STRIKE 終焉突擊** — 縱向捲軸射擊 | `shooter.html` |
| 🏠 | 入口頁 | `index.html` |

---

## 水晶傳說 Crystal Legend

ATB 戰鬥、召喚獸與魔法特效、城鎮與世界地圖、路行鳥坐騎與飛空艇（可飛越山海抵達隱藏之地）。

**操作**：`方向鍵` 移動　`Enter / Z` 確定　`X` 選單　`R / F` 坐騎切換

## OMEGA STRIKE 終焉突擊

三個關卡、三尊多階段大魔王（外加三尊中王）的縱向捲軸射擊。

- **擦彈 GRAZE** — 判定點僅 3px，貼著彈幕飛才能充滿能量
- **零時領域** — 子彈時間（`timeScale 0.35`），消耗 BURST 能量
- **BURST 超必殺** — 全屏能量波清彈、敵彈轉為分數寶石
- **三系武器 ×5 級 + 最多 4 台僚機**，集中模式會切換成平行陣型
- **魔王部位破壞** — 盾板／砲塔／體節各有獨立血條，打掉就少一組招式
- CHAIN COMBO ×32、S~D 評價、CONTINUE、最高分保存於 localStorage

| 關卡 | 大魔王 | 階段 |
|---|---|---|
| 軌道殘骸帶 | 刃盾 AEGIS-01 | 護盾板 → 雷射鑽頭 → 核心暴走 |
| 熔核地表 | 爐心巨蟲 IGNIS WYRM | 12 節體節 → 潛入熔岩 → 爐心崩解 |
| 零號軌道要塞 | 終焉機神 OMEGA-XIII | 武裝 → 浮游砲分離 → 重力核心 → 奇點（4 階段）|

**操作**：`方向鍵 / WASD` 移動　`Z / 空白` 射擊　`Shift` 零時領域＋集中　`X` BURST
　　　　`Q / E` 或 `1 2 3` 切換武器　`P` 暫停　`M` 靜音（也支援滑鼠拖曳與觸控）

**除錯用 URL 參數**：`?stage=2`（指定關卡）`?boss=3`（直接打魔王）`?phase=4`（指定魔王階段）
`?dmg=4`（火力倍率）`?debug=1`（顯示 FPS 與實體數）`?auto=1`（自動迴避 AI）

---

## 本機執行

```bash
python -m http.server 8765
# 開 http://localhost:8765/
```

也可以直接用瀏覽器打開 `index.html`（純靜態，不需要伺服器；只有 OG 預覽圖需要 http）。

## 部署

純靜態網站，**沒有建置步驟**。

### GitHub Pages（已自動化）

`.github/workflows/pages.yml` 會在推上 `main` 時自動把 repo 根目錄發佈到 GitHub Pages
（`actions/configure-pages` 帶 `enablement: true`，Pages 尚未啟用時會自動建站）。
推上去之後到 repo 的 **Actions** 分頁就能看到部署結果與網址。

### Vercel

`vercel.json` 已備好（`cleanUrls` + 快取標頭），連結 repo 即可：

1. 到 [vercel.com](https://vercel.com) 用 GitHub 帳號登入 → **Add New… → Project**
2. Import `hsupc103/crystal-legend-rpg`
3. Framework Preset 選 **Other**，**Build Command 與 Output Directory 全部留空**
4. **Deploy**

之後每次推上 `main` 都會自動重新部署，其他分支會拿到 preview 網址。
`cleanUrls` 讓 `/rpg`、`/shooter` 這種不帶副檔名的網址也能用。
