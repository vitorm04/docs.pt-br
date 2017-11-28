---
title: Campo ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a><span data-ttu-id="0ac02-102">ServicePointManager.s\_ServicePointTable campo</span><span class="sxs-lookup"><span data-stu-id="0ac02-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="0ac02-103">`ServicePointManager.s_ServicePointTable`é um <xref:System.Collections.Hashtable> que contém a lista de conexões ativas de HTTP (<xref:System.Net.ServicePoint>s) na <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0ac02-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ac02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ac02-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="0ac02-105">O `ServicePointManager.s_ServicePointTable` campo é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="0ac02-105">The `ServicePointManager.s_ServicePointTable` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="0ac02-106">Microsoft não suporta o uso desse campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="0ac02-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ac02-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ac02-107">Requirements</span></span>

<span data-ttu-id="0ac02-108">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0ac02-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0ac02-109">**Assembly:** sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="0ac02-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="0ac02-110">**Versões do .NET framework:** disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="0ac02-110">**.NET Framework versions:** Available since 2.0.</span></span>
