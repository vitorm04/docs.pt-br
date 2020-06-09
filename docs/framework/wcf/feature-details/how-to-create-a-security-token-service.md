---
title: Como criar um serviço de token de segurança
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: 1cfcca524e5dd2b0c1560eb7600795766e2db1d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598951"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="3a5fe-102">Como criar um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="3a5fe-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="3a5fe-103">Um serviço de token de segurança implementa o protocolo definido na especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="3a5fe-104">Esse protocolo define os formatos de mensagem e os padrões de troca de mensagens para emissão, renovação, cancelamento e validação de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="3a5fe-105">Um determinado serviço de token de segurança fornece um ou mais desses recursos.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="3a5fe-106">Este tópico analisa o cenário mais comum: implementando a emissão de tokens.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="3a5fe-107">Emitindo tokens</span><span class="sxs-lookup"><span data-stu-id="3a5fe-107">Issuing Tokens</span></span>  
 <span data-ttu-id="3a5fe-108">O WS-Trust define formatos de mensagem, com base no `RequestSecurityToken` elemento de esquema XSD (linguagem de definição de esquema XML) e no `RequestSecurityTokenResponse` elemento de esquema XSD para executar a emissão de tokens.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="3a5fe-109">Além disso, ele define os URIs (identificadores de recursos uniformes) da ação associada.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="3a5fe-110">O URI de ação associado à `RequestSecurityToken` mensagem é `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` .</span><span class="sxs-lookup"><span data-stu-id="3a5fe-110">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="3a5fe-111">O URI de ação associado à `RequestSecurityTokenResponse` mensagem é `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .</span><span class="sxs-lookup"><span data-stu-id="3a5fe-111">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="3a5fe-112">Estrutura da mensagem de solicitação</span><span class="sxs-lookup"><span data-stu-id="3a5fe-112">Request Message Structure</span></span>  
 <span data-ttu-id="3a5fe-113">A estrutura da mensagem de solicitação de problema normalmente consiste nos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="3a5fe-113">The issue request message structure typically consists of the following items:</span></span>  
  
- <span data-ttu-id="3a5fe-114">Um URI de tipo de solicitação com um valor de `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .</span><span class="sxs-lookup"><span data-stu-id="3a5fe-114">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
- <span data-ttu-id="3a5fe-115">Um URI de tipo de token.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-115">A token type URI.</span></span> <span data-ttu-id="3a5fe-116">Para tokens 1,1 SAML (Security Asserts Markup Language), o valor desse URI é `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .</span><span class="sxs-lookup"><span data-stu-id="3a5fe-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
- <span data-ttu-id="3a5fe-117">Um valor de tamanho de chave que indica o número de bits na chave a ser associado ao token emitido.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
- <span data-ttu-id="3a5fe-118">Um URI de tipo de chave.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-118">A key type URI.</span></span> <span data-ttu-id="3a5fe-119">Para chaves simétricas, o valor desse URI é `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .</span><span class="sxs-lookup"><span data-stu-id="3a5fe-119">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="3a5fe-120">Além disso, alguns outros itens podem estar presentes:</span><span class="sxs-lookup"><span data-stu-id="3a5fe-120">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="3a5fe-121">Material da chave fornecido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-121">Key material provided by the client.</span></span>  
  
- <span data-ttu-id="3a5fe-122">Informações de escopo que indicam o serviço de destino com o qual o token emitido será usado.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="3a5fe-123">O serviço de token de segurança usa as informações na mensagem de solicitação de problema ao construir a mensagem de resposta do problema.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="3a5fe-124">Estrutura da mensagem de resposta</span><span class="sxs-lookup"><span data-stu-id="3a5fe-124">Response Message Structure</span></span>  
 <span data-ttu-id="3a5fe-125">A estrutura da mensagem de resposta do problema normalmente consiste nos seguintes itens;</span><span class="sxs-lookup"><span data-stu-id="3a5fe-125">The issue response message structure typically consists of the following items;</span></span>  
  
- <span data-ttu-id="3a5fe-126">O token de segurança emitido, por exemplo, uma Asserção SAML 1,1.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
- <span data-ttu-id="3a5fe-127">Um token de prova associado ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-127">A proof token associated with the security token.</span></span> <span data-ttu-id="3a5fe-128">Para chaves simétricas, isso geralmente é uma forma criptografada do material da chave.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
- <span data-ttu-id="3a5fe-129">Referências ao token de segurança emitido.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-129">References to the issued security token.</span></span> <span data-ttu-id="3a5fe-130">Normalmente, o serviço de token de segurança retorna uma referência que pode ser usada quando o token emitido aparece em uma mensagem subsequente enviada pelo cliente e outra que pode ser usada quando o token não está presente nas mensagens subsequentes.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="3a5fe-131">Além disso, alguns outros itens podem estar presentes:</span><span class="sxs-lookup"><span data-stu-id="3a5fe-131">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="3a5fe-132">Material da chave fornecido pelo serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-132">Key material provided by the security token service.</span></span>  
  
- <span data-ttu-id="3a5fe-133">O algoritmo necessário para computar a chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-133">The algorithm needed to compute the shared key.</span></span>  
  
- <span data-ttu-id="3a5fe-134">Informações de tempo de vida para o token emitido.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="3a5fe-135">Processando mensagens de solicitação</span><span class="sxs-lookup"><span data-stu-id="3a5fe-135">Processing Request Messages</span></span>  
 <span data-ttu-id="3a5fe-136">O serviço de token de segurança processa a solicitação de problema examinando as várias partes da mensagem de solicitação e garantindo que ela possa emitir um token que satisfaça a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="3a5fe-137">O serviço de token de segurança deve determinar o seguinte antes de construir o token a ser emitido:</span><span class="sxs-lookup"><span data-stu-id="3a5fe-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
- <span data-ttu-id="3a5fe-138">A solicitação é realmente uma solicitação para que um token seja emitido.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-138">The request really is a request for a token to be issued.</span></span>  
  
- <span data-ttu-id="3a5fe-139">O serviço de token de segurança dá suporte ao tipo de token solicitado.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-139">The security token service supports the requested token type.</span></span>  
  
- <span data-ttu-id="3a5fe-140">O solicitante está autorizado a fazer a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-140">The requester is authorized to make the request.</span></span>  
  
- <span data-ttu-id="3a5fe-141">O serviço de token de segurança pode atender às expectativas do solicitante em relação ao material da chave.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="3a5fe-142">Duas partes vitais da construção de um token estão determinando a chave com a qual assinar o token e a chave com a qual criptografar a chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="3a5fe-143">O token precisa ser assinado para que, quando o cliente apresentar o token para o serviço de destino, esse serviço possa determinar que o token foi emitido por um serviço de token de segurança que ele confia.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="3a5fe-144">O material da chave precisa ser criptografado de forma que o serviço de destino possa descriptografar esse material da chave.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="3a5fe-145">Assinar uma Asserção SAML envolve a criação de uma <xref:System.IdentityModel.Tokens.SigningCredentials> instância.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="3a5fe-146">O construtor para essa classe usa o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3a5fe-146">The constructor for this class takes the following:</span></span>  
  
- <span data-ttu-id="3a5fe-147">Um <xref:System.IdentityModel.Tokens.SecurityKey> para a chave a ser usada para assinar a ASSERÇÃO SAML.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
- <span data-ttu-id="3a5fe-148">Uma cadeia de caracteres que identifica o algoritmo de assinatura a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-148">A string identifying the signature algorithm to use.</span></span>  
  
- <span data-ttu-id="3a5fe-149">Uma cadeia de caracteres que identifica o algoritmo de resumo a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-149">A string identifying the digest algorithm to use.</span></span>  
  
- <span data-ttu-id="3a5fe-150">Opcionalmente, um <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> que identifica a chave a ser usada para assinar a asserção.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="3a5fe-151">Criptografar a chave compartilhada envolve pegar o material da chave e criptografá-lo com uma chave que o serviço de destino pode usar para descriptografar a chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="3a5fe-152">Normalmente, a chave pública do serviço de destino é usada.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="3a5fe-153">Além disso, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> é necessário um para a chave criptografada.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="3a5fe-154">Isso <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> é usado para criar um `SamlSubject` como parte do `SamlToken` .</span><span class="sxs-lookup"><span data-stu-id="3a5fe-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="3a5fe-155">Para obter mais informações, consulte [exemplo de Federação](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3a5fe-155">For more information, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="3a5fe-156">Criando mensagens de resposta</span><span class="sxs-lookup"><span data-stu-id="3a5fe-156">Creating Response Messages</span></span>  
 <span data-ttu-id="3a5fe-157">Depois que o serviço de token de segurança processa a solicitação de problema e constrói o token a ser emitido junto com a chave de prova, a mensagem de resposta precisa ser construída, incluindo pelo menos o token solicitado, o token de prova e as referências de token emitidas.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="3a5fe-158">O token emitido normalmente é <xref:System.IdentityModel.Tokens.SamlSecurityToken> criado a partir do <xref:System.IdentityModel.Tokens.SamlAssertion> , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="3a5fe-159">No caso em que o serviço de token de segurança fornece o material de chave compartilhada, o token de prova é construído pela criação de um <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="3a5fe-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="3a5fe-160">Para obter mais informações sobre como construir o token de prova quando o cliente e o serviço de token de segurança fornecem o material de chave para a chave compartilhada, consulte [exemplo de Federação](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3a5fe-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="3a5fe-161">As referências de token emitidas são criadas pela criação de instâncias da <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> classe.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="3a5fe-162">Esses vários valores são serializados na mensagem de resposta retornada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="3a5fe-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a5fe-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a5fe-163">Example</span></span>  
 <span data-ttu-id="3a5fe-164">Para obter o código completo de um serviço de token de segurança, consulte [exemplo de Federação](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3a5fe-164">For full code for a security token service, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5fe-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a5fe-165">See also</span></span>

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [<span data-ttu-id="3a5fe-166">Exemplo de federação</span><span class="sxs-lookup"><span data-stu-id="3a5fe-166">Federation Sample</span></span>](../samples/federation-sample.md)
