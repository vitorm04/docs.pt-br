---
title: Propriedade SqlStreamChars. Length (System. Data. SqlTypes)
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
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395603"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="dcf9a-102">Propriedade SqlStreamChars. Length</span><span class="sxs-lookup"><span data-stu-id="dcf9a-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="dcf9a-103">Quando substituído em uma classe derivada, obtém o comprimento do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="dcf9a-104">O assembly que contém essa propriedade tem uma relação Friend com SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="dcf9a-105">Ele é destinado ao uso por SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="dcf9a-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="dcf9a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcf9a-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="dcf9a-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="dcf9a-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="dcf9a-109">O comprimento do fluxo.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="dcf9a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="dcf9a-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="dcf9a-111">A propriedade `SqlStreamChars.Length` é privada e não se destina a ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="dcf9a-112">A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcf9a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dcf9a-113">Requirements</span></span>

<span data-ttu-id="dcf9a-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="dcf9a-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="dcf9a-115">**Assembly:** System. Data (em System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="dcf9a-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="dcf9a-116">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="dcf9a-116">**.NET Framework versions:** Available since 2.0.</span></span>
