---
title: Método SqlStreamChars.Close (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d0c29bbc5c6bea98cf36e3c2b6bf7825d6843ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705864"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="34baf-102">Método SqlStreamChars.Close</span><span class="sxs-lookup"><span data-stu-id="34baf-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="34baf-103">Fecha o fluxo atual e libera os recursos de sistema associados ao fluxo.</span><span class="sxs-lookup"><span data-stu-id="34baf-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="34baf-104">O assembly que contém este método tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="34baf-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="34baf-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="34baf-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="34baf-106"> Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="34baf-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="34baf-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="34baf-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="34baf-108">O `SqlStreamChars.Close` método é privado e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="34baf-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="34baf-109">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="34baf-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="34baf-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34baf-110">Requirements</span></span>

<span data-ttu-id="34baf-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="34baf-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="34baf-112">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="34baf-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="34baf-113">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="34baf-113">**.NET Framework versions:** Available since 2.0.</span></span>