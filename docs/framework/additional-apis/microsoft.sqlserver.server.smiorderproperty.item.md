---
title: Propriedade SmiOrderProperty.Item (SQLServer)
author: douglaslMS
ms.author: douglasl
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
ms.openlocfilehash: 5453167e16e2658b3546b7114201b04d481a0c79
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222995"
---
# <a name="smiorderpropertyitem-property"></a><span data-ttu-id="98737-102">Propriedade SmiOrderProperty.Item</span><span class="sxs-lookup"><span data-stu-id="98737-102">SmiOrderProperty.Item Property</span></span>

<span data-ttu-id="98737-103">Obtém a ordem das colunas para a entidade.</span><span class="sxs-lookup"><span data-stu-id="98737-103">Gets the column order for the entity.</span></span> <span data-ttu-id="98737-104">O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="98737-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="98737-105">Ele é destinado a uso pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="98737-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="98737-106">Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="98737-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="98737-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98737-107">Syntax</span></span>

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a><span data-ttu-id="98737-108">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="98737-108">Property value</span></span>

<span data-ttu-id="98737-109">A ordem das colunas.</span><span class="sxs-lookup"><span data-stu-id="98737-109">The column order.</span></span>

## <a name="remarks"></a><span data-ttu-id="98737-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="98737-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="98737-111">O `SmiOrderProperty.Item` propriedade é interna e não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="98737-111">The `SmiOrderProperty.Item` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="98737-112">Microsoft não suporta o uso dessa propriedade em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="98737-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="98737-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98737-113">Requirements</span></span>

<span data-ttu-id="98737-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span><span class="sxs-lookup"><span data-stu-id="98737-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span></span>

<span data-ttu-id="98737-115">**Assembly:** System. Data (em dll)</span><span class="sxs-lookup"><span data-stu-id="98737-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="98737-116">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="98737-116">**.NET Framework versions:** Available since 2.0.</span></span>