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
ms.openlocfilehash: 03b702b0ffe258eb8cad0a1ece5314b363f9a0d0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634624"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="2d1f6-102">Propriedade SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="2d1f6-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="2d1f6-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="2d1f6-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="2d1f6-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="2d1f6-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d1f6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d1f6-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="2d1f6-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="2d1f6-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="2d1f6-109">`true` Se o fluxo estiver `null`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d1f6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d1f6-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="2d1f6-111">O `SqlStreamChars.IsNull` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2d1f6-112">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d1f6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d1f6-113">Requirements</span></span>

<span data-ttu-id="2d1f6-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="2d1f6-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="2d1f6-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="2d1f6-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="2d1f6-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="2d1f6-116">**.NET Framework versions:** Available since 2.0.</span></span>
