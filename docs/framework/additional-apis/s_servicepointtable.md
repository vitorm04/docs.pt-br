---
title: Campo ServicePointManager. s_ServicePointTable
description: Leia sobre o campo ServicePointManager. s_ServicePointTable no .NET. Este campo de tabela de hash contém conexões HTTP ativas (pontos de bits) no AppDomain.
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
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989541"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="a1952-104">Campo ServicePointManager. s do \_ Objectpointtable</span><span class="sxs-lookup"><span data-stu-id="a1952-104">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="a1952-105">`ServicePointManager.s_ServicePointTable`é um <xref:System.Collections.Hashtable> que contém a lista de conexões http ativas <xref:System.Net.ServicePoint> no <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="a1952-105">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1952-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1952-106">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="a1952-107">O `ServicePointManager.s_ServicePointTable` campo é privado e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="a1952-107">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a1952-108">A Microsoft não oferece suporte ao uso deste campo em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="a1952-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1952-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1952-109">Requirements</span></span>

<span data-ttu-id="a1952-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a1952-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a1952-111">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="a1952-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="a1952-112">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="a1952-112">**.NET Framework versions:** Available since 2.0.</span></span>
