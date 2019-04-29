---
title: CoreResponseData.m_ResponseHeaders Field
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
ms.openlocfilehash: ea93b70ae8e1a710b4208050d7ec823a28b218b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705968"
---
# <a name="coreresponsedatamresponseheaders-field"></a><span data-ttu-id="a8ef3-102">CoreResponseData.m\_ResponseHeaders campo</span><span class="sxs-lookup"><span data-stu-id="a8ef3-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="a8ef3-103">`CoreResponseData.m_ResponseHeaders` é um <xref:System.Net.WebHeaderCollection> de cabeçalhos associados a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="a8ef3-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8ef3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8ef3-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="a8ef3-105">Essa API não se destina a ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="a8ef3-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="a8ef3-106">Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para capturar o código de rede.</span><span class="sxs-lookup"><span data-stu-id="a8ef3-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="a8ef3-107">Ver [guia do usuário DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="a8ef3-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="a8ef3-108">Microsoft não suporta o uso dessa classe em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="a8ef3-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8ef3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8ef3-109">Requirements</span></span>

<span data-ttu-id="a8ef3-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a8ef3-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a8ef3-111">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="a8ef3-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="a8ef3-112">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="a8ef3-112">**.NET Framework versions:** Available since 2.0.</span></span>
