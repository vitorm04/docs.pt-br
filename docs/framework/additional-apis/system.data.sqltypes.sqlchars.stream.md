---
title: Propriedade SqlChars.Stream (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d756b78a7cdbc12562e474ca3d2c9a1f3529f6bf
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223046"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="d1e12-102">Propriedade SqlChars.Stream</span><span class="sxs-lookup"><span data-stu-id="d1e12-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="d1e12-103">Obtém ou define o fluxo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1e12-103">Gets or sets the character stream.</span></span> <span data-ttu-id="d1e12-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="d1e12-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d1e12-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1e12-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d1e12-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d1e12-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="d1e12-107">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="d1e12-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="d1e12-108">O fluxo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1e12-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1e12-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1e12-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d1e12-110">O `SqlChars.Stream` propriedade é interna e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="d1e12-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d1e12-111">Microsoft não suporta o uso dessa propriedade em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="d1e12-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1e12-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1e12-112">Requirements</span></span>

<span data-ttu-id="d1e12-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d1e12-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d1e12-114">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="d1e12-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d1e12-115">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="d1e12-115">**.NET Framework versions:** Available since 2.0.</span></span>