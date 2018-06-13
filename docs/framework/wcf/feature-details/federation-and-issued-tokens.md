---
title: Federação e tokens emitidos
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: b6a5411b74b53cb5e3b18cced7fd8fc09e9a9676
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491569"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="e5ca6-102">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e5ca6-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="e5ca6-103">Com o Windows Communication Foundation (WCF), você pode criar clientes que se comunicam com segurança com os serviços que implementam as especificações de WS-Federation e WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="e5ca6-104">As especificações de usam XML, SOAP e WSDL Web Services Description Language () para fornecer mecanismos que permitem a autenticação e autorização em realms de confiança diferente.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5ca6-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e5ca6-105">In This Section</span></span>  
 [<span data-ttu-id="e5ca6-106">Federação</span><span class="sxs-lookup"><span data-stu-id="e5ca6-106">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 <span data-ttu-id="e5ca6-107">Fornece uma visão geral da federação.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="e5ca6-108">Federação e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="e5ca6-108">Federation and Trust</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 <span data-ttu-id="e5ca6-109">Lista os problemas de design para estar ciente de quando criar federado serviços ou clientes.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="e5ca6-110">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="e5ca6-110">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 <span data-ttu-id="e5ca6-111">Descreve os conceitos básicos de criação de um cliente federado com o WCF.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="e5ca6-112">Como configurar as credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="e5ca6-112">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="e5ca6-113">Descreve as etapas de criação de um serviço federado.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="e5ca6-114">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e5ca6-114">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="e5ca6-115">Descreve como configurar clientes e serviços que usam o `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="e5ca6-116">Como criar um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="e5ca6-116">How to: Create a Security Token Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 <span data-ttu-id="e5ca6-117">Descreve as etapas de criação de um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="e5ca6-118">Declarações e tokens de SAML (Security Assertions Markup Language)</span><span class="sxs-lookup"><span data-stu-id="e5ca6-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 <span data-ttu-id="e5ca6-119">Descreve os tokens de segurança asserções Markup Language (SAML), que são extensíveis e habilitar a criação avançada tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="e5ca6-120">Como configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="e5ca6-120">How to: Configure a Local Issuer</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="e5ca6-121">Descreve como criar um emissor local dos tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="e5ca6-122">Como: desabilitar sessões seguras em um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e5ca6-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="e5ca6-123">Descreve como desabilitar sessões seguras em uma `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="e5ca6-124">Desabilitar sessões seguras é necessário ao criar uma Web farm que exige uma sessão para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="e5ca6-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e5ca6-125">Referência</span><span class="sxs-lookup"><span data-stu-id="e5ca6-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="e5ca6-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5ca6-126">See Also</span></span>  
 [<span data-ttu-id="e5ca6-127">Autorização</span><span class="sxs-lookup"><span data-stu-id="e5ca6-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="e5ca6-128">Tokens personalizados</span><span class="sxs-lookup"><span data-stu-id="e5ca6-128">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [<span data-ttu-id="e5ca6-129">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="e5ca6-129">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
