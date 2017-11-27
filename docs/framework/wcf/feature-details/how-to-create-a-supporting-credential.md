---
title: Como criar uma credencial de suporte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c140b96fab0227a1563c8c1a511053d8d1ab944
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="3a4b2-102">Como criar uma credencial de suporte</span><span class="sxs-lookup"><span data-stu-id="3a4b2-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="3a4b2-103">É possível ter um esquema de segurança personalizado que requer mais de uma credencial.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="3a4b2-104">Por exemplo, um serviço pode demandar do cliente não apenas um nome de usuário e senha, mas também uma credencial que comprove o cliente é com mais de 18.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="3a4b2-105">A credencial de segundo é um *suporte credencial*.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="3a4b2-106">Este tópico explica como implementar essas credenciais em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-106">This topic explains how to implement such credentials in an [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a4b2-107">A especificação para dar suporte a credenciais faz parte da especificação WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="3a4b2-108">[Especificações de segurança de serviços web](http://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="3a4b2-108"> [Web Services Security Specifications](http://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="3a4b2-109">Tokens com suporte</span><span class="sxs-lookup"><span data-stu-id="3a4b2-109">Supporting Tokens</span></span>  
 <span data-ttu-id="3a4b2-110">Em suma, quando você usa segurança de mensagem, um *credencial primário* sempre é usado para proteger a mensagem (por exemplo, um certificado x. 509 ou um tíquete Kerberos).</span><span class="sxs-lookup"><span data-stu-id="3a4b2-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="3a4b2-111">Conforme definido pela especificação, usa uma associação de segurança *tokens* para proteger a troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="3a4b2-112">Um *token* é uma representação de uma credencial de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="3a4b2-113">A associação de segurança usa um token primário identificado na política de associação de segurança para criar uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="3a4b2-114">Esta assinatura é conhecida como o *assinatura da mensagem*.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="3a4b2-115">Tokens adicionais podem ser especificados para aumentar as declarações fornecidas pelo símbolo associado com a assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="3a4b2-116">Endossando, assinatura e criptografia</span><span class="sxs-lookup"><span data-stu-id="3a4b2-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="3a4b2-117">Uma credencial de suporte resulta em uma *token de suporte* transmitidos dentro a mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="3a4b2-118">A especificação WS-SecurityPolicy define quatro maneiras para anexar um token de suporte para a mensagem, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="3a4b2-119">Finalidade</span><span class="sxs-lookup"><span data-stu-id="3a4b2-119">Purpose</span></span>|<span data-ttu-id="3a4b2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a4b2-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a4b2-121">Assinado</span><span class="sxs-lookup"><span data-stu-id="3a4b2-121">Signed</span></span>|<span data-ttu-id="3a4b2-122">O token de suporte está incluído no cabeçalho de segurança e é assinado pela assinatura de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="3a4b2-123">Endossando</span><span class="sxs-lookup"><span data-stu-id="3a4b2-123">Endorsing</span></span>|<span data-ttu-id="3a4b2-124">Um *um token* assina a assinatura da mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="3a4b2-125">Endosso e não assinados</span><span class="sxs-lookup"><span data-stu-id="3a4b2-125">Signed and Endorsing</span></span>|<span data-ttu-id="3a4b2-126">Assinado, endossando tokens de entrada todo o `ds:Signature` elemento próprios produzido da assinatura da mensagem e são assinados por essa assinatura de mensagem; ou seja, ambos os tokens (o token usado para a assinatura da mensagem e o token de endosso assinado) entrar uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="3a4b2-127">Criptografia e não assinados</span><span class="sxs-lookup"><span data-stu-id="3a4b2-127">Signed and Encrypting</span></span>|<span data-ttu-id="3a4b2-128">Tokens de suporte assinados e criptografados são assinados para dar suporte a tokens que também são criptografadas quando elas aparecerem no `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="3a4b2-129">Credenciais de programação com suporte</span><span class="sxs-lookup"><span data-stu-id="3a4b2-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="3a4b2-130">Para criar um serviço que usa tokens de suporte, você deve criar um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="3a4b2-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="3a4b2-131">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="3a4b2-131">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="3a4b2-132">A primeira etapa ao criar uma associação personalizada é criar um elemento de associação de segurança, que pode ser um dos três tipos:</span><span class="sxs-lookup"><span data-stu-id="3a4b2-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="3a4b2-133">Todas as classes herdam o <xref:System.ServiceModel.Channels.SecurityBindingElement>, que inclui quatro propriedades relevantes:</span><span class="sxs-lookup"><span data-stu-id="3a4b2-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="3a4b2-134">Escopos</span><span class="sxs-lookup"><span data-stu-id="3a4b2-134">Scopes</span></span>  
 <span data-ttu-id="3a4b2-135">Existem dois escopos para dar suporte a credenciais:</span><span class="sxs-lookup"><span data-stu-id="3a4b2-135">Two scopes exist for supporting credentials:</span></span>  
  
-   <span data-ttu-id="3a4b2-136">*Ponto de extremidade de dar suporte a tokens* oferece suporte a todas as operações de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="3a4b2-137">Ou seja, a credencial que representa o token de suporte pode ser usada sempre que qualquer operação de ponto de extremidade é invocadas.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
-   <span data-ttu-id="3a4b2-138">*Operação de dar suporte a tokens* dar suporte a apenas uma operação de ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="3a4b2-139">Conforme indicado pelos nomes de propriedade, as credenciais de suporte pode ser obrigatório ou opcional.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="3a4b2-140">Ou seja, se a credencial de suporte será usada se estiver presente, embora ele não é necessário, mas a autenticação não falharão se não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="3a4b2-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="3a4b2-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="3a4b2-142">Para criar uma associação personalizada que inclui as credenciais de suporte</span><span class="sxs-lookup"><span data-stu-id="3a4b2-142">To create a custom binding that includes supporting credentials</span></span>  
  
1.  <span data-ttu-id="3a4b2-143">Crie um elemento de associação de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-143">Create a security binding element.</span></span> <span data-ttu-id="3a4b2-144">O exemplo a seguir cria um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> com o `UserNameForCertificate` modo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="3a4b2-145">Use o método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2.  <span data-ttu-id="3a4b2-146">Adicione o parâmetro de suporte para a coleção de tipos retornados pela propriedade apropriada (`Endorsing`, `Signed`, `SignedEncrypted`, ou `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="3a4b2-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="3a4b2-147">Os tipos no <xref:System.ServiceModel.Security.Tokens> namespace incluem tipos de uso geral, como o <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a4b2-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a4b2-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3a4b2-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a4b2-149">Description</span></span>  
 <span data-ttu-id="3a4b2-150">O exemplo a seguir cria uma instância do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e adiciona uma instância do <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> a propriedade Endorsing retornada da classe à coleção.</span><span class="sxs-lookup"><span data-stu-id="3a4b2-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3a4b2-151">Código</span><span class="sxs-lookup"><span data-stu-id="3a4b2-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3a4b2-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a4b2-152">See Also</span></span>  
 [<span data-ttu-id="3a4b2-153">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3a4b2-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
