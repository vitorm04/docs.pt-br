---
title: Propriedade SqlStreamChars.CanSeek (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8d7bd7fb90177932b413c379f618a6d36374de57
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223137"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="03e80-102">Propriedade SqlStreamChars.CanSeek</span><span class="sxs-lookup"><span data-stu-id="03e80-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="03e80-103">Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo atual dá suporte à operação de busca.</span><span class="sxs-lookup"><span data-stu-id="03e80-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="03e80-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="03e80-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="03e80-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03e80-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="03e80-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="03e80-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="03e80-107">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="03e80-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="03e80-108">`true` Se o fluxo atual dá suporte à operação de busca; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="03e80-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="03e80-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="03e80-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="03e80-110">O `SqlStreamChars.CanSeek` propriedade é privada e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="03e80-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="03e80-111">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="03e80-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="03e80-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03e80-112">Requirements</span></span>

<span data-ttu-id="03e80-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="03e80-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="03e80-114">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="03e80-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="03e80-115">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="03e80-115">**.NET Framework versions:** Available since 2.0.</span></span>