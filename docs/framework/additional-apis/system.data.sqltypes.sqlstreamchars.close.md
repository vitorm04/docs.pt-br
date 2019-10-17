---
title: Método SqlStreamChars. Close (System. Data. SqlTypes)
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
ms.openlocfilehash: c33c60842d181be7011528ca7550f3d09f291f43
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395631"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="93d79-102">Método SqlStreamChars. Close</span><span class="sxs-lookup"><span data-stu-id="93d79-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="93d79-103">Fecha o fluxo atual e libera todos os recursos do sistema associados ao fluxo.</span><span class="sxs-lookup"><span data-stu-id="93d79-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="93d79-104">O assembly que contém esse método tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="93d79-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="93d79-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="93d79-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="93d79-106"> Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="93d79-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="93d79-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="93d79-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="93d79-108">O método `SqlStreamChars.Close` é privado e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="93d79-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="93d79-109">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="93d79-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="93d79-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93d79-110">Requirements</span></span>

<span data-ttu-id="93d79-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="93d79-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="93d79-112">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="93d79-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="93d79-113">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="93d79-113">**.NET Framework versions:** Available since 2.0.</span></span>
