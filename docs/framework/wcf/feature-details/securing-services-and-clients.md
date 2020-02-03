---
title: Protegendo serviços e clientes
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746419"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="71de6-102">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="71de6-102">Securing Services and Clients</span></span>
<span data-ttu-id="71de6-103">As informações contidas nesta seção concentram-se na segurança de programação no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="71de6-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="71de6-104">Em geral, isso inclui a seleção de uma associação apropriada fornecida pelo sistema, a definição das propriedades do elemento de segurança e a configuração das propriedades dos comportamentos de serviço que regem o modo como as credenciais são recuperadas para uso pelo serviço ou pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="71de6-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="71de6-105">Essas técnicas abrangem os requisitos de segurança da maioria dos usuários para a maioria dos cenários, conforme mostrado em [cenários de segurança comuns](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="71de6-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="71de6-106">Se seu cenário exigir mais recursos, primeiro consulte [recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); se uma solução não for aparente, consulte [estendendo a segurança](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="71de6-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="71de6-107">Se você estiver criando (ou Interoperando com) um sistema que usa declarações avançadas, consulte os tópicos em [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="71de6-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71de6-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="71de6-108">In This Section</span></span>  
 [<span data-ttu-id="71de6-109">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="71de6-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="71de6-110">Uma visão geral do modelo de programação usado para proteger mensagens.</span><span class="sxs-lookup"><span data-stu-id="71de6-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="71de6-111">Visão geral de segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="71de6-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="71de6-112">Uma visão geral de como proteger mensagens por meio da camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="71de6-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="71de6-113">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="71de6-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="71de6-114">Resume os motivos para usar a segurança em nível de mensagem no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="71de6-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="71de6-115">Sessões seguras</span><span class="sxs-lookup"><span data-stu-id="71de6-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="71de6-116">Uma discussão sobre as considerações necessárias ao proteger uma sessão do WCF.</span><span class="sxs-lookup"><span data-stu-id="71de6-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="71de6-117">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="71de6-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="71de6-118">Uma explicação de algumas das tarefas comuns necessárias ao usar certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="71de6-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="71de6-119">Referência</span><span class="sxs-lookup"><span data-stu-id="71de6-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="71de6-120">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="71de6-120">Related Sections</span></span>  
 [<span data-ttu-id="71de6-121">Conceitos de segurança</span><span class="sxs-lookup"><span data-stu-id="71de6-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="71de6-122">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="71de6-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="71de6-123">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="71de6-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="71de6-124">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="71de6-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="71de6-125">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="71de6-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="71de6-126">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="71de6-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="71de6-127">Autorização</span><span class="sxs-lookup"><span data-stu-id="71de6-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="71de6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71de6-128">See also</span></span>

- [<span data-ttu-id="71de6-129">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="71de6-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- <span data-ttu-id="71de6-130">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="71de6-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
