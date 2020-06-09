---
title: Como definir uma confirmação de assinatura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586904"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="74086-102">Como definir uma confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="74086-102">How to: Set Up a Signature Confirmation</span></span>

<span data-ttu-id="74086-103">A *confirmação de assinatura* é um mecanismo para um iniciador de mensagem garantir que uma resposta recebida tenha sido gerada em resposta à mensagem original do remetente.</span><span class="sxs-lookup"><span data-stu-id="74086-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="74086-104">A confirmação de assinatura é definida na especificação WS-Security 1,1.</span><span class="sxs-lookup"><span data-stu-id="74086-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="74086-105">Se um ponto de extremidade oferecer suporte ao WS-Security 1,0, você não poderá usar a confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="74086-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>

<span data-ttu-id="74086-106">Os procedimentos a seguir especificam como habilitar a confirmação de assinatura usando um <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="74086-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="74086-107">Você pode usar o mesmo procedimento com um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="74086-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="74086-108">O procedimento se baseia nas etapas básicas encontradas em [como: criar uma associação personalizada usando o SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="74086-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="74086-109">Para habilitar a confirmação de assinatura no código</span><span class="sxs-lookup"><span data-stu-id="74086-109">To enable signature confirmation in code</span></span>

1. <span data-ttu-id="74086-110">Criar uma instância da classe <xref:System.ServiceModel.Channels.BindingElementCollection>.</span><span class="sxs-lookup"><span data-stu-id="74086-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>

2. <span data-ttu-id="74086-111">Crie uma instância da <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="74086-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>

3. <span data-ttu-id="74086-112">Defina o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="74086-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>

4. <span data-ttu-id="74086-113">Adicione o elemento Security à coleção Binding.</span><span class="sxs-lookup"><span data-stu-id="74086-113">Add the security element to the binding collection.</span></span>

5. <span data-ttu-id="74086-114">Crie uma associação personalizada, conforme especificado em [como: criar uma associação personalizada usando o SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="74086-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="74086-115">Para habilitar a confirmação de assinatura na configuração</span><span class="sxs-lookup"><span data-stu-id="74086-115">To enable signature confirmation in configuration</span></span>

1. <span data-ttu-id="74086-116">Adicione um `<customBinding>` elemento à `<bindings>` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="74086-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>

2. <span data-ttu-id="74086-117">Adicione um `<binding>` elemento e defina o atributo Name para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="74086-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>

3. <span data-ttu-id="74086-118">Adicione um elemento Encoding apropriado.</span><span class="sxs-lookup"><span data-stu-id="74086-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="74086-119">O exemplo a seguir adiciona um `<TextMessageEncoding>` elemento.</span><span class="sxs-lookup"><span data-stu-id="74086-119">The following example adds a `<TextMessageEncoding>` element.</span></span>

4. <span data-ttu-id="74086-120">Adicione um `<security>` elemento filho e defina o `requireSignatureConfirmation` atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="74086-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

5. <span data-ttu-id="74086-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="74086-121">Optional.</span></span> <span data-ttu-id="74086-122">Para habilitar a confirmação de assinatura durante a inicialização, adicione um [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento filho e defina o `requireSignatureConfirmation` atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="74086-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

6. <span data-ttu-id="74086-123">Adicione um elemento de transporte apropriado.</span><span class="sxs-lookup"><span data-stu-id="74086-123">Add an appropriate transport element.</span></span> <span data-ttu-id="74086-124">O exemplo a seguir adiciona um [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :</span><span class="sxs-lookup"><span data-stu-id="74086-124">The following example adds an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md):</span></span>

    ```xml
    <bindings>
      <customBinding>
        <binding name="SignatureConfirmationBinding">
          <security requireSignatureConfirmation="true">
            <secureConversationBootstrap requireSignatureConfirmation="true" />
              </security>
           <textMessageEncoding />
             <httpTransport />
        </binding>
      </customBinding>
    </bindings>
    ```

## <a name="example"></a><span data-ttu-id="74086-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74086-125">Example</span></span>

<span data-ttu-id="74086-126">O código a seguir cria uma instância do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e define a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> propriedade como `true` .</span><span class="sxs-lookup"><span data-stu-id="74086-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="74086-127">Observe que este exemplo não usa o `<secureConversationBootstrap>` elemento mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="74086-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="74086-128">Este exemplo demonstra a confirmação de assinatura ao usar um token do Windows (protocolo Kerberos).</span><span class="sxs-lookup"><span data-stu-id="74086-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="74086-129">Nesse caso, a assinatura do cliente é retornada em todas as respostas do serviço e é confirmada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="74086-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="74086-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74086-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="74086-131">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="74086-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="74086-132">Como criar um SecurityBindingElement para um modo de autenticação especificado</span><span class="sxs-lookup"><span data-stu-id="74086-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
