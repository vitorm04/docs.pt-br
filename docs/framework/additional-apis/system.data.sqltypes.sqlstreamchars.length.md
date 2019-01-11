---
title: Propriedade SqlStreamChars.Length (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ac6e6af9c9411ebc25039e0992133fae2b35ee23
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221175"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="9a84a-102">Propriedade SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="9a84a-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="9a84a-103">Quando substituído em uma classe derivada, obtém o comprimento do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="9a84a-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="9a84a-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="9a84a-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="9a84a-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9a84a-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="9a84a-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9a84a-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a84a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a84a-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="9a84a-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="9a84a-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="9a84a-109">O comprimento do fluxo.</span><span class="sxs-lookup"><span data-stu-id="9a84a-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a84a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a84a-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="9a84a-111">O `SqlStreamChars.Length` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="9a84a-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9a84a-112">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="9a84a-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a84a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a84a-113">Requirements</span></span>

<span data-ttu-id="9a84a-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="9a84a-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="9a84a-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="9a84a-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="9a84a-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="9a84a-116">**.NET Framework versions:** Available since 2.0.</span></span>