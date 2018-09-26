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
author: BrucePerlerMS
ms.openlocfilehash: dd2c4f32978107a82ce940e0ef984c70f461b2c3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172187"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="48e82-102">Como criar um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="48e82-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="48e82-103">Um serviço de token de segurança implementa o protocolo definido na especificação WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="48e82-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="48e82-104">Esse protocolo define os formatos de mensagem e padrões de troca de mensagem para a emissão, renovação, cancelando e validando tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="48e82-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="48e82-105">Um serviço de token de segurança fornece uma ou mais desses recursos.</span><span class="sxs-lookup"><span data-stu-id="48e82-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="48e82-106">Este tópico é o cenário mais comum: implementação de emissão de token.</span><span class="sxs-lookup"><span data-stu-id="48e82-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="48e82-107">Emissão de Tokens</span><span class="sxs-lookup"><span data-stu-id="48e82-107">Issuing Tokens</span></span>  
 <span data-ttu-id="48e82-108">WS-Trust define os formatos de mensagem, com base nas `RequestSecurityToken` elemento de esquema XSD (linguagem) de definição de esquema XML, e `RequestSecurityTokenResponse` elemento do esquema XSD para a execução de emissão de token.</span><span class="sxs-lookup"><span data-stu-id="48e82-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="48e82-109">Além disso, ele define o associado ação de recurso uniformes (URIs).</span><span class="sxs-lookup"><span data-stu-id="48e82-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="48e82-110">A ação de URI associado a `RequestSecurityToken` mensagem é http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span><span class="sxs-lookup"><span data-stu-id="48e82-110">The action URI associated with the `RequestSecurityToken` message is http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span></span> <span data-ttu-id="48e82-111">A ação de URI associado a `RequestSecurityTokenResponse` mensagem é http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span><span class="sxs-lookup"><span data-stu-id="48e82-111">The action URI associated with the `RequestSecurityTokenResponse` message is   http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="48e82-112">Estrutura de mensagem de solicitação</span><span class="sxs-lookup"><span data-stu-id="48e82-112">Request Message Structure</span></span>  
 <span data-ttu-id="48e82-113">A estrutura de mensagens de solicitação de problema normalmente consiste dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="48e82-113">The issue request message structure typically consists of the following items:</span></span>  
  
-   <span data-ttu-id="48e82-114">URI de tipo de uma solicitação com um valor de http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span><span class="sxs-lookup"><span data-stu-id="48e82-114">A request type URI with a value of    http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span></span>  
  
-   <span data-ttu-id="48e82-115">Um tipo de token URI.</span><span class="sxs-lookup"><span data-stu-id="48e82-115">A token type URI.</span></span> <span data-ttu-id="48e82-116">Para tokens de segurança asserções Markup Language (SAML) 1.1, o valor desse URI é http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span><span class="sxs-lookup"><span data-stu-id="48e82-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span></span>  
  
-   <span data-ttu-id="48e82-117">Um valor de tamanho de chave que indica o número de bits na chave a ser associado com o token emitido.</span><span class="sxs-lookup"><span data-stu-id="48e82-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
-   <span data-ttu-id="48e82-118">Um tipo de chave URI.</span><span class="sxs-lookup"><span data-stu-id="48e82-118">A key type URI.</span></span> <span data-ttu-id="48e82-119">Para chaves simétricas, o valor desse URI é http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="48e82-119">For symmetric keys, the value of this URI is http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span></span>  
  
 <span data-ttu-id="48e82-120">Além disso, alguns outros itens podem estar presentes:</span><span class="sxs-lookup"><span data-stu-id="48e82-120">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="48e82-121">Material de chave fornecido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="48e82-121">Key material provided by the client.</span></span>  
  
-   <span data-ttu-id="48e82-122">Informações de escopo que indicam o serviço de destino que será usado com o token emitido.</span><span class="sxs-lookup"><span data-stu-id="48e82-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="48e82-123">O serviço de token de segurança usa as informações na mensagem de solicitação de problema ao construir a mensagem de resposta do problema.</span><span class="sxs-lookup"><span data-stu-id="48e82-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="48e82-124">Estrutura de mensagem de resposta</span><span class="sxs-lookup"><span data-stu-id="48e82-124">Response Message Structure</span></span>  
 <span data-ttu-id="48e82-125">A estrutura de mensagem de resposta de problema normalmente consiste dos seguintes itens;</span><span class="sxs-lookup"><span data-stu-id="48e82-125">The issue response message structure typically consists of the following items;</span></span>  
  
-   <span data-ttu-id="48e82-126">O token de segurança emitido, por exemplo, uma asserção SAML 1.1.</span><span class="sxs-lookup"><span data-stu-id="48e82-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
-   <span data-ttu-id="48e82-127">Um token de prova associado com o token de segurança.</span><span class="sxs-lookup"><span data-stu-id="48e82-127">A proof token associated with the security token.</span></span> <span data-ttu-id="48e82-128">As chaves simétricas, isso geralmente é um formato criptografado do material de chave.</span><span class="sxs-lookup"><span data-stu-id="48e82-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
-   <span data-ttu-id="48e82-129">Referências para o token de segurança emitido.</span><span class="sxs-lookup"><span data-stu-id="48e82-129">References to the issued security token.</span></span> <span data-ttu-id="48e82-130">Normalmente, o serviço de token de segurança retorna uma referência que pode ser usada quando o token emitido é exibido em uma mensagem subsequente enviada pelo cliente e outro que pode ser usada quando o token não está presente nas mensagens subsequentes.</span><span class="sxs-lookup"><span data-stu-id="48e82-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="48e82-131">Além disso, alguns outros itens podem estar presentes:</span><span class="sxs-lookup"><span data-stu-id="48e82-131">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="48e82-132">Material de chave fornecido pelo serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="48e82-132">Key material provided by the security token service.</span></span>  
  
-   <span data-ttu-id="48e82-133">O algoritmo necessário para calcular a chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="48e82-133">The algorithm needed to compute the shared key.</span></span>  
  
-   <span data-ttu-id="48e82-134">Informações de tempo de vida de token emitido.</span><span class="sxs-lookup"><span data-stu-id="48e82-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="48e82-135">Processando mensagens de solicitação</span><span class="sxs-lookup"><span data-stu-id="48e82-135">Processing Request Messages</span></span>  
 <span data-ttu-id="48e82-136">O serviço de token de segurança processa a solicitação de problema examinando as várias partes da mensagem de solicitação e garantindo que ele pode emitir um token que atende à solicitação.</span><span class="sxs-lookup"><span data-stu-id="48e82-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="48e82-137">O serviço de token de segurança deve determinar o seguinte antes de ele constrói o token a ser emitido:</span><span class="sxs-lookup"><span data-stu-id="48e82-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
-   <span data-ttu-id="48e82-138">A solicitação é realmente uma solicitação para um token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="48e82-138">The request really is a request for a token to be issued.</span></span>  
  
-   <span data-ttu-id="48e82-139">O serviço de token de segurança dá suporte ao tipo de token solicitado.</span><span class="sxs-lookup"><span data-stu-id="48e82-139">The security token service supports the requested token type.</span></span>  
  
-   <span data-ttu-id="48e82-140">O solicitante está autorizado a fazer a solicitação.</span><span class="sxs-lookup"><span data-stu-id="48e82-140">The requester is authorized to make the request.</span></span>  
  
-   <span data-ttu-id="48e82-141">O serviço de token de segurança pode atender às expectativas do solicitante com relação ao material de chave.</span><span class="sxs-lookup"><span data-stu-id="48e82-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="48e82-142">Duas partes vitais de construir um token são determinar qual chave para assinar o token com e qual chave deve criptografar a chave compartilhada com.</span><span class="sxs-lookup"><span data-stu-id="48e82-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="48e82-143">O token precisa ser assinado para que quando o cliente apresenta o token ao serviço de destino, o serviço pode determinar que o token foi emitido por um serviço de token de segurança que ele confia.</span><span class="sxs-lookup"><span data-stu-id="48e82-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="48e82-144">O material da chave precisa ser criptografado de tal forma que o serviço de destino pode descriptografar o material da chave.</span><span class="sxs-lookup"><span data-stu-id="48e82-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="48e82-145">Uma asserção SAML de assinatura envolve a criação de um <xref:System.IdentityModel.Tokens.SigningCredentials> instância.</span><span class="sxs-lookup"><span data-stu-id="48e82-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="48e82-146">O construtor para essa classe usa o seguinte:</span><span class="sxs-lookup"><span data-stu-id="48e82-146">The constructor for this class takes the following:</span></span>  
  
-   <span data-ttu-id="48e82-147">Um <xref:System.IdentityModel.Tokens.SecurityKey> para a chave a ser usado para assinar declaração SAML.</span><span class="sxs-lookup"><span data-stu-id="48e82-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
-   <span data-ttu-id="48e82-148">Uma cadeia de caracteres que identifica o algoritmo de assinatura a ser usado.</span><span class="sxs-lookup"><span data-stu-id="48e82-148">A string identifying the signature algorithm to use.</span></span>  
  
-   <span data-ttu-id="48e82-149">Uma cadeia de caracteres que identifica o algoritmo de resumo para usar.</span><span class="sxs-lookup"><span data-stu-id="48e82-149">A string identifying the digest algorithm to use.</span></span>  
  
-   <span data-ttu-id="48e82-150">Opcionalmente, um <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> que identifica a chave a ser usado para assinar a asserção.</span><span class="sxs-lookup"><span data-stu-id="48e82-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="48e82-151">Criptografar a chave compartilhada envolve pegar o material da chave e criptografá-los com uma chave que o serviço de destino pode usar para descriptografar a chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="48e82-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="48e82-152">Normalmente, a chave pública do serviço de destino é usada.</span><span class="sxs-lookup"><span data-stu-id="48e82-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="48e82-153">Além disso, um <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> para a chave criptografada é necessária.</span><span class="sxs-lookup"><span data-stu-id="48e82-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="48e82-154">Isso <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> , em seguida, é usado para criar um `SamlSubject` como parte do `SamlToken`.</span><span class="sxs-lookup"><span data-stu-id="48e82-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="48e82-155">Para obter mais informações, consulte [exemplo de Federação](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="48e82-155">For more information, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="48e82-156">Criação de mensagens de resposta</span><span class="sxs-lookup"><span data-stu-id="48e82-156">Creating Response Messages</span></span>  
 <span data-ttu-id="48e82-157">Depois que o serviço de token de segurança processa a solicitação de problema e constrói o token a ser emitido junto com a chave de prova, a mensagem de resposta precisa ser construído, incluindo pelo menos o token solicitado, o token de prova e as referências de token emitidas.</span><span class="sxs-lookup"><span data-stu-id="48e82-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="48e82-158">O token emitido é normalmente um <xref:System.IdentityModel.Tokens.SamlSecurityToken> criado a partir de <xref:System.IdentityModel.Tokens.SamlAssertion>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="48e82-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="48e82-159">No caso em que o serviço de token de segurança fornece o material da chave compartilhado, o token de prova é construído com a criação de um <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="48e82-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="48e82-160">Para obter mais informações sobre como construir o token de prova quando o cliente e o serviço de token de segurança fornecem o material da chave para a chave compartilhada, consulte [exemplo de Federação](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="48e82-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="48e82-161">As referências de token emitidas são construídas com a criação de instâncias do <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> classe.</span><span class="sxs-lookup"><span data-stu-id="48e82-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="48e82-162">Esses vários valores, em seguida, são serializados em mensagem de resposta retornada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="48e82-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e82-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48e82-163">Example</span></span>  
 <span data-ttu-id="48e82-164">Para o código completo para um serviço de token de segurança, consulte [exemplo de Federação](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="48e82-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e82-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48e82-165">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [<span data-ttu-id="48e82-166">Exemplo de federação</span><span class="sxs-lookup"><span data-stu-id="48e82-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
