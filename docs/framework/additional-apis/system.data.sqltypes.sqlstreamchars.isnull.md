---
title: Propriedade SqlStreamChars.IsNull (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7bef26119e31658b8495df402bbc07341cd84cf7
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222552"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="26110-102">Propriedade SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="26110-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="26110-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`.</span><span class="sxs-lookup"><span data-stu-id="26110-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="26110-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="26110-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="26110-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="26110-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="26110-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="26110-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="26110-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26110-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="26110-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="26110-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="26110-109">`true` Se o fluxo estiver `null`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="26110-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="26110-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="26110-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="26110-111">O `SqlStreamChars.IsNull` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="26110-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="26110-112">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="26110-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="26110-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26110-113">Requirements</span></span>

<span data-ttu-id="26110-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="26110-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="26110-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="26110-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="26110-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="26110-116">**.NET Framework versions:** Available since 2.0.</span></span>