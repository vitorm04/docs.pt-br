---
title: Classe CoreResponseData
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 640a925c3aec86b4743b1b2b62eb3793af1cc0bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675410"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="42f13-102">Classe CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="42f13-102">CoreResponseData Class</span></span>

<span data-ttu-id="42f13-103">O `CoreResponseData` classe representa a análise de cabeçalhos HTTP e o corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="42f13-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="42f13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42f13-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="42f13-105">Essa API é interno, e ele não deve ser usado diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="42f13-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="42f13-106">Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para capturar o código de rede.</span><span class="sxs-lookup"><span data-stu-id="42f13-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="42f13-107">Ver [guia do usuário DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="42f13-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="42f13-108">Microsoft não suporta o uso dessa classe em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="42f13-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="42f13-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42f13-109">Requirements</span></span>

<span data-ttu-id="42f13-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="42f13-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="42f13-111">**Assembly:** Sistema (em System. dll)</span><span class="sxs-lookup"><span data-stu-id="42f13-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="42f13-112">**Versões do .NET framework:** Disponível desde o 2.0.</span><span class="sxs-lookup"><span data-stu-id="42f13-112">**.NET Framework versions:** Available since 2.0.</span></span>
