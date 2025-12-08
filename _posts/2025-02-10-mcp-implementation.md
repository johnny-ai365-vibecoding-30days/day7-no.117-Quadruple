---
layout: single
title: "實作 MCP：服務註冊、能力宣告與測試"
date: 2025-02-10
categories: [MCP, 實作]
tags: [服務註冊, 契約測試, 安全]
author_profile: true
excerpt: "以 MCP 角色模型為指引，規劃工具清單、錯誤處理與觀測，確保協議相容。"
---

要落地 MCP，首先要釐清 HOST、CLIENT、SERVER 的責任：SERVER 需公開工具清單並驗證輸入，CLIENT 代表模型發起 `listTools()` 與 `invoke()`，HOST 則協調多條通道與事件路由，確保所有呼叫都能被監控。【F:resource/MCP.md†L25-L44】

接著，根據 v1.1 的更新規則為每個工具補充 metadata（版本、限制、授權），並在錯誤回報中使用統一的 error code 與串流回傳標記，方便除錯與性能優化。【F:resource/MCP.md†L46-L70】這些結構化的宣告，就像 Function Calling 的 JSON Schema，能讓模型與工具在更新後仍保持相容。

最後，部署時應準備觀測面板：監看通道狀態、請求與錯誤分佈，並檢查不同廠商模型的輸出是否符合 MCP 格式。若發現 Server 的容錯行為或重試策略與規範不一致，就需調整實作或補充測試案例，維持生態的互通性。【F:resource/MCP.md†L25-L44】【F:resource/MCP.md†L46-L86】
