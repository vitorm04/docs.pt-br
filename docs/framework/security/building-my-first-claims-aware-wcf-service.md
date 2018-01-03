---
title: "Criando meu primeiro serviço WCF baseado em declarações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: af39c3c5788db95eaee248ca8454534022cab659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="building-my-first-claims-aware-wcf-service"></a><span data-ttu-id="02714-102">Criando meu primeiro serviço WCF baseado em declarações</span><span class="sxs-lookup"><span data-stu-id="02714-102">Building My First Claims-Aware WCF Service</span></span>
## <a name="applies-to"></a><span data-ttu-id="02714-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="02714-103">Applies To</span></span>  
  
-   <span data-ttu-id="02714-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="02714-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="02714-105">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="02714-105">Windows Communication Foundation (WCF)</span></span>  
  
## <a name="overview"></a><span data-ttu-id="02714-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="02714-106">Overview</span></span>  
 <span data-ttu-id="02714-107">Este tópico descreve o cenário da criação de serviços WCF com reconhecimento de declarações usando o WIF.</span><span class="sxs-lookup"><span data-stu-id="02714-107">This topic outlines the scenario of building claims-aware WCF services using WIF.</span></span> <span data-ttu-id="02714-108">Geralmente há três participantes em um cenário de serviço Web com reconhecimento de declarações: o serviço Web em si, o usuário final e o STS (Serviço de Token de Segurança).</span><span class="sxs-lookup"><span data-stu-id="02714-108">There are usually three participants in a claims-aware web service scenario: the web service itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="02714-109">A figura a seguir descreve esse cenário:</span><span class="sxs-lookup"><span data-stu-id="02714-109">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="02714-110">![Serviço WCF básico baseado em declarações do WIF](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span><span class="sxs-lookup"><span data-stu-id="02714-110">![WIF Basic Claims Aware WCF Service](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span></span>  
  
1.  <span data-ttu-id="02714-111">O cliente do serviço WCF (às vezes chamado de agente) usa o WIF para enviar credenciais ao STS e, após a autenticação bem-sucedida, o agente receberá um token do STS.</span><span class="sxs-lookup"><span data-stu-id="02714-111">The WCF service client (sometimes called agent) uses WIF to send credentials to the STS and upon successful authentication, the agent is issued a token by the STS.</span></span>  
  
2.  <span data-ttu-id="02714-112">O agente envia esse token emitido pelo STS para o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="02714-112">The agent sends this STS-issued token to the WCF service.</span></span>  
  
3.  <span data-ttu-id="02714-113">O serviço WCF com reconhecimento de declarações é configurado para usar o STS e os tokens que ele emite.</span><span class="sxs-lookup"><span data-stu-id="02714-113">The claims-aware WCF service is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="02714-114">O serviço WCF com reconhecimento de declarações usa o WIF para validar o token e analisá-lo.</span><span class="sxs-lookup"><span data-stu-id="02714-114">The claims-aware WCF service uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="02714-115">Os desenvolvedores usam a API e os tipos do WIF, por exemplo, **ClaimsPrincipal**, apropriados para as necessidades do aplicativo, como implementar a autorização para ele.</span><span class="sxs-lookup"><span data-stu-id="02714-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="02714-116">A partir do .NET 4.5, o WIF faz parte do pacote do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02714-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="02714-117">Ter as classes do WIF diretamente disponíveis no Framework permite uma integração muito mais profunda da identidade baseada em declarações no .NET, facilitando o uso de declarações.</span><span class="sxs-lookup"><span data-stu-id="02714-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="02714-118">Com o WIF 4.5, você não precisa instalar os componentes fora da banda para começar a desenvolver aplicativos Web com reconhecimento de declarações.</span><span class="sxs-lookup"><span data-stu-id="02714-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="02714-119">As classes WIF agora são difundidas por vários assemblies, sendo os principais System.Security.Claims, System.IdentityModel e System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="02714-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="02714-120">STS é um serviço que emite tokens após a autenticação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="02714-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="02714-121">A Microsoft oferece dois STSs padrão do setor:</span><span class="sxs-lookup"><span data-stu-id="02714-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="02714-122">[Serviços de Federação do Active Directory (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="02714-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="02714-123">[ACS (Serviço de Controle de Acesso) do Microsoft Azure](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="02714-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="02714-124">O AD FS 2.0 faz parte do Windows Server R2 e pode ser usado como um STS para cenários locais.</span><span class="sxs-lookup"><span data-stu-id="02714-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="02714-125">O Controle de Acesso do Azure Active Directory (também conhecido como Serviço de Controle de Acesso ou ACS) é um serviço de nuvem, oferecido como parte do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="02714-125">Azure Active Directory Access Control (also known as Access Control Service or ACS) is a cloud service, offered as part of Microsoft Azure.</span></span> <span data-ttu-id="02714-126">Para fins de testes ou educativos, você também pode usar outros STSs para criar seus aplicativos com reconhecimento de reivindicações.</span><span class="sxs-lookup"><span data-stu-id="02714-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="02714-127">Por exemplo, você pode usar o STS de Desenvolvimento Local que faz parte da [Ferramenta de Identidade e Acesso para o Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849), que está disponível online gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="02714-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="02714-128">Para criar seu primeiro serviço WCF baseado em declarações usando o WIF, consulte [Como criar um serviço WCF baseado em declarações usando o WIF](http://msdn.microsoft.com/en-us/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span><span class="sxs-lookup"><span data-stu-id="02714-128">To build your first claims-aware WCF service using WIF, see [How To: Build Claims-Aware WCF Service Using WIF](http://msdn.microsoft.com/en-us/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02714-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02714-129">See Also</span></span>  
 [<span data-ttu-id="02714-130">Introdução ao WIF</span><span class="sxs-lookup"><span data-stu-id="02714-130">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
