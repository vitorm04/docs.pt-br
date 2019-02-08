---
title: Propriedade SmiOrderProperty.Item (SQLServer)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: cb2f6cb956f9571f9bd2ba7f86d79c5df6e72a15
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827728"
---
# <a name="smiorderpropertyitem-property"></a><span data-ttu-id="3ebab-102">Propriedade SmiOrderProperty.Item</span><span class="sxs-lookup"><span data-stu-id="3ebab-102">SmiOrderProperty.Item Property</span></span>

<span data-ttu-id="3ebab-103">Obtém a ordem das colunas para a entidade.</span><span class="sxs-lookup"><span data-stu-id="3ebab-103">Gets the column order for the entity.</span></span> <span data-ttu-id="3ebab-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="3ebab-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="3ebab-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3ebab-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="3ebab-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3ebab-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ebab-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ebab-107">Syntax</span></span>

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a><span data-ttu-id="3ebab-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="3ebab-108">Property value</span></span>

<span data-ttu-id="3ebab-109">A ordem das colunas.</span><span class="sxs-lookup"><span data-stu-id="3ebab-109">The column order.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ebab-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ebab-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="3ebab-111">O `SmiOrderProperty.Item` propriedade é interna e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="3ebab-111">The `SmiOrderProperty.Item` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="3ebab-112">Microsoft não suporta o uso dessa propriedade em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="3ebab-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ebab-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ebab-113">Requirements</span></span>

<span data-ttu-id="3ebab-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span><span class="sxs-lookup"><span data-stu-id="3ebab-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span></span>

<span data-ttu-id="3ebab-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="3ebab-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="3ebab-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ebab-116">**.NET Framework versions:** Available since 2.0.</span></span>