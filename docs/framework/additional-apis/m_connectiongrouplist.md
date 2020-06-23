---
title: Campo de ponto de extremidade. m_ConnectionGroupList
description: Entenda o campo do ponto. m_ConnectionGroupList, uma tabela de hash de grupos de conexão que cada um tem uma conexão para o URI do ponto de extremidade no .NET.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989706"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="aa5cc-103">Campo ConnectionGroupList do ponto. m \_</span><span class="sxs-lookup"><span data-stu-id="aa5cc-103">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="aa5cc-104">`ServicePoint.m_ConnectionGroupList`é um <xref:System.Collections.Hashtable> dos grupos de conexão, cada um mantendo uma conexão para o <xref:System.Net.ServicePoint> URI do.</span><span class="sxs-lookup"><span data-stu-id="aa5cc-104">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa5cc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa5cc-105">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="aa5cc-106">O `ServicePoint.m_ConnectionGroupList` campo é privado e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="aa5cc-106">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="aa5cc-107">A Microsoft não oferece suporte ao uso deste campo em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="aa5cc-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa5cc-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa5cc-108">Requirements</span></span>

<span data-ttu-id="aa5cc-109">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="aa5cc-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="aa5cc-110">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="aa5cc-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="aa5cc-111">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="aa5cc-111">**.NET Framework versions:** Available since 2.0.</span></span>
