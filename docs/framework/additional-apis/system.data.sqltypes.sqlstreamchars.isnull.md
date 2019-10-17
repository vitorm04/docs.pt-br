---
title: Propriedade SqlStreamChars. IsNull (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395742"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="6010c-102">Propriedade SqlStreamChars. IsNull</span><span class="sxs-lookup"><span data-stu-id="6010c-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="6010c-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`.</span><span class="sxs-lookup"><span data-stu-id="6010c-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="6010c-104">O assembly que contém essa propriedade tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="6010c-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="6010c-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6010c-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="6010c-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="6010c-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="6010c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6010c-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="6010c-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="6010c-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="6010c-109">`true` se o fluxo for `null`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6010c-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6010c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6010c-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6010c-111">A propriedade `SqlStreamChars.IsNull` é privada e não se destina a ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="6010c-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6010c-112">A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="6010c-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6010c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6010c-113">Requirements</span></span>

<span data-ttu-id="6010c-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="6010c-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="6010c-115">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="6010c-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="6010c-116">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="6010c-116">**.NET Framework versions:** Available since 2.0.</span></span>
