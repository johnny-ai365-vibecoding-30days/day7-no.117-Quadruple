---
layout: single
title: "函式調用入門：結構化輸入與防呆設計"
date: 2025-02-06
categories: [函式調用, 工具]
tags: [Function Calling, 結構化輸出, 防錯]
author_profile: true
excerpt: "從 LLM 的角色與外部系統分工，整理 Function Calling 的基本流程與格式。"
---

Function Calling 的核心是讓 LLM 生成結構化的調用請求，再由外部系統負責執行。模型依據工具清單判斷是否需要呼叫函式，並產生 JSON 格式的請求；外部系統解析後執行，例如查詢資料庫或呼叫 API，最後把結果回傳給模型繼續回答。【F:resource/Function_Calling.md†L7-L49】【F:resource/Function_Calling.md†L62-L111】

要讓這流程順利，工具清單需透過 JSON Schema 詳述名稱、參數與必要欄位，並提供範例值；回傳結果也應以結構化格式呈現，包含成功與錯誤訊息，方便後續判斷是否重試。【F:resource/Function_Calling.md†L62-L111】【F:resource/Function_Calling.md†L155-L174】

由於不同模型的格式尚未完全標準化，開發者必須在外部系統側做輸出驗證、錯誤處理與上下文整合，確保每次呼叫都能安全回饋給模型。這種分工讓 LLM 專注於意圖理解與格式生成，工具執行者則掌握實際操作與防呆控制。【F:resource/Function_Calling.md†L7-L49】【F:resource/Function_Calling.md†L124-L174】
