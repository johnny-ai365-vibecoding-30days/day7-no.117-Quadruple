---
layout: single
title: "防呆護欄：避免函式調用走偏的三個技巧"
date: 2025-02-08
categories: [函式調用, 安全]
tags: [輸入驗證, 重試, 人工確認]
author_profile: true
excerpt: "結合輸入檢查、錯誤處理與上下文管理，讓 Function Calling 更穩健。"
---

第一道護欄是輸入驗證與參數描述。以 Function Calling 為例，每個工具都用 JSON Schema 說明欄位與限制，模型若輸出不符格式，外部系統就能攔截並回報錯誤，避免執行未知操作。【F:resource/Function_Calling.md†L62-L111】【F:resource/Function_Calling.md†L124-L174】

第二道護欄是錯誤處理與重試策略。因為不同模型的調用格式尚未完全統一，外部系統需要檢查 LLM 產生的 JSON 是否有效、在執行時捕捉暫時性失敗並決定是否重試或改用替代工具。【F:resource/Function_Calling.md†L7-L49】【F:resource/Function_Calling.md†L124-L174】

第三道護欄是上下文管理。每次調用結果都會返回模型，成為下一輪回應的依據；若沒有這層回饋，模型無法根據實際結果調整回答或停止錯誤行為。把結果、錯誤訊息與執行環境納入上下文，才能在多步驟任務中保持一致與安全。【F:resource/Function_Calling.md†L94-L174】
