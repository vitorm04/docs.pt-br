---
title: Campo CoreResponseData. m_StatusCode
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_StatusCode
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 8abe619a57cc61fc3502807f60deccbbd578f382
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740994"
---
# <a name="coreresponsedatam_statuscode-field"></a><span data-ttu-id="e453b-102">CoreResponseData. m\_campo StatusCode</span><span class="sxs-lookup"><span data-stu-id="e453b-102">CoreResponseData.m\_StatusCode Field</span></span>

<span data-ttu-id="e453b-103">`CoreResponseData.m_StatusCode` é um <xref:System.Net.HttpStatusCode> que contém o status da resposta.</span><span class="sxs-lookup"><span data-stu-id="e453b-103">`CoreResponseData.m_StatusCode` is an <xref:System.Net.HttpStatusCode> containing the status of the response.</span></span>

## <a name="syntax"></a><span data-ttu-id="e453b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e453b-104">Syntax</span></span>
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> <span data-ttu-id="e453b-105">Essa API não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="e453b-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="e453b-106">Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para conectar o código de rede.</span><span class="sxs-lookup"><span data-stu-id="e453b-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="e453b-107">Consulte o [Guia do usuário do diagnosticm](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="e453b-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="e453b-108">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="e453b-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e453b-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e453b-109">Requirements</span></span>

<span data-ttu-id="e453b-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e453b-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e453b-111">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="e453b-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e453b-112">**.NET Framework versões:** Disponível desde 2,0.</span><span class="sxs-lookup"><span data-stu-id="e453b-112">**.NET Framework versions:** Available since 2.0.</span></span>
