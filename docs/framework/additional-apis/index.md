---
title: Bibliotecas de classes e APIs adicionais
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 049268c29946e95ca7bb194f6cae38baf8f060f6
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361937"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="07b12-102">Bibliotecas de classes e APIs adicionais</span><span class="sxs-lookup"><span data-stu-id="07b12-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="07b12-103">O .NET Framework está em constante evolução.</span><span class="sxs-lookup"><span data-stu-id="07b12-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="07b12-104">Para melhorar o desenvolvimento de plataforma cruzada e introduzir novas funcionalidades no início, os novos recursos são lançados fora de banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="07b12-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="07b12-105">Este tópico lista os projetos OOB para os quais fornecemos documentação.</span><span class="sxs-lookup"><span data-stu-id="07b12-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="07b12-106">Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07b12-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="07b12-107">Por exemplo, o <xref:System.Text.CodePagesEncodingProvider> classe disponibiliza as codificações de página de código para aplicativos UWP desenvolvidos usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07b12-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="07b12-108">Este tópico também lista essas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="07b12-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="07b12-109">Projetos OOB</span><span class="sxs-lookup"><span data-stu-id="07b12-109">OOB projects</span></span>
  
| <span data-ttu-id="07b12-110">Projeto</span><span class="sxs-lookup"><span data-stu-id="07b12-110">Project</span></span> | <span data-ttu-id="07b12-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="07b12-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="07b12-112">Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado.</span><span class="sxs-lookup"><span data-stu-id="07b12-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="07b12-113">Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> com base na interface do WinHTTP do Windows.</span><span class="sxs-lookup"><span data-stu-id="07b12-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="07b12-114">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="07b12-114">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="07b12-115">Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="07b12-115">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="07b12-116">A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="07b12-116">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="07b12-117">Bibliotecas específicas da plataforma</span><span class="sxs-lookup"><span data-stu-id="07b12-117">Platform-specific libraries</span></span>
  
| <span data-ttu-id="07b12-118">Projeto</span><span class="sxs-lookup"><span data-stu-id="07b12-118">Project</span></span> | <span data-ttu-id="07b12-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="07b12-119">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="07b12-120">Estende o <xref:System.Text.EncodingProvider> classe para disponibilizar codificações de página de código para aplicativos voltados para a plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="07b12-120">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="07b12-121">APIs privadas</span><span class="sxs-lookup"><span data-stu-id="07b12-121">Private APIs</span></span>  

<span data-ttu-id="07b12-122">Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="07b12-122">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="07b12-123">Nome da API</span><span class="sxs-lookup"><span data-stu-id="07b12-123">API Name</span></span> |
| -------- |
| [<span data-ttu-id="07b12-124">Classe System.Net.Connection</span><span class="sxs-lookup"><span data-stu-id="07b12-124">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="07b12-125">System.Net.Connection.m\_WriteList campo</span><span class="sxs-lookup"><span data-stu-id="07b12-125">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="07b12-126">Classe System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="07b12-126">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="07b12-127">System.Net.ConnectionGroup.m\_ConnectionList campo</span><span class="sxs-lookup"><span data-stu-id="07b12-127">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="07b12-128">Classe System.Net.CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="07b12-128">System.Net.CoreResponseData Class</span></span>](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [<span data-ttu-id="07b12-129">System.Net.CoreResponseData.m\_ResponseHeaders campo</span><span class="sxs-lookup"><span data-stu-id="07b12-129">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="07b12-130">System.Net.CoreResponseData.m\_campo StatusCode</span><span class="sxs-lookup"><span data-stu-id="07b12-130">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="07b12-131">System. \_Campo AutoRedirects</span><span class="sxs-lookup"><span data-stu-id="07b12-131">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="07b12-132">System. \_Campo CoreResponse</span><span class="sxs-lookup"><span data-stu-id="07b12-132">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="07b12-133">System. \_HttpResponse campo</span><span class="sxs-lookup"><span data-stu-id="07b12-133">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="07b12-134">System.Net.ServicePoint.m\_ConnectionGroupList campo</span><span class="sxs-lookup"><span data-stu-id="07b12-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="07b12-135">System.Net.ServicePointManager.s\_ServicePointTable campo</span><span class="sxs-lookup"><span data-stu-id="07b12-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="07b12-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes campo</span><span class="sxs-lookup"><span data-stu-id="07b12-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="07b12-137">Classe System.Windows.Forms.Design.DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="07b12-137">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="07b12-138">Classe System.Windows.Forms.Design.DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="07b12-138">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="07b12-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07b12-139">See also</span></span>

[<span data-ttu-id="07b12-140">O .NET Framework e lançamentos fora da banda</span><span class="sxs-lookup"><span data-stu-id="07b12-140">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
