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
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155801"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="5d2e3-102">Campo servicepointtable\_servicepointmanager.s</span><span class="sxs-lookup"><span data-stu-id="5d2e3-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="5d2e3-103">`ServicePointManager.s_ServicePointTable`é <xref:System.Collections.Hashtable> um que contém a lista<xref:System.Net.ServicePoint>de conexões <xref:System.AppDomain>HTTP ativas (s) no .</span><span class="sxs-lookup"><span data-stu-id="5d2e3-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d2e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d2e3-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="5d2e3-105">O `ServicePointManager.s_ServicePointTable` campo é privado e não deve ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="5d2e3-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5d2e3-106">A Microsoft não suporta o uso deste campo em um aplicativo de produção nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="5d2e3-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d2e3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d2e3-107">Requirements</span></span>

<span data-ttu-id="5d2e3-108">**Espaço de nome:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5d2e3-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5d2e3-109">**Montagem:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="5d2e3-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="5d2e3-110">**Versões do Framework .NET:** Disponível desde 2.0.</span><span class="sxs-lookup"><span data-stu-id="5d2e3-110">**.NET Framework versions:** Available since 2.0.</span></span>
