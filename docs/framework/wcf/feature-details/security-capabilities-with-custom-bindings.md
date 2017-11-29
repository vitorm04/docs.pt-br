---
title: "Recursos de segurança com associações personalizadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9d252dca363c952dde44b499363e285d4bb7eb82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="ef11b-102">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ef11b-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="ef11b-103">Você pode executar tarefas mais comuns de segurança usando uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="ef11b-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="ef11b-104">Se você precisar de mais controle, no entanto, você pode criar uma associação personalizada com um <xref:System.ServiceModel.Channels.SecurityBindingElement>, conforme explicado nestes tópicos.</span><span class="sxs-lookup"><span data-stu-id="ef11b-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ef11b-105">associações personalizadas, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ef11b-105"> custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef11b-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ef11b-106">In This Section</span></span>  
 [<span data-ttu-id="ef11b-107">Modos de autenticação SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef11b-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="ef11b-108">Descreve os modos de autenticação que são possíveis com uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="ef11b-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="ef11b-109">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef11b-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="ef11b-110">Descreve as etapas básicas para criar uma associação personalizada com um elemento de segurança.</span><span class="sxs-lookup"><span data-stu-id="ef11b-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="ef11b-111">Como: criar um SecurityBindingElement para um modo de autenticação especificado</span><span class="sxs-lookup"><span data-stu-id="ef11b-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="ef11b-112">Descreve como criar um elemento de segurança para um modo de autenticação especificado.</span><span class="sxs-lookup"><span data-stu-id="ef11b-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="ef11b-113">Como: desabilitar sessões seguranças em uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ef11b-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="ef11b-114">Descreve como desabilitar sessões seguras durante a criação de um serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="ef11b-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="ef11b-115">Como: habilitar a detecção de repetição de mensagem</span><span class="sxs-lookup"><span data-stu-id="ef11b-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="ef11b-116">Descreve como determinar quando ocorre um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="ef11b-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="ef11b-117">Como: criar uma credencial de suporte</span><span class="sxs-lookup"><span data-stu-id="ef11b-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="ef11b-118">Descreve como fornecer uma credencial de suporte a um serviço, se o serviço exigir.</span><span class="sxs-lookup"><span data-stu-id="ef11b-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="ef11b-119">Como: configurar uma confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="ef11b-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="ef11b-120">Descreve as etapas para confirmar assinaturas ao assinar digitalmente as mensagens.</span><span class="sxs-lookup"><span data-stu-id="ef11b-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="ef11b-121">Como: definir uma máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="ef11b-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="ef11b-122">Descreve como definir a diferença de tempo máximo permitido entre um serviço e um cliente.</span><span class="sxs-lookup"><span data-stu-id="ef11b-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="ef11b-123">Como: desabilitar a criptografia de assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="ef11b-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="ef11b-124">Descreve como desabilitar a criptografia de assinaturas digitais que pode ter um benefício de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ef11b-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ef11b-125">Referência</span><span class="sxs-lookup"><span data-stu-id="ef11b-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="ef11b-126">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="ef11b-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="ef11b-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ef11b-127">Related Sections</span></span>  
 <span data-ttu-id="ef11b-128">[Understanding Protection Level](../../../../docs/framework/wcf/understanding-protection-level.md) (Noções básicas de nível de proteção)</span><span class="sxs-lookup"><span data-stu-id="ef11b-128">[Understanding Protection Level](../../../../docs/framework/wcf/understanding-protection-level.md)</span></span>  
  
 [<span data-ttu-id="ef11b-129">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ef11b-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef11b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef11b-130">See Also</span></span>  
 [<span data-ttu-id="ef11b-131">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="ef11b-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="ef11b-132">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="ef11b-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="ef11b-133">[System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md) (Associações fornecidas pelo sistema)</span><span class="sxs-lookup"><span data-stu-id="ef11b-133">[System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)</span></span>
