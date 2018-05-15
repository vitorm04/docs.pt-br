---
title: Campo HttpWebRequest._CoreResponse
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
ms.openlocfilehash: 3627c9bf0d72ccec3a0d6d9c7c89b62f83dcd4b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="628d1-102">HttpWebRequest. \_CoreResponse campo</span><span class="sxs-lookup"><span data-stu-id="628d1-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="628d1-103">`HttpWebRequest._CoreResponse` é um objeto (ou um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception>) que contém o resultado da análise de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="628d1-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="628d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="628d1-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="628d1-105">Esta API não é destinada a ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="628d1-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="628d1-106">Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para capturar o código de rede.</span><span class="sxs-lookup"><span data-stu-id="628d1-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="628d1-107">Consulte [guia do usuário DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="628d1-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="628d1-108">Microsoft não suporta o uso dessa classe em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="628d1-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="628d1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="628d1-109">Requirements</span></span>

<span data-ttu-id="628d1-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="628d1-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="628d1-111">**Assembly:** sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="628d1-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="628d1-112">**Versões do .NET framework:** disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="628d1-112">**.NET Framework versions:** Available since 2.0.</span></span>
