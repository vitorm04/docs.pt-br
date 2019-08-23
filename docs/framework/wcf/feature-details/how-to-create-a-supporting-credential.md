---
title: 'Como: criar uma credencial de suporte'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1f95748235aa5238193b8869f8330f0a7fc650d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968893"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="20e20-102">Como: criar uma credencial de suporte</span><span class="sxs-lookup"><span data-stu-id="20e20-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="20e20-103">É possível ter um esquema de segurança personalizado que exija mais de uma credencial.</span><span class="sxs-lookup"><span data-stu-id="20e20-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="20e20-104">Por exemplo, um serviço pode exigir do cliente não apenas um nome de usuário e uma senha, mas também uma credencial que comprova que o cliente está acima da idade de 18.</span><span class="sxs-lookup"><span data-stu-id="20e20-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="20e20-105">A segunda credencial é uma credencial de *suporte*.</span><span class="sxs-lookup"><span data-stu-id="20e20-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="20e20-106">Este tópico explica como implementar essas credenciais em um cliente Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="20e20-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20e20-107">A especificação para dar suporte a credenciais faz parte da especificação WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="20e20-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="20e20-108">Para obter mais informações, consulte [especificações de especificação Web Services Security](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="20e20-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="20e20-109">Tokens com suporte</span><span class="sxs-lookup"><span data-stu-id="20e20-109">Supporting Tokens</span></span>  
 <span data-ttu-id="20e20-110">Em resumo, quando você usa a segurança da mensagem, uma *credencial primária* é sempre usada para proteger a mensagem (por exemplo, um certificado X. 509 ou um tíquete Kerberos).</span><span class="sxs-lookup"><span data-stu-id="20e20-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="20e20-111">Conforme definido pela especificação, uma associação de segurança usa *tokens* para proteger a troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="20e20-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="20e20-112">Um *token* é uma representação de uma credencial de segurança.</span><span class="sxs-lookup"><span data-stu-id="20e20-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="20e20-113">A associação de segurança usa um token primário identificado na política de associação de segurança para criar uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="20e20-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="20e20-114">Essa assinatura é conhecida como a *assinatura da mensagem*.</span><span class="sxs-lookup"><span data-stu-id="20e20-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="20e20-115">Tokens adicionais podem ser especificados para aumentar as declarações fornecidas pelo token associado à assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="20e20-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="20e20-116">Endossando, assinando e criptografando</span><span class="sxs-lookup"><span data-stu-id="20e20-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="20e20-117">Uma credencial de suporte resulta em um *token de suporte* transmitido dentro da mensagem.</span><span class="sxs-lookup"><span data-stu-id="20e20-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="20e20-118">A especificação WS-SecurityPolicy define quatro maneiras de anexar um token de suporte à mensagem, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="20e20-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="20e20-119">Finalidade</span><span class="sxs-lookup"><span data-stu-id="20e20-119">Purpose</span></span>|<span data-ttu-id="20e20-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="20e20-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20e20-121">Assinado</span><span class="sxs-lookup"><span data-stu-id="20e20-121">Signed</span></span>|<span data-ttu-id="20e20-122">O token de suporte é incluído no cabeçalho de segurança e é assinado pela assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="20e20-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="20e20-123">Endosso</span><span class="sxs-lookup"><span data-stu-id="20e20-123">Endorsing</span></span>|<span data-ttu-id="20e20-124">Um *token de endosso* assina a assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="20e20-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="20e20-125">Assinado e endossador</span><span class="sxs-lookup"><span data-stu-id="20e20-125">Signed and Endorsing</span></span>|<span data-ttu-id="20e20-126">Assinados, os tokens de endosso `ds:Signature` assinam todo o elemento produzido da assinatura da mensagem e são assinados por essa assinatura de mensagem; ou seja, ambos os tokens (o token usado para a assinatura de mensagem e o token de endosso assinado) se assinam uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="20e20-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="20e20-127">Assinado e criptografado</span><span class="sxs-lookup"><span data-stu-id="20e20-127">Signed and Encrypting</span></span>|<span data-ttu-id="20e20-128">Tokens de suporte criptografados assinados são tokens de suporte assinados que também são `wsse:SecurityHeader`criptografados quando aparecem no.</span><span class="sxs-lookup"><span data-stu-id="20e20-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="20e20-129">Programando credenciais de suporte</span><span class="sxs-lookup"><span data-stu-id="20e20-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="20e20-130">Para criar um serviço que usa tokens de suporte, você deve criar um [ \<> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="20e20-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="20e20-131">(Para obter mais informações, [consulte Como: Crie uma associação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="20e20-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="20e20-132">A primeira etapa ao criar uma associação personalizada é criar um elemento de associação de segurança, que pode ser um dos três tipos:</span><span class="sxs-lookup"><span data-stu-id="20e20-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="20e20-133">Todas as classes herdam <xref:System.ServiceModel.Channels.SecurityBindingElement>do, que inclui quatro propriedades relevantes:</span><span class="sxs-lookup"><span data-stu-id="20e20-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="20e20-134">Escopos</span><span class="sxs-lookup"><span data-stu-id="20e20-134">Scopes</span></span>  
 <span data-ttu-id="20e20-135">Existem dois escopos para dar suporte a credenciais:</span><span class="sxs-lookup"><span data-stu-id="20e20-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="20e20-136">Os tokens de *suporte do ponto de extremidade* oferecem suporte a todas as operações de um ponto</span><span class="sxs-lookup"><span data-stu-id="20e20-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="20e20-137">Ou seja, a credencial que o token de suporte representa pode ser usada sempre que qualquer operação de ponto de extremidade for invocada.</span><span class="sxs-lookup"><span data-stu-id="20e20-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="20e20-138">Os tokens de *suporte de operação* dão suporte apenas a uma operação de ponto de extremidade específica</span><span class="sxs-lookup"><span data-stu-id="20e20-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="20e20-139">Conforme indicado pelos nomes de propriedade, as credenciais de suporte podem ser obrigatórias ou opcionais.</span><span class="sxs-lookup"><span data-stu-id="20e20-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="20e20-140">Ou seja, se a credencial de suporte for usada se estiver presente, embora não seja necessário, mas a autenticação não falhará se ela não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="20e20-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="20e20-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="20e20-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="20e20-142">Para criar uma associação personalizada que inclui credenciais de suporte</span><span class="sxs-lookup"><span data-stu-id="20e20-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="20e20-143">Crie um elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="20e20-143">Create a security binding element.</span></span> <span data-ttu-id="20e20-144">O exemplo a seguir cria <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> um com `UserNameForCertificate` o modo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="20e20-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="20e20-145">Use o método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="20e20-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="20e20-146">Adicione o parâmetro de suporte à coleção de tipos retornada pela propriedade`Endorsing`apropriada ( `SignedEncrypted`, `Signed`, ou `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="20e20-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="20e20-147">Os tipos no <xref:System.ServiceModel.Security.Tokens> namespace incluem tipos comumente usados, como o <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="20e20-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20e20-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20e20-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="20e20-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="20e20-149">Description</span></span>  
 <span data-ttu-id="20e20-150">O exemplo a seguir cria uma instância do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e adiciona uma instância <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> da classe à coleção que a propriedade de endosso retornou.</span><span class="sxs-lookup"><span data-stu-id="20e20-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="20e20-151">Código</span><span class="sxs-lookup"><span data-stu-id="20e20-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="20e20-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20e20-152">See also</span></span>

- [<span data-ttu-id="20e20-153">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="20e20-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
