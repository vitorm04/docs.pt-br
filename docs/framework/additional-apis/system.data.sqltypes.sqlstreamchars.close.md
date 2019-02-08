---
title: Método SqlStreamChars.Close (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 634b2262ce3262b2c5971fb995b7c988f50924ed
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826883"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="28e9c-102">Método SqlStreamChars.Close</span><span class="sxs-lookup"><span data-stu-id="28e9c-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="28e9c-103">Fecha o fluxo atual e libera os recursos de sistema associados ao fluxo.</span><span class="sxs-lookup"><span data-stu-id="28e9c-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="28e9c-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="28e9c-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="28e9c-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="28e9c-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="28e9c-106"> Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="28e9c-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="28e9c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="28e9c-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="28e9c-108">O `SqlStreamChars.Close` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="28e9c-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="28e9c-109">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="28e9c-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="28e9c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28e9c-110">Requirements</span></span>

<span data-ttu-id="28e9c-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="28e9c-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="28e9c-112">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="28e9c-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="28e9c-113">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="28e9c-113">**.NET Framework versions:** Available since 2.0.</span></span>