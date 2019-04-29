---
title: Propriedade SqlStreamChars.Length (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c2ef66fa493512e1fa062e22858ea251ced39453
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705838"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="280bf-102">Propriedade SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="280bf-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="280bf-103">Quando substituído em uma classe derivada, obtém o comprimento do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="280bf-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="280bf-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="280bf-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="280bf-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="280bf-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="280bf-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="280bf-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="280bf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="280bf-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="280bf-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="280bf-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="280bf-109">O comprimento do fluxo.</span><span class="sxs-lookup"><span data-stu-id="280bf-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="280bf-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="280bf-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="280bf-111">O `SqlStreamChars.Length` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="280bf-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="280bf-112">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="280bf-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="280bf-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="280bf-113">Requirements</span></span>

<span data-ttu-id="280bf-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="280bf-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="280bf-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="280bf-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="280bf-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="280bf-116">**.NET Framework versions:** Available since 2.0.</span></span>