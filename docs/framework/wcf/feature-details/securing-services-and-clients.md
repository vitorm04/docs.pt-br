---
title: "Protegendo serviços e clientes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ed37992b5488d33b9292bdd54eef47f9eb12f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="35fb0-102">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="35fb0-102">Securing Services and Clients</span></span>
<span data-ttu-id="35fb0-103">As informações nesta seção se concentra na programação de segurança no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35fb0-103">The information in this section focuses on programming security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="35fb0-104">Em geral, isso inclui a seleção de uma associação fornecida pelo sistema apropriada, definindo as propriedades do elemento de segurança e, em seguida, definir propriedades dos comportamentos de serviço que determinam como as credenciais são recuperadas para uso, o serviço ou cliente.</span><span class="sxs-lookup"><span data-stu-id="35fb0-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="35fb0-105">Essas técnicas aborda os requisitos de segurança da maioria dos usuários para a maioria dos cenários, como mostrado na [cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="35fb0-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="35fb0-106">Se seu cenário exigir mais recursos, consulte primeiro [recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); se uma solução não estiver visível, consulte [estendendo segurança](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="35fb0-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="35fb0-107">Se você estiver criando (ou interagir com) um sistema que usa declarações avançada, consulte os tópicos [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="35fb0-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35fb0-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="35fb0-108">In This Section</span></span>  
 [<span data-ttu-id="35fb0-109">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="35fb0-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="35fb0-110">Uma visão geral do modelo de programação usada para proteger as mensagens.</span><span class="sxs-lookup"><span data-stu-id="35fb0-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="35fb0-111">Visão geral de segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="35fb0-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="35fb0-112">Uma visão geral de como proteger mensagens por meio da camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="35fb0-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="35fb0-113">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="35fb0-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="35fb0-114">Resume os motivos para usar a segurança em nível de mensagem [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35fb0-114">Summarizes reasons for using message-level security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 [<span data-ttu-id="35fb0-115">Sessões seguras</span><span class="sxs-lookup"><span data-stu-id="35fb0-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="35fb0-116">Uma discussão sobre as considerações necessárias ao proteger um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessão.</span><span class="sxs-lookup"><span data-stu-id="35fb0-116">A discussion of the considerations required when securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] session.</span></span>  
  
 [<span data-ttu-id="35fb0-117">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="35fb0-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="35fb0-118">Obter uma explicação de algumas das tarefas comuns exigidas quando usando certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="35fb0-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="35fb0-119">Referência</span><span class="sxs-lookup"><span data-stu-id="35fb0-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="35fb0-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="35fb0-120">Related Sections</span></span>  
 [<span data-ttu-id="35fb0-121">Conceitos de segurança</span><span class="sxs-lookup"><span data-stu-id="35fb0-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="35fb0-122">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="35fb0-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="35fb0-123">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="35fb0-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="35fb0-124">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="35fb0-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="35fb0-125">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="35fb0-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="35fb0-126">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="35fb0-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="35fb0-127">Autorização</span><span class="sxs-lookup"><span data-stu-id="35fb0-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="35fb0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35fb0-128">See Also</span></span>  
 <span data-ttu-id="35fb0-129">[Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md) (Programação básica do WCF)</span><span class="sxs-lookup"><span data-stu-id="35fb0-129">[Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md)</span></span>  
 [<span data-ttu-id="35fb0-130">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="35fb0-130">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
