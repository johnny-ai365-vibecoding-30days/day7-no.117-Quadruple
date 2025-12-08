---
layout: single
title: "認識 MCP：模型上下文協議的運作方式"
date: 2025-02-09
categories: [MCP, 標準]
tags: [協議, 上下文, 介接]
author_profile: true
excerpt: "介紹 MCP 的設計動機、角色分工與核心流程，理解它如何標準化 Function Calling。"
---

MCP（Model Context Protocol）是一套為 LLM 與外部工具互動設計的應用層協議，目標是像 HTTP 或 USB-C 一樣提供統一格式，讓不同模型與工具可以互通並共用同一份合約。【F:resource/MCP.md†L5-L23】它定義了工具清單查詢、函式呼叫與結果回傳的 JSON 結構，降低跨廠商整合成本。【F:resource/MCP.md†L5-L23】

協議將參與者分為 HOST、CLIENT、SERVER：HOST 管理多條通道並負責路由，CLIENT 代表模型端負責列出工具、發起呼叫並處理結果，SERVER 則公開工具清單、驗證參數並執行業務邏輯。【F:resource/MCP.md†L25-L44】清晰的角色分工，確保每個節點都知道要遵循的介面與責任。

在近期發展中，MCP v1.1 新增更細緻的錯誤代碼、優化串流回傳並擴充工具 metadata，強化安全性與可管理性。【F:resource/MCP.md†L46-L70】隨著更多 LLM 廠商與生態平台宣告支援，MCP 正朝向成為 Function Calling 的事實標準，讓模型可以帶著上下文安全地跨服務協作。【F:resource/MCP.md†L46-L86】
