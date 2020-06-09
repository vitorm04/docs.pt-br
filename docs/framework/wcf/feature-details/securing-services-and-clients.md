---
title: Protegendo serviços e clientes
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: db0a0dcfbe04a7b7dbfabfed59f9b8637d0a2797
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586202"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="9f9fa-102">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9f9fa-102">Securing Services and Clients</span></span>
<span data-ttu-id="9f9fa-103">As informações contidas nesta seção concentram-se na segurança de programação no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9f9fa-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="9f9fa-104">Em geral, isso inclui a seleção de uma associação apropriada fornecida pelo sistema, a definição das propriedades do elemento de segurança e a configuração das propriedades dos comportamentos de serviço que regem o modo como as credenciais são recuperadas para uso pelo serviço ou pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="9f9fa-105">Essas técnicas abrangem os requisitos de segurança da maioria dos usuários para a maioria dos cenários, conforme mostrado em [cenários de segurança comuns](common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="9f9fa-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="9f9fa-106">Se seu cenário exigir mais recursos, primeiro consulte [recursos de segurança com associações personalizadas](security-capabilities-with-custom-bindings.md); se uma solução não for aparente, consulte [estendendo a segurança](../extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="9f9fa-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="9f9fa-107">Se você estiver criando (ou Interoperando com) um sistema que usa declarações avançadas, consulte os tópicos em [autorização](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="9f9fa-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f9fa-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9f9fa-108">In This Section</span></span>  
 [<span data-ttu-id="9f9fa-109">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="9f9fa-109">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="9f9fa-110">Uma visão geral do modelo de programação usado para proteger mensagens.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="9f9fa-111">Visão geral de segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="9f9fa-111">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="9f9fa-112">Uma visão geral de como proteger mensagens por meio da camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="9f9fa-113">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="9f9fa-113">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="9f9fa-114">Resume os motivos para usar a segurança em nível de mensagem no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9f9fa-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="9f9fa-115">Sessões seguras</span><span class="sxs-lookup"><span data-stu-id="9f9fa-115">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="9f9fa-116">Uma discussão sobre as considerações necessárias ao proteger uma sessão do WCF.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="9f9fa-117">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="9f9fa-117">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="9f9fa-118">Uma explicação de algumas das tarefas comuns necessárias ao usar certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9f9fa-119">Referência</span><span class="sxs-lookup"><span data-stu-id="9f9fa-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="9f9fa-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9f9fa-120">Related Sections</span></span>  
 [<span data-ttu-id="9f9fa-121">Conceitos de segurança</span><span class="sxs-lookup"><span data-stu-id="9f9fa-121">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="9f9fa-122">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="9f9fa-122">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="9f9fa-123">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="9f9fa-123">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="9f9fa-124">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="9f9fa-124">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="9f9fa-125">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9f9fa-125">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="9f9fa-126">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="9f9fa-126">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="9f9fa-127">Autorização</span><span class="sxs-lookup"><span data-stu-id="9f9fa-127">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="9f9fa-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f9fa-128">See also</span></span>

- [<span data-ttu-id="9f9fa-129">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="9f9fa-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="9f9fa-130">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9f9fa-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
