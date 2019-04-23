---
title: Recursos de segurança com associações personalizadas
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 25d203fa706eeb0d0ccf1eaf4367ffa5bd7b83aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157268"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="64f28-102">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="64f28-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="64f28-103">Você pode executar tarefas mais comuns de segurança usando uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="64f28-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="64f28-104">Se você precisar de mais controle, no entanto, você pode criar uma ligação personalizada com um <xref:System.ServiceModel.Channels.SecurityBindingElement>, conforme explicado nestes tópicos.</span><span class="sxs-lookup"><span data-stu-id="64f28-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="64f28-105">Para obter mais informações sobre ligações personalizadas, consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="64f28-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64f28-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="64f28-106">In This Section</span></span>  
 [<span data-ttu-id="64f28-107">Modos de autenticação de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="64f28-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="64f28-108">Descreve os modos de autenticação que são possíveis com uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="64f28-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="64f28-109">Como: Criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="64f28-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="64f28-110">Descreve as etapas básicas para criar uma associação personalizada com um elemento de segurança.</span><span class="sxs-lookup"><span data-stu-id="64f28-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="64f28-111">Como: Criar um SecurityBindingElement para um modo de autenticação especificado</span><span class="sxs-lookup"><span data-stu-id="64f28-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="64f28-112">Descreve como criar um elemento de segurança para um modo de autenticação especificado.</span><span class="sxs-lookup"><span data-stu-id="64f28-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="64f28-113">Como: Desabilitar sessões seguras em um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="64f28-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="64f28-114">Descreve como desabilitar sessões seguras ao criar um serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="64f28-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="64f28-115">Como: Habilitar a detecção de reprodução de mensagem</span><span class="sxs-lookup"><span data-stu-id="64f28-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="64f28-116">Descreve como determinar quando ocorre um ataque de repetição.</span><span class="sxs-lookup"><span data-stu-id="64f28-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="64f28-117">Como: Criar uma credencial de suporte</span><span class="sxs-lookup"><span data-stu-id="64f28-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="64f28-118">Descreve como fornecer uma credencial de suporte a um serviço, se o serviço exigir.</span><span class="sxs-lookup"><span data-stu-id="64f28-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="64f28-119">Como: Configurar uma confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="64f28-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="64f28-120">Descreve as etapas para confirmar assinaturas ao assinar digitalmente as mensagens.</span><span class="sxs-lookup"><span data-stu-id="64f28-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="64f28-121">Como: Definir uma distorção máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="64f28-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="64f28-122">Descreve como definir a diferença de tempo máximo permitido entre um serviço e um cliente.</span><span class="sxs-lookup"><span data-stu-id="64f28-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="64f28-123">Como: Desabilitar a criptografia de assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="64f28-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="64f28-124">Descreve como desabilitar a criptografia de assinaturas digitais que pode ter um benefício de desempenho.</span><span class="sxs-lookup"><span data-stu-id="64f28-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="64f28-125">Referência</span><span class="sxs-lookup"><span data-stu-id="64f28-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="64f28-126">\<security></span><span class="sxs-lookup"><span data-stu-id="64f28-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="64f28-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="64f28-127">Related Sections</span></span>  
 [<span data-ttu-id="64f28-128">Noções básicas de nível de proteção</span><span class="sxs-lookup"><span data-stu-id="64f28-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="64f28-129">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="64f28-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="64f28-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64f28-130">See also</span></span>

- [<span data-ttu-id="64f28-131">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="64f28-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="64f28-132">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="64f28-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="64f28-133">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="64f28-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
