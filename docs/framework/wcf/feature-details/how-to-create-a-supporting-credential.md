---
title: 'Como: criar uma credencial de suporte'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 7c6c4ea777f62541f8ca8fa79fdd024e5f5cf2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787602"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="54272-102">Como: criar uma credencial de suporte</span><span class="sxs-lookup"><span data-stu-id="54272-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="54272-103">É possível ter um esquema de segurança personalizado que requer mais de uma credencial.</span><span class="sxs-lookup"><span data-stu-id="54272-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="54272-104">Por exemplo, pode exigir que um serviço do cliente não apenas um nome de usuário e senha, mas também uma credencial que comprova o cliente é com mais de 18 anos.</span><span class="sxs-lookup"><span data-stu-id="54272-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="54272-105">A segunda credencial é um *que dão suporte a credencial*.</span><span class="sxs-lookup"><span data-stu-id="54272-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="54272-106">Este tópico explica como implementar essas credenciais em um cliente do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="54272-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54272-107">A especificação para dar suporte a credenciais é parte da especificação WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="54272-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="54272-108">Para obter mais informações, consulte [especificações de segurança de serviços Web](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="54272-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="54272-109">Tokens com suporte</span><span class="sxs-lookup"><span data-stu-id="54272-109">Supporting Tokens</span></span>  
 <span data-ttu-id="54272-110">Em resumo, quando você usa a segurança de mensagem, uma *credencial primário* sempre é usado para proteger a mensagem (por exemplo, um certificado X.509 ou um tíquete Kerberos).</span><span class="sxs-lookup"><span data-stu-id="54272-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="54272-111">Conforme definido pela especificação, uma associação de segurança usa *tokens* para proteger a troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="54272-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="54272-112">Um *token* é uma representação de uma credencial de segurança.</span><span class="sxs-lookup"><span data-stu-id="54272-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="54272-113">A associação de segurança usa um token de primário identificado na política de associação de segurança para criar uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="54272-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="54272-114">Essa assinatura é conhecida como o *assinatura da mensagem*.</span><span class="sxs-lookup"><span data-stu-id="54272-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="54272-115">Tokens adicionais podem ser especificados para aumentar as declarações fornecidas pelo token associado com a assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="54272-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="54272-116">Endossando, assinatura e criptografia</span><span class="sxs-lookup"><span data-stu-id="54272-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="54272-117">Uma credencial de suporte resulta em uma *token de suporte* transmitidos dentro da mensagem.</span><span class="sxs-lookup"><span data-stu-id="54272-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="54272-118">A especificação de WS-SecurityPolicy define quatro maneiras para anexar um token de suporte para a mensagem, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="54272-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="54272-119">Finalidade</span><span class="sxs-lookup"><span data-stu-id="54272-119">Purpose</span></span>|<span data-ttu-id="54272-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="54272-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54272-121">Assinado</span><span class="sxs-lookup"><span data-stu-id="54272-121">Signed</span></span>|<span data-ttu-id="54272-122">O token de suporte está incluído no cabeçalho de segurança e é assinado pela assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="54272-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="54272-123">Endossando</span><span class="sxs-lookup"><span data-stu-id="54272-123">Endorsing</span></span>|<span data-ttu-id="54272-124">Uma *token de endosso* assina a assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="54272-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="54272-125">Assinado e de endosso</span><span class="sxs-lookup"><span data-stu-id="54272-125">Signed and Endorsing</span></span>|<span data-ttu-id="54272-126">Assinado, endossando tokens de sinal de todo o `ds:Signature` elemento produzido a partir de assinatura da mensagem e são em si assinadas por essa assinatura de mensagem; ou seja, ambos os tokens (o token usado para a assinatura da mensagem e o token de endosso assinado) entrar uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="54272-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="54272-127">Criptografia e não assinados</span><span class="sxs-lookup"><span data-stu-id="54272-127">Signed and Encrypting</span></span>|<span data-ttu-id="54272-128">Tokens de suporte assinados e criptografados são assinados que dão suporte a tokens que também são criptografados quando são exibidas no `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="54272-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="54272-129">Programação que dão suporte a credenciais</span><span class="sxs-lookup"><span data-stu-id="54272-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="54272-130">Para criar um serviço que usa tokens de suporte, você deve criar uma [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="54272-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="54272-131">(Para obter mais informações, consulte [como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="54272-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="54272-132">A primeira etapa ao criar uma ligação personalizada é criar um elemento de associação de segurança, que pode ser um dos três tipos:</span><span class="sxs-lookup"><span data-stu-id="54272-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="54272-133">Todas as classes herdam o <xref:System.ServiceModel.Channels.SecurityBindingElement>, que inclui quatro propriedades relevantes:</span><span class="sxs-lookup"><span data-stu-id="54272-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="54272-134">Escopos</span><span class="sxs-lookup"><span data-stu-id="54272-134">Scopes</span></span>  
 <span data-ttu-id="54272-135">Existem dois escopos para dar suporte a credenciais:</span><span class="sxs-lookup"><span data-stu-id="54272-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="54272-136">*Ponto de extremidade que dão suporte a tokens* dão suporte a todas as operações de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="54272-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="54272-137">Ou seja, a credencial que representa o token de suporte pode ser usada sempre que qualquer operação de ponto de extremidade é invocadas.</span><span class="sxs-lookup"><span data-stu-id="54272-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="54272-138">*Operação de dar suporte a tokens* dar suporte a apenas uma operação de ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="54272-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="54272-139">Conforme indicado pelos nomes de propriedade, que dão suporte a credenciais pode ser obrigatório ou opcional.</span><span class="sxs-lookup"><span data-stu-id="54272-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="54272-140">Ou seja, se a credencial de suporte é usada se estiver presente, embora ele não é necessário, mas a autenticação não falhará se não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="54272-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="54272-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="54272-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="54272-142">Para criar uma associação personalizada que inclui suporte a credenciais</span><span class="sxs-lookup"><span data-stu-id="54272-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="54272-143">Crie um elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="54272-143">Create a security binding element.</span></span> <span data-ttu-id="54272-144">O exemplo a seguir cria uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> com o `UserNameForCertificate` modo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="54272-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="54272-145">Use o método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="54272-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="54272-146">Adicione o parâmetro de suporte para a coleção de tipos retornados pela propriedade apropriada (`Endorsing`, `Signed`, `SignedEncrypted`, ou `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="54272-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="54272-147">Os tipos na <xref:System.ServiceModel.Security.Tokens> namespace incluem tipos comumente usados, como o <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="54272-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54272-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54272-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="54272-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="54272-149">Description</span></span>  
 <span data-ttu-id="54272-150">O exemplo a seguir cria uma instância das <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e adiciona uma instância da <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> a propriedade Endorsing retornada da classe à coleção.</span><span class="sxs-lookup"><span data-stu-id="54272-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="54272-151">Código</span><span class="sxs-lookup"><span data-stu-id="54272-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="54272-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54272-152">See also</span></span>

- [<span data-ttu-id="54272-153">Como: Criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="54272-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
