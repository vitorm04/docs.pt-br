---
title: Campo ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ebcf5c3f13b3bd30a8e091be09ae546eee1eaffe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147441"
---
# <a name="servicepointmanagersservicepointtable-field"></a><span data-ttu-id="7e947-102">ServicePointManager.s\_ServicePointTable campo</span><span class="sxs-lookup"><span data-stu-id="7e947-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="7e947-103">`ServicePointManager.s_ServicePointTable` é um <xref:System.Collections.Hashtable> que contém a lista de conexões ativas de HTTP (<xref:System.Net.ServicePoint>s) na <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="7e947-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e947-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e947-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="7e947-105">O `ServicePointManager.s_ServicePointTable` campo é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="7e947-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="7e947-106">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="7e947-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e947-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e947-107">Requirements</span></span>

<span data-ttu-id="7e947-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="7e947-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="7e947-109">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="7e947-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="7e947-110">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="7e947-110">**.NET Framework versions:** Available since 2.0.</span></span>
