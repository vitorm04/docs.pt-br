---
title: Autenticação no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: b513c9713bd2c04e125915d1a0a87c86ce249666
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597638"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="b4fb0-102">Autenticação no WCF</span><span class="sxs-lookup"><span data-stu-id="b4fb0-102">Authentication in WCF</span></span>
<span data-ttu-id="b4fb0-103">Os tópicos a seguir mostram vários mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, autenticação do Windows, certificados X. 509 e nome de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4fb0-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b4fb0-104">In This Section</span></span>  
 [<span data-ttu-id="b4fb0-105">Como utilizar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b4fb0-105">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="b4fb0-106">Os recursos do ASP.NET incluem uma associação e um provedor de função, um banco de dados para armazenar pares de nome de usuário/senha para autenticação e funções de usuário para autorização.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="b4fb0-107">Este tópico explica como os serviços WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="b4fb0-108">Como usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="b4fb0-108">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="b4fb0-109">Demonstra como integrar um validador de nome de usuário/senha personalizado.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="b4fb0-110">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="b4fb0-110">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="b4fb0-111">Como uma proteção extra, um cliente pode autenticar o serviço especificando a *identidade* esperada do serviço.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="b4fb0-112">Se a identidade esperada e a identidade retornada pelo serviço não corresponderem, a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="b4fb0-113">Negociação de segurança e tempos limite</span><span class="sxs-lookup"><span data-stu-id="b4fb0-113">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="b4fb0-114">Descreve como usar a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Propriedade na <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="b4fb0-115">Depurando erros de autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="b4fb0-115">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="b4fb0-116">Concentra-se em problemas comuns encontrados ao usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="b4fb0-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b4fb0-117">Referência</span><span class="sxs-lookup"><span data-stu-id="b4fb0-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="b4fb0-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b4fb0-118">Related Sections</span></span>  
 [<span data-ttu-id="b4fb0-119">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="b4fb0-119">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4fb0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4fb0-120">See also</span></span>

- [<span data-ttu-id="b4fb0-121">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="b4fb0-121">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b4fb0-122">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b4fb0-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
