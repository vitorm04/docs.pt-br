---
title: campo httpWebRequest._CoreResponse
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
ms.openlocfilehash: b275f3eece96ac8a9ae3fb0ebd030c8d79e21fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155915"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="2d814-102">HttpWebRequest. \_Campo CoreResponse</span><span class="sxs-lookup"><span data-stu-id="2d814-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="2d814-103">`HttpWebRequest._CoreResponse`é um objeto (um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception>) contendo o resultado da análise de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="2d814-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d814-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d814-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="2d814-105">Esta API não deve ser usada diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="2d814-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="2d814-106">Em vez disso, <xref:System.Diagnostics.DiagnosticSource> você deve usar um código de rede para conectar.</span><span class="sxs-lookup"><span data-stu-id="2d814-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="2d814-107">Consulte [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="2d814-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="2d814-108">A Microsoft não suporta o uso desta classe em um aplicativo de produção nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="2d814-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d814-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d814-109">Requirements</span></span>

<span data-ttu-id="2d814-110">**Espaço de nome:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="2d814-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="2d814-111">**Montagem:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="2d814-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="2d814-112">**Versões do Framework .NET:** Disponível desde 2.0.</span><span class="sxs-lookup"><span data-stu-id="2d814-112">**.NET Framework versions:** Available since 2.0.</span></span>
