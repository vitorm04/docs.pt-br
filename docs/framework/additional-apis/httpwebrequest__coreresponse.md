---
title: Campo HttpWebRequest. _CoreResponse
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
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740451"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="fbe97-102">HttpWebRequest.\_campo CoreResponse</span><span class="sxs-lookup"><span data-stu-id="fbe97-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="fbe97-103">`HttpWebRequest._CoreResponse` é um objeto (um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception>) que contém o resultado da análise de resposta http.</span><span class="sxs-lookup"><span data-stu-id="fbe97-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbe97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbe97-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="fbe97-105">Essa API não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="fbe97-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="fbe97-106">Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para conectar o código de rede.</span><span class="sxs-lookup"><span data-stu-id="fbe97-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="fbe97-107">Consulte o [Guia do usuário do diagnosticm](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="fbe97-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="fbe97-108">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="fbe97-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbe97-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="fbe97-109">Requirements</span></span>

<span data-ttu-id="fbe97-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="fbe97-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="fbe97-111">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="fbe97-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="fbe97-112">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="fbe97-112">**.NET Framework versions:** Available since 2.0.</span></span>
