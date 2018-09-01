---
title: Segurança do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a070800ea15c5a7f16b52ca69c7e454c92618e1a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384922"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="c09f4-102">Segurança do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c09f4-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="c09f4-103">Os tópicos nesta seção descrevem os recursos de segurança do Windows Communication Foundation (WCF) e como usá-los para ajudar a proteger mensagens.</span><span class="sxs-lookup"><span data-stu-id="c09f4-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="c09f4-104">Para obter mais informações sobre a segurança e o Windows Server AppFabric, consulte [modelo de segurança para o Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="c09f4-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c09f4-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c09f4-105">In This Section</span></span>  
 [<span data-ttu-id="c09f4-106">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="c09f4-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="c09f4-107">Descreve os recursos de segurança no WCF.</span><span class="sxs-lookup"><span data-stu-id="c09f4-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="c09f4-108">Conceitos de segurança</span><span class="sxs-lookup"><span data-stu-id="c09f4-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="c09f4-109">Descreve a terminologia básica e conceitos usados na segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="c09f4-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="c09f4-110">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="c09f4-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="c09f4-111">Descreve os cenários e topologias que você pode configurar com o WCF.</span><span class="sxs-lookup"><span data-stu-id="c09f4-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="c09f4-112">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="c09f4-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="c09f4-113">Fornece uma visão geral dos comportamentos do WCF que afetam a segurança, como a configuração de credenciais.</span><span class="sxs-lookup"><span data-stu-id="c09f4-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="c09f4-114">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="c09f4-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="c09f4-115">Uma exibição orientadas a segurança das associações, incluindo tópicos que demonstram como criar associações de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="c09f4-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="c09f4-116">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c09f4-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="c09f4-117">Descreve como proteger mensagens usando recursos de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="c09f4-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="c09f4-118">Autenticação</span><span class="sxs-lookup"><span data-stu-id="c09f4-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="c09f4-119">Demonstra as tarefas comuns de autenticação.</span><span class="sxs-lookup"><span data-stu-id="c09f4-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="c09f4-120">Autorização</span><span class="sxs-lookup"><span data-stu-id="c09f4-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="c09f4-121">Descreve cenários comuns de autorização com implementações de segurança.</span><span class="sxs-lookup"><span data-stu-id="c09f4-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="c09f4-122">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c09f4-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="c09f4-123">Descreve os fundamentos da federação e como criar clientes que se comunicam com servidores federados.</span><span class="sxs-lookup"><span data-stu-id="c09f4-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="c09f4-124">Confiança parcial</span><span class="sxs-lookup"><span data-stu-id="c09f4-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="c09f4-125">Descreve como executar cenários de confiança parcial e limitações do WCF ao executar parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="c09f4-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="c09f4-126">Auditoria</span><span class="sxs-lookup"><span data-stu-id="c09f4-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="c09f4-127">Descreve como fazer a auditoria de eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="c09f4-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="c09f4-128">Diretrizes e práticas recomendadas de segurança</span><span class="sxs-lookup"><span data-stu-id="c09f4-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="c09f4-129">Diretrizes para criação de aplicativos seguros do WCF.</span><span class="sxs-lookup"><span data-stu-id="c09f4-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c09f4-130">Referência</span><span class="sxs-lookup"><span data-stu-id="c09f4-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="c09f4-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c09f4-131">Related Sections</span></span>  
 [<span data-ttu-id="c09f4-132">Detalhes de recursos do WCF</span><span class="sxs-lookup"><span data-stu-id="c09f4-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="c09f4-133">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="c09f4-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="c09f4-134">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="c09f4-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="c09f4-135">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="c09f4-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="c09f4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c09f4-136">See Also</span></span>  
 [<span data-ttu-id="c09f4-137">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c09f4-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
