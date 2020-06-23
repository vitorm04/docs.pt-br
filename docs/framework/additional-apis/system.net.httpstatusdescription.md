---
title: Classe HttpStatusDescription (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990303"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="13c86-102">Classe HttpStatusDescription</span><span class="sxs-lookup"><span data-stu-id="13c86-102">HttpStatusDescription class</span></span>

<span data-ttu-id="13c86-103">Fornece descrições de status HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="13c86-103">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="13c86-104">Esta classe não pode ser herdada.</span><span class="sxs-lookup"><span data-stu-id="13c86-104">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="13c86-105">Essa classe é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="13c86-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="13c86-106">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="13c86-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="13c86-107">método Get</span><span class="sxs-lookup"><span data-stu-id="13c86-107">Get method</span></span>

<span data-ttu-id="13c86-108">Retorna a descrição associada ao código de status HTTP especificado.</span><span class="sxs-lookup"><span data-stu-id="13c86-108">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="13c86-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13c86-109">Parameters</span></span>

<span data-ttu-id="13c86-110">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="13c86-110">`code` <xref:System.Int32></span></span>

<span data-ttu-id="13c86-111">O código de status HTTP, por exemplo, `404` .</span><span class="sxs-lookup"><span data-stu-id="13c86-111">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="13c86-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="13c86-112">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="13c86-113">A descrição do status HTTP.</span><span class="sxs-lookup"><span data-stu-id="13c86-113">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="13c86-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13c86-114">Requirements</span></span>

<span data-ttu-id="13c86-115">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="13c86-115">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="13c86-116">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="13c86-116">**Assembly:** System (in System.dll)</span></span>
