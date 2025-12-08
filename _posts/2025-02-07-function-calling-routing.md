---
layout: single
title: "選擇對的工具：函式調用中的路由策略"
date: 2025-02-07
categories: [函式調用, 策略]
tags: [工具選擇, 路由, 判斷邏輯]
author_profile: true
excerpt: "依據工具清單、輸入完整度與風險，讓 LLM 在 Function Calling 流程中做出正確選擇。"
---

在 Function Calling 流程裡，模型必須先理解使用者意圖，再對照工具清單決定是否需要調用。工具描述越完整（名稱、功能、參數型別與必填欄位），模型就越能產出正確的 JSON 請求，避免誤用或漏填參數。【F:resource/Function_Calling.md†L62-L111】

若輸入資訊不足，外部系統或提示設計應引導模型先詢問補充，而不是直接呼叫。這對需要精確條件的函式（如查詢特定月份業績）特別重要，因為正確的欄位值會決定調用是否成功。【F:resource/Function_Calling.md†L62-L111】【F:resource/Function_Calling.md†L113-L152】

完成調用後，結果會回傳給模型形成新的上下文，再進一步回應或安排後續步驟。透過反覆比對「預期輸出 vs. 實際結果」，可以微調工具排序與路由策略，讓每次選擇都更貼近需求與風險控管。【F:resource/Function_Calling.md†L7-L49】【F:resource/Function_Calling.md†L124-L174】
