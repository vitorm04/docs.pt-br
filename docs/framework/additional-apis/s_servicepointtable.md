---
title: Campo ServicePointManager. s_ServicePointTable
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68445f4a290b9f4fe2696e35cda391b6c0ee8f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119998"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="c5596-102">ServicePointManager. s\_campo do objectpointtable</span><span class="sxs-lookup"><span data-stu-id="c5596-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="c5596-103">`ServicePointManager.s_ServicePointTable` é uma <xref:System.Collections.Hashtable> que contém a lista de conexões HTTP ativas (<xref:System.Net.ServicePoint>s) no <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c5596-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5596-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5596-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="c5596-105">O campo `ServicePointManager.s_ServicePointTable` é privado e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="c5596-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="c5596-106">A Microsoft não oferece suporte ao uso deste campo em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="c5596-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5596-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5596-107">Requirements</span></span>

<span data-ttu-id="c5596-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="c5596-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="c5596-109">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="c5596-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="c5596-110">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="c5596-110">**.NET Framework versions:** Available since 2.0.</span></span>
