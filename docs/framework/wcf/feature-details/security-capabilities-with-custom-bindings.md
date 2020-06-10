---
title: Recursos de segurança com associações personalizadas
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595187"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="c9f04-102">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c9f04-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="c9f04-103">Você pode executar as tarefas de segurança mais comuns usando uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="c9f04-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="c9f04-104">No entanto, se você precisar de mais controle, poderá criar uma associação personalizada com uma <xref:System.ServiceModel.Channels.SecurityBindingElement> , conforme explicado nestes tópicos.</span><span class="sxs-lookup"><span data-stu-id="c9f04-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="c9f04-105">Para obter mais informações sobre associações personalizadas, consulte [associações personalizadas](../extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c9f04-105">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9f04-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c9f04-106">In This Section</span></span>  
 [<span data-ttu-id="c9f04-107">SecurityBindingElement Authentication Modes</span><span class="sxs-lookup"><span data-stu-id="c9f04-107">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="c9f04-108">Descreve os modos de autenticação que são possíveis com uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c9f04-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="c9f04-109">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c9f04-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="c9f04-110">Descreve as etapas básicas para criar uma associação personalizada com um elemento de segurança.</span><span class="sxs-lookup"><span data-stu-id="c9f04-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="c9f04-111">Como criar um SecurityBindingElement para um modo de autenticação especificado</span><span class="sxs-lookup"><span data-stu-id="c9f04-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="c9f04-112">Descreve como criar um elemento de segurança para um modo de autenticação especificado.</span><span class="sxs-lookup"><span data-stu-id="c9f04-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="c9f04-113">Como desabilitar sessões seguranças em uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c9f04-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="c9f04-114">Descreve como desabilitar sessões seguras ao criar um serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="c9f04-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="c9f04-115">Como habilitar a detecção de repetição de mensagem</span><span class="sxs-lookup"><span data-stu-id="c9f04-115">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="c9f04-116">Descreve como determinar quando ocorre um ataque de reprodução.</span><span class="sxs-lookup"><span data-stu-id="c9f04-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="c9f04-117">Como criar uma credencial de suporte</span><span class="sxs-lookup"><span data-stu-id="c9f04-117">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="c9f04-118">Descreve como fornecer uma credencial de suporte a um serviço, se o serviço exigir.</span><span class="sxs-lookup"><span data-stu-id="c9f04-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="c9f04-119">Como definir uma confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="c9f04-119">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="c9f04-120">Descreve as etapas para confirmar as assinaturas ao assinar digitalmente as mensagens.</span><span class="sxs-lookup"><span data-stu-id="c9f04-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="c9f04-121">Como definir a precisão máxima do relógio</span><span class="sxs-lookup"><span data-stu-id="c9f04-121">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="c9f04-122">Descreve como definir a diferença de tempo máxima permitida entre um serviço e um cliente.</span><span class="sxs-lookup"><span data-stu-id="c9f04-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="c9f04-123">Como desabilitar criptografia de assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="c9f04-123">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="c9f04-124">Descreve como desabilitar a criptografia de assinaturas digitais pode ter um benefício de desempenho.</span><span class="sxs-lookup"><span data-stu-id="c9f04-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c9f04-125">Referência</span><span class="sxs-lookup"><span data-stu-id="c9f04-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="c9f04-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c9f04-126">Related Sections</span></span>  
 [<span data-ttu-id="c9f04-127">Noções básicas de nível de proteção</span><span class="sxs-lookup"><span data-stu-id="c9f04-127">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="c9f04-128">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c9f04-128">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9f04-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9f04-129">See also</span></span>

- [<span data-ttu-id="c9f04-130">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="c9f04-130">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="c9f04-131">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="c9f04-131">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="c9f04-132">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c9f04-132">System-Provided Bindings</span></span>](../system-provided-bindings.md)
