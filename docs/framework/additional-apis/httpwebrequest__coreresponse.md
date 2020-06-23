---
title: Campo HttpWebRequest. _CoreResponse
description: Leia sobre o campo HttpWebRequest. _CoreResponse no .NET. Esse campo é um objeto CoreResponseData ou Exception que contém o resultado da análise de resposta HTTP.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989753"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="4e04c-104">HttpWebRequest. \_ Campo CoreResponse</span><span class="sxs-lookup"><span data-stu-id="4e04c-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="4e04c-105">`HttpWebRequest._CoreResponse`é um objeto (um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception> ) que contém o resultado da análise de resposta http.</span><span class="sxs-lookup"><span data-stu-id="4e04c-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e04c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e04c-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="4e04c-107">Essa API não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="4e04c-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="4e04c-108">Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para conectar o código de rede.</span><span class="sxs-lookup"><span data-stu-id="4e04c-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="4e04c-109">Consulte o [Guia do usuário do diagnosticm](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="4e04c-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="4e04c-110">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="4e04c-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4e04c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4e04c-111">Requirements</span></span>

<span data-ttu-id="4e04c-112">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="4e04c-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="4e04c-113">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="4e04c-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="4e04c-114">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="4e04c-114">**.NET Framework versions:** Available since 2.0.</span></span>
