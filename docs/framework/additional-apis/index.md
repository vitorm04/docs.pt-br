---
title: Bibliotecas de classes e APIs adicionais
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3bb7a7c53cbca8bbd4026b46ce59589cef22382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="aff71-102">Bibliotecas de classes e APIs adicionais</span><span class="sxs-lookup"><span data-stu-id="aff71-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="aff71-103">O .NET Framework está em constante evolução e, para melhorar o desenvolvimento multiplataforma e introduzir novas funcionalidades o quanto antes para nossos clientes, lançamos novos recursos OOB (fora de banda).</span><span class="sxs-lookup"><span data-stu-id="aff71-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="aff71-104">Este tópico lista os projetos OOB para os quais fornecemos documentação.</span><span class="sxs-lookup"><span data-stu-id="aff71-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="aff71-105">Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aff71-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="aff71-106">Por exemplo, a <xref:System.Text.CodePagesEncodingProvider> classe disponibiliza codificações de página de código para aplicativos UWP desenvolvidos usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aff71-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="aff71-107">Este tópico também lista essas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="aff71-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="aff71-108">Projetos OOB</span><span class="sxs-lookup"><span data-stu-id="aff71-108">OOB projects</span></span>
  
| <span data-ttu-id="aff71-109">Projeto</span><span class="sxs-lookup"><span data-stu-id="aff71-109">Project</span></span> | <span data-ttu-id="aff71-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="aff71-110">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="aff71-111">Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado.</span><span class="sxs-lookup"><span data-stu-id="aff71-111">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="aff71-112">Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> com base na interface do WinHTTP do Windows.</span><span class="sxs-lookup"><span data-stu-id="aff71-112">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="aff71-113">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="aff71-113">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="aff71-114">Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="aff71-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="aff71-115">A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="aff71-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="aff71-116">Bibliotecas específicas da plataforma</span><span class="sxs-lookup"><span data-stu-id="aff71-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="aff71-117">Projeto</span><span class="sxs-lookup"><span data-stu-id="aff71-117">Project</span></span> | <span data-ttu-id="aff71-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="aff71-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="aff71-119">Estende o <xref:System.Text.EncodingProvider> classe para disponibilizar as codificações de página de código para aplicativos que se destinam a plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="aff71-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="aff71-120">APIs privadas</span><span class="sxs-lookup"><span data-stu-id="aff71-120">Private APIs</span></span>  

<span data-ttu-id="aff71-121">Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="aff71-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="aff71-122">Nome da API</span><span class="sxs-lookup"><span data-stu-id="aff71-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="aff71-123">Classe System.Net.Connection</span><span class="sxs-lookup"><span data-stu-id="aff71-123">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="aff71-124">System.Net.Connection.m\_WriteList campo</span><span class="sxs-lookup"><span data-stu-id="aff71-124">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="aff71-125">Classe System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="aff71-125">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="aff71-126">System.Net.ConnectionGroup.m\_ConnectionList campo</span><span class="sxs-lookup"><span data-stu-id="aff71-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="aff71-127">System.Net.HttpWebRequest. \_HttpResponse campo</span><span class="sxs-lookup"><span data-stu-id="aff71-127">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="aff71-128">System.Net.HttpWebRequest. \_AutoRedirects campo</span><span class="sxs-lookup"><span data-stu-id="aff71-128">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="aff71-129">System.Net.ServicePoint.m\_ConnectionGroupList campo</span><span class="sxs-lookup"><span data-stu-id="aff71-129">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="aff71-130">System.Net.ServicePointManager.s\_ServicePointTable campo</span><span class="sxs-lookup"><span data-stu-id="aff71-130">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="aff71-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes campo</span><span class="sxs-lookup"><span data-stu-id="aff71-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="aff71-132">Classe System.Windows.Forms.Design.DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="aff71-132">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="aff71-133">Classe System.Windows.Forms.Design.DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="aff71-133">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="aff71-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aff71-134">See also</span></span>

[<span data-ttu-id="aff71-135">O .NET Framework e lançamentos fora da banda</span><span class="sxs-lookup"><span data-stu-id="aff71-135">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
