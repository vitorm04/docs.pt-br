---
title: Propriedade SqlStreamChars.IsNull (SqlTypes)
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
ms.openlocfilehash: ec00b0afa1597c3ae6488c12fe5a0667dad70e2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675215"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="b5f1b-102">Propriedade SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="b5f1b-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="b5f1b-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="b5f1b-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="b5f1b-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="b5f1b-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5f1b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5f1b-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="b5f1b-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="b5f1b-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="b5f1b-109">`true` Se o fluxo estiver `null`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5f1b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5f1b-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b5f1b-111">O `SqlStreamChars.IsNull` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b5f1b-112">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5f1b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5f1b-113">Requirements</span></span>

<span data-ttu-id="b5f1b-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="b5f1b-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="b5f1b-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="b5f1b-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="b5f1b-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="b5f1b-116">**.NET Framework versions:** Available since 2.0.</span></span>