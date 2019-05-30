---
title: Campo Connection.m_WriteList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d138e0490e849ff26f540077ec7d23ae42737606
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300902"
---
# <a name="connectionmwritelist-field"></a><span data-ttu-id="bdd65-102">Connection.m\_WriteList campo</span><span class="sxs-lookup"><span data-stu-id="bdd65-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="bdd65-103">`Connection.m_WriteList` é um <xref:System.Collections.ArrayList> de <xref:System.Net.HttpWebRequest> objetos que são enfileirados para serem enviadas pelo HTTP.</span><span class="sxs-lookup"><span data-stu-id="bdd65-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="bdd65-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdd65-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="bdd65-105">O `Connection.m_WriteList` campo é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="bdd65-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="bdd65-106">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="bdd65-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bdd65-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdd65-107">Requirements</span></span>

<span data-ttu-id="bdd65-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="bdd65-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="bdd65-109">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="bdd65-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="bdd65-110">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="bdd65-110">**.NET Framework versions:** Available since 2.0.</span></span>
