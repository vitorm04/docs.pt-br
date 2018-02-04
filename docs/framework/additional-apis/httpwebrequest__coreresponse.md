---
title: HttpWebRequest._CoreResponse Field
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6493747cf6c894357223f011da026770778e26c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="9b6bd-102">HttpWebRequest. \_CoreResponse campo</span><span class="sxs-lookup"><span data-stu-id="9b6bd-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="9b6bd-103">`HttpWebRequest._CoreResponse`é um objeto (ou um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception>) que contém o resultado da análise de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="9b6bd-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b6bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b6bd-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="9b6bd-105">Esta API não é destinada a ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="9b6bd-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="9b6bd-106">Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para capturar o código de rede.</span><span class="sxs-lookup"><span data-stu-id="9b6bd-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="9b6bd-107">Consulte [guia do usuário DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="9b6bd-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="9b6bd-108">Microsoft não suporta o uso dessa classe em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="9b6bd-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b6bd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b6bd-109">Requirements</span></span>

<span data-ttu-id="9b6bd-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9b6bd-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9b6bd-111">**Assembly:** sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="9b6bd-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="9b6bd-112">**Versões do .NET framework:** disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="9b6bd-112">**.NET Framework versions:** Available since 2.0.</span></span>
