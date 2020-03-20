---
title: Campo CoreResponseData.m_ResponseHeaders
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 723df6dc2de978695608d106e3a01bde286fc4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156097"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="13e0a-102">Campo CoreResponseData.m\_ResponseHeaders</span><span class="sxs-lookup"><span data-stu-id="13e0a-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="13e0a-103">`CoreResponseData.m_ResponseHeaders`é <xref:System.Net.WebHeaderCollection> um dos cabeçalhos associados à resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="13e0a-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="13e0a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13e0a-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="13e0a-105">Esta API não deve ser usada diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="13e0a-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="13e0a-106">Em vez disso, <xref:System.Diagnostics.DiagnosticSource> você deve usar um código de rede para conectar.</span><span class="sxs-lookup"><span data-stu-id="13e0a-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="13e0a-107">Consulte [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="13e0a-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="13e0a-108">A Microsoft não suporta o uso desta classe em um aplicativo de produção nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="13e0a-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="13e0a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13e0a-109">Requirements</span></span>

<span data-ttu-id="13e0a-110">**Espaço de nome:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="13e0a-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="13e0a-111">**Montagem:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="13e0a-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="13e0a-112">**Versões do Framework .NET:** Disponível desde 2.0.</span><span class="sxs-lookup"><span data-stu-id="13e0a-112">**.NET Framework versions:** Available since 2.0.</span></span>
