---
title: Declarações e tokens de SAML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bd10fe663ccb4c78af775baf3e76663ef9a91bd
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="cdf42-102">Declarações e tokens de SAML</span><span class="sxs-lookup"><span data-stu-id="cdf42-102">SAML Tokens and Claims</span></span>
<span data-ttu-id="cdf42-103">Security asserções Markup Language (SAML) *tokens* são representações de XML de declarações.</span><span class="sxs-lookup"><span data-stu-id="cdf42-103">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="cdf42-104">Por padrão, os tokens SAML [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usa em cenários de segurança federada é *tokens emitidos*.</span><span class="sxs-lookup"><span data-stu-id="cdf42-104">By default, SAML tokens [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="cdf42-105">Tokens SAML executar instruções que são conjuntos de declarações feitas por uma entidade sobre outra entidade.</span><span class="sxs-lookup"><span data-stu-id="cdf42-105">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="cdf42-106">Por exemplo, em cenários de segurança federada, as instruções são feitas por um serviço de token de segurança sobre um usuário no sistema.</span><span class="sxs-lookup"><span data-stu-id="cdf42-106">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="cdf42-107">O serviço de token de segurança assina o token SAML para indicar a veracidade das instruções contidas no token.</span><span class="sxs-lookup"><span data-stu-id="cdf42-107">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="cdf42-108">Além disso, o token SAML é associado ao material de chave de criptografia que o usuário do token SAML prova conhecimento de.</span><span class="sxs-lookup"><span data-stu-id="cdf42-108">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="cdf42-109">Essa prova de acordo com a terceira parte confiável que o token SAML, na verdade, é emitido para o usuário.</span><span class="sxs-lookup"><span data-stu-id="cdf42-109">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="cdf42-110">Por exemplo, em um cenário típico:</span><span class="sxs-lookup"><span data-stu-id="cdf42-110">For example, in a typical scenario:</span></span>  
  
1.  <span data-ttu-id="cdf42-111">Um cliente solicita um token SAML de um serviço de token de segurança de autenticação para esse serviço de token de segurança usando as credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="cdf42-111">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="cdf42-112">O serviço de token de segurança emite um token SAML para o cliente.</span><span class="sxs-lookup"><span data-stu-id="cdf42-112">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="cdf42-113">O token SAML é assinado com um certificado associado com o serviço de token de segurança e contém uma chave de prova criptografada para o serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="cdf42-113">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3.  <span data-ttu-id="cdf42-114">O cliente também recebe uma cópia do *chave de prova*.</span><span class="sxs-lookup"><span data-stu-id="cdf42-114">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="cdf42-115">O cliente, em seguida, apresenta o token SAML para o serviço de aplicativo (o *terceira parte confiável*) e assina a mensagem com a chave de prova.</span><span class="sxs-lookup"><span data-stu-id="cdf42-115">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4.  <span data-ttu-id="cdf42-116">A assinatura sobre o token SAML informa a terceira parte confiável que o serviço de token de segurança emitido o token.</span><span class="sxs-lookup"><span data-stu-id="cdf42-116">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="cdf42-117">A assinatura da mensagem criada com a chave de prova informa a terceira parte confiável que o token foi emitido para o cliente.</span><span class="sxs-lookup"><span data-stu-id="cdf42-117">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="cdf42-118">De declarações para SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="cdf42-118">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="cdf42-119">Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], declarações nos tokens SAML são modeladas como <xref:System.IdentityModel.Tokens.SamlAttribute> objetos, que podem ser preenchidos diretamente do <xref:System.IdentityModel.Claims.Claim> objetos, fornecidos o <xref:System.IdentityModel.Claims.Claim> objeto tem um <xref:System.IdentityModel.Claims.Claim.Right%2A> propriedade de <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> e o <xref:System.IdentityModel.Claims.Claim.Resource%2A> a propriedade é do tipo <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="cdf42-119">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="cdf42-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cdf42-120">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  <span data-ttu-id="cdf42-121">Quando os tokens SAML são serializados em mensagens, quando eles são emitidos por um serviço de token de segurança ou quando são apresentadas pelos clientes para serviços como parte da autenticação, a cota de tamanho máximo da mensagem deve ser grande o suficiente para acomodar o token SAML e as outras partes da mensagem.</span><span class="sxs-lookup"><span data-stu-id="cdf42-121">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="cdf42-122">Em casos normais, as cotas de tamanho de mensagem padrão são suficientes.</span><span class="sxs-lookup"><span data-stu-id="cdf42-122">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="cdf42-123">No entanto, em casos em que um token SAML é grande porque ele contém centenas de declarações, você precisará aumentar as cotas para acomodar o token serializado.</span><span class="sxs-lookup"><span data-stu-id="cdf42-123">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> <span data-ttu-id="cdf42-124">Para obter mais informações, consulte [considerações de segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="cdf42-124">For more information, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="cdf42-125">De SamlAttributes declarações</span><span class="sxs-lookup"><span data-stu-id="cdf42-125">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="cdf42-126">Quando os tokens SAML são recebidos em mensagens, as várias instruções no token de SAML são transformadas em <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objetos que são colocados no <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="cdf42-126">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="cdf42-127">As declarações de cada instrução de SAML são retornadas pelo <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> propriedade o <xref:System.IdentityModel.Policy.AuthorizationContext> e pode ser examinado para determinar se é autenticar e autorizar o usuário.</span><span class="sxs-lookup"><span data-stu-id="cdf42-127">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf42-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdf42-128">See Also</span></span>  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="cdf42-129">Federação</span><span class="sxs-lookup"><span data-stu-id="cdf42-129">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="cdf42-130">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="cdf42-130">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="cdf42-131">Como configurar as credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="cdf42-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="cdf42-132">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="cdf42-132">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="cdf42-133">Declarações e tokens</span><span class="sxs-lookup"><span data-stu-id="cdf42-133">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [<span data-ttu-id="cdf42-134">Valores de recursos e criação de declarações</span><span class="sxs-lookup"><span data-stu-id="cdf42-134">Claim Creation and Resource Values</span></span>](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [<span data-ttu-id="cdf42-135">Como criar uma declaração personalizada</span><span class="sxs-lookup"><span data-stu-id="cdf42-135">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
