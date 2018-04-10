---
title: Bibliotecas de classes e APIs adicionais
ms.custom: ''
ms.date: 01/29/2018
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
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
ms.workload:
- dotnet
ms.openlocfilehash: d9ceb1ad24d4ba87fab7713ba61fed91eef26c4d
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="34cfc-102">Bibliotecas de classes e APIs adicionais</span><span class="sxs-lookup"><span data-stu-id="34cfc-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="34cfc-103">O .NET Framework está em constante evolução e, para melhorar o desenvolvimento multiplataforma e introduzir novas funcionalidades o quanto antes para nossos clientes, lançamos novos recursos OOB (fora de banda).</span><span class="sxs-lookup"><span data-stu-id="34cfc-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="34cfc-104">Este tópico lista os projetos OOB para os quais fornecemos documentação.</span><span class="sxs-lookup"><span data-stu-id="34cfc-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="34cfc-105">Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34cfc-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="34cfc-106">Por exemplo, a <xref:System.Text.CodePagesEncodingProvider> classe disponibiliza codificações de página de código para aplicativos UWP desenvolvidos usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34cfc-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="34cfc-107">Este tópico também lista essas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="34cfc-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="34cfc-108">Projetos OOB</span><span class="sxs-lookup"><span data-stu-id="34cfc-108">OOB projects</span></span>
  
| <span data-ttu-id="34cfc-109">Projeto</span><span class="sxs-lookup"><span data-stu-id="34cfc-109">Project</span></span> | <span data-ttu-id="34cfc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="34cfc-110">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="34cfc-111">Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado.</span><span class="sxs-lookup"><span data-stu-id="34cfc-111">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="34cfc-112">Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> com base na interface do WinHTTP do Windows.</span><span class="sxs-lookup"><span data-stu-id="34cfc-112">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="34cfc-113">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="34cfc-113">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="34cfc-114">Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="34cfc-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="34cfc-115">A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="34cfc-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="34cfc-116">Bibliotecas específicas da plataforma</span><span class="sxs-lookup"><span data-stu-id="34cfc-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="34cfc-117">Projeto</span><span class="sxs-lookup"><span data-stu-id="34cfc-117">Project</span></span> | <span data-ttu-id="34cfc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="34cfc-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="34cfc-119">Estende o <xref:System.Text.EncodingProvider> classe para disponibilizar as codificações de página de código para aplicativos que se destinam a plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="34cfc-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="34cfc-120">APIs privadas</span><span class="sxs-lookup"><span data-stu-id="34cfc-120">Private APIs</span></span>  

<span data-ttu-id="34cfc-121">Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="34cfc-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="34cfc-122">Nome da API</span><span class="sxs-lookup"><span data-stu-id="34cfc-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="34cfc-123">Classe System.Net.Connection</span><span class="sxs-lookup"><span data-stu-id="34cfc-123">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="34cfc-124">System.Net.Connection.m\_WriteList Field</span><span class="sxs-lookup"><span data-stu-id="34cfc-124">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="34cfc-125">Classe System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="34cfc-125">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="34cfc-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="34cfc-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="34cfc-127">System.Net.CoreResponseData Class</span><span class="sxs-lookup"><span data-stu-id="34cfc-127">System.Net.CoreResponseData Class</span></span>](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [<span data-ttu-id="34cfc-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="34cfc-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="34cfc-129">System.Net.CoreResponseData.m\_StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="34cfc-129">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="34cfc-130">System.Net.HttpWebRequest. \_AutoRedirects campo</span><span class="sxs-lookup"><span data-stu-id="34cfc-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="34cfc-131">System.Net.HttpWebRequest. \_CoreResponse campo</span><span class="sxs-lookup"><span data-stu-id="34cfc-131">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="34cfc-132">System.Net.HttpWebRequest. \_HttpResponse campo</span><span class="sxs-lookup"><span data-stu-id="34cfc-132">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="34cfc-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="34cfc-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="34cfc-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="34cfc-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="34cfc-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="34cfc-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="34cfc-136">Classe System.Windows.Forms.Design.DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="34cfc-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="34cfc-137">Classe System.Windows.Forms.Design.DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="34cfc-137">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="34cfc-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34cfc-138">See also</span></span>

[<span data-ttu-id="34cfc-139">O .NET Framework e lançamentos fora da banda</span><span class="sxs-lookup"><span data-stu-id="34cfc-139">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
