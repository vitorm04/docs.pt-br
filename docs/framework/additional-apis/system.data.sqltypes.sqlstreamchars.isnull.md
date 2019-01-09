---
title: Propriedade SqlStreamChars.IsNull (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 79ebb9ec54185a94cb95dfd0fb2929e61cf513ef
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152619"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="63825-102">Propriedade SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="63825-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="63825-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`.</span><span class="sxs-lookup"><span data-stu-id="63825-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="63825-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="63825-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="63825-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="63825-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="63825-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="63825-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="63825-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63825-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="63825-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="63825-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="63825-109">`true` Se o fluxo estiver `null`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="63825-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="63825-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="63825-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="63825-111">O `SqlStreamChars.IsNull` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="63825-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="63825-112">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="63825-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="63825-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63825-113">Requirements</span></span>

<span data-ttu-id="63825-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="63825-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="63825-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="63825-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="63825-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="63825-116">**.NET Framework versions:** Available since 2.0.</span></span>