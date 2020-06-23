---
title: Método webcabeçalhocollection. addinterna (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990292"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="6a68b-102">Método webcabeçalhocollection. addinterna</span><span class="sxs-lookup"><span data-stu-id="6a68b-102">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="6a68b-103">Adiciona um novo cabeçalho com o nome e o valor especificados à coleção, ignorando as verificações.</span><span class="sxs-lookup"><span data-stu-id="6a68b-103">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="6a68b-104">Esse método é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="6a68b-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6a68b-105">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="6a68b-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="6a68b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a68b-106">Parameters</span></span>

- <span data-ttu-id="6a68b-107">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6a68b-107">`name` <xref:System.String></span></span>

  <span data-ttu-id="6a68b-108">O nome do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="6a68b-108">The name of the header.</span></span>

- <span data-ttu-id="6a68b-109">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="6a68b-109">`value` <xref:System.String></span></span>

  <span data-ttu-id="6a68b-110">O valor do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="6a68b-110">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a68b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a68b-111">Requirements</span></span>

<span data-ttu-id="6a68b-112">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6a68b-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6a68b-113">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="6a68b-113">**Assembly:** System (in System.dll)</span></span>
