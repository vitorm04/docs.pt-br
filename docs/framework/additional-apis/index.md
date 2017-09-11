---
title: Bibliotecas de classes e APIs adicionais | Microsoft Docs
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: b53b8acc2a6c56db6a9d8a9b7c685a2d400a53e1
ms.openlocfilehash: 34815268b707aa70d174a1bbc04c32276db8412d
ms.contentlocale: pt-br
ms.lasthandoff: 05/02/2017

---

# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="6f044-102">Bibliotecas de classes e APIs adicionais</span><span class="sxs-lookup"><span data-stu-id="6f044-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="6f044-103">O .NET Framework está em constante evolução e, para melhorar o desenvolvimento multiplataforma e introduzir novas funcionalidades o quanto antes para nossos clientes, lançamos novos recursos OOB (fora de banda).</span><span class="sxs-lookup"><span data-stu-id="6f044-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="6f044-104">Este tópico lista os projetos OOB para os quais fornecemos documentação.</span><span class="sxs-lookup"><span data-stu-id="6f044-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="6f044-105">Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f044-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="6f044-106">Por exemplo, a classe <xref:System.Text.CodePagesEncodingProvider> disponibiliza as codificações de página de código para aplicativos UWP desenvolvidos usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f044-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="6f044-107">Este tópico também lista essas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="6f044-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="6f044-108">Projetos OOB</span><span class="sxs-lookup"><span data-stu-id="6f044-108">OOB projects</span></span>
  
| <span data-ttu-id="6f044-109">Projeto</span><span class="sxs-lookup"><span data-stu-id="6f044-109">Project</span></span> | <span data-ttu-id="6f044-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f044-110">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="6f044-111"><xref:System.Collections.Immutable></span><span class="sxs-lookup"><span data-stu-id="6f044-111"><xref:System.Collections.Immutable></span></span> | <span data-ttu-id="6f044-112">Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado.</span><span class="sxs-lookup"><span data-stu-id="6f044-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <span data-ttu-id="6f044-113"><xref:System.Net.Http.WinHttpHandler></span><span class="sxs-lookup"><span data-stu-id="6f044-113"><xref:System.Net.Http.WinHttpHandler></span></span> | <span data-ttu-id="6f044-114">Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> com base na interface WinHTTP do Windows.</span><span class="sxs-lookup"><span data-stu-id="6f044-114">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="6f044-115">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="6f044-115">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="6f044-116">Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="6f044-116">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <span data-ttu-id="6f044-117"><xref:System.Threading.Tasks.Dataflow></span><span class="sxs-lookup"><span data-stu-id="6f044-117"><xref:System.Threading.Tasks.Dataflow></span></span> | <span data-ttu-id="6f044-118">A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="6f044-118">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="6f044-119">Bibliotecas específicas da plataforma</span><span class="sxs-lookup"><span data-stu-id="6f044-119">Platform-specific libraries</span></span>
  
| <span data-ttu-id="6f044-120">Projeto</span><span class="sxs-lookup"><span data-stu-id="6f044-120">Project</span></span> | <span data-ttu-id="6f044-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f044-121">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="6f044-122"><xref:System.Text.CodePagesEncodingProvider></span><span class="sxs-lookup"><span data-stu-id="6f044-122"><xref:System.Text.CodePagesEncodingProvider></span></span> | <span data-ttu-id="6f044-123">Estende a classe <xref:System.Text.EncodingProvider> para disponibilizar codificações de página de código a aplicativos direcionados à Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="6f044-123">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="6f044-124">APIs privadas</span><span class="sxs-lookup"><span data-stu-id="6f044-124">Private APIs</span></span>  

<span data-ttu-id="6f044-125">Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="6f044-125">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="6f044-126">Nome da API</span><span class="sxs-lookup"><span data-stu-id="6f044-126">API Name</span></span> |  
| -------- |  
| [<span data-ttu-id="6f044-127">s_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="6f044-127">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |  
| [<span data-ttu-id="6f044-128">DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="6f044-128">DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |  
| [<span data-ttu-id="6f044-129">DataMemberListEditor Class</span><span class="sxs-lookup"><span data-stu-id="6f044-129">DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |  
  
## <a name="see-also"></a><span data-ttu-id="6f044-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f044-130">See also</span></span>

[<span data-ttu-id="6f044-131">O .NET Framework e lançamentos fora da banda</span><span class="sxs-lookup"><span data-stu-id="6f044-131">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

