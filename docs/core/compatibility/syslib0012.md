---
title: Aviso de SYSLIB0012
description: Saiba mais sobre o obsoletions que gera SYSLIB0012 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2ed93b6eefbaa861faca319f0cc9bf19ac741f3b
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333199"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="1bd01-103">SYSLIB0012: assembly. CodeBase e assembly. EscapedCodeBase são obsoletos</span><span class="sxs-lookup"><span data-stu-id="1bd01-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="1bd01-104">As seguintes APIs são marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="1bd01-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="1bd01-105">Usá-los no código gera aviso `SYSLIB0012` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="1bd01-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

<span data-ttu-id="1bd01-106">Solução alternativa</span><span class="sxs-lookup"><span data-stu-id="1bd01-106">Workaround</span></span>

<span data-ttu-id="1bd01-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="1bd01-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>
