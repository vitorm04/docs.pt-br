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
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634330"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="acee7-102">Propriedade SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="acee7-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="acee7-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`.</span><span class="sxs-lookup"><span data-stu-id="acee7-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="acee7-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="acee7-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="acee7-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="acee7-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="acee7-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acee7-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="acee7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acee7-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="acee7-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="acee7-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="acee7-109">`true` Se o fluxo estiver `null`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="acee7-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="acee7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="acee7-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="acee7-111">O `SqlStreamChars.IsNull` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="acee7-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="acee7-112">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="acee7-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="acee7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="acee7-113">Requirements</span></span>

<span data-ttu-id="acee7-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="acee7-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="acee7-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="acee7-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="acee7-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="acee7-116">**.NET Framework versions:** Available since 2.0.</span></span>