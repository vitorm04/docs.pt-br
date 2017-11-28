---
title: "Criando meu primeiro aplicativo Web ASP.NET baseado em declarações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: aa25f163199652618e35399c6548a9864a17370a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="3ebb6-102">Criando meu primeiro aplicativo Web ASP.NET baseado em declarações</span><span class="sxs-lookup"><span data-stu-id="3ebb6-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="3ebb6-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="3ebb6-103">Applies To</span></span>  
  
-   <span data-ttu-id="3ebb6-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="3ebb6-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="3ebb6-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3ebb6-105">ASP.NET</span></span>  
  
 <span data-ttu-id="3ebb6-106">Este tópico descreve o cenário da criação de aplicativos Web ASP.NET com reconhecimento de declarações usando o WIF.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="3ebb6-107">Geralmente há três participantes em um cenário de aplicativo com reconhecimento de declarações: o aplicativo em si, o usuário final e o STS (Serviço de Token de Segurança).</span><span class="sxs-lookup"><span data-stu-id="3ebb6-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="3ebb6-108">A figura a seguir descreve esse cenário:</span><span class="sxs-lookup"><span data-stu-id="3ebb6-108">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="3ebb6-109">![Aplicativo Web básico do WIF](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span><span class="sxs-lookup"><span data-stu-id="3ebb6-109">![WIF Basic Web App](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span></span>  
  
1.  <span data-ttu-id="3ebb6-110">O aplicativo com reconhecimento de declarações usa o WIF para identificar solicitações não autenticadas e redirecioná-las ao STS.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2.  <span data-ttu-id="3ebb6-111">O usuário final fornece credenciais ao STS e, após a autenticação bem-sucedida, ele recebe um token do STS.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3.  <span data-ttu-id="3ebb6-112">O usuário é redirecionado do STS ao aplicativo com reconhecimento de declarações com o token emitido pelo STS na solicitação.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4.  <span data-ttu-id="3ebb6-113">O aplicativo com reconhecimento de declarações é configurado para usar o STS e os tokens que ele emite.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="3ebb6-114">O aplicativo com reconhecimento de declarações usa o WIF para validar o token e analisá-lo.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="3ebb6-115">Os desenvolvedores usam a API e os tipos do WIF, por exemplo, **ClaimsPrincpal**, apropriados para as necessidades do aplicativo, como implementar a autorização para ele.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincpal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="3ebb6-116">A partir do .NET 4.5, o WIF faz parte do pacote do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="3ebb6-117">Ter as classes do WIF diretamente disponíveis no Framework permite uma integração muito mais profunda da identidade baseada em declarações no .NET, facilitando o uso de declarações.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="3ebb6-118">Com o WIF 4.5, você não precisa instalar os componentes fora da banda para começar a desenvolver aplicativos Web com reconhecimento de declarações.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="3ebb6-119">As classes WIF agora são difundidas por vários assemblies, sendo os principais System.Security.Claims, System.IdentityModel e System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="3ebb6-120">STS é um serviço que emite tokens após a autenticação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="3ebb6-121">A Microsoft oferece dois STSs padrão do setor:</span><span class="sxs-lookup"><span data-stu-id="3ebb6-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="3ebb6-122">[Serviços de Federação do Active Directory (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="3ebb6-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="3ebb6-123">[ACS (Serviço de Controle de Acesso) do Microsoft Azure](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="3ebb6-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="3ebb6-124">O AD FS 2.0 faz parte do Windows Server R2 e pode ser usado como um STS para cenários locais.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="3ebb6-125">O ACS é um serviço de nuvem oferecido como parte da Plataforma Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="3ebb6-126">Para fins de testes ou educativos, você também pode usar outros STSs para criar seus aplicativos com reconhecimento de reivindicações.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="3ebb6-127">Por exemplo, você pode usar o STS de Desenvolvimento Local que faz parte da [Ferramenta de Identidade e Acesso para o Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849), que está disponível online gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="3ebb6-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="3ebb6-128">Para criar seu primeiro aplicativo ASP.NET com reconhecimento de declarações usando o WIF, siga as instruções em uma destas referências:</span><span class="sxs-lookup"><span data-stu-id="3ebb6-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
-   [<span data-ttu-id="3ebb6-129">Como criar um aplicativo Web ASP.NET MVC com reconhecimento de declarações usando WIF</span><span class="sxs-lookup"><span data-stu-id="3ebb6-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [<span data-ttu-id="3ebb6-130">Como criar um aplicativo Web Forms do ASP.NET com reconhecimento de declarações usando WIF</span><span class="sxs-lookup"><span data-stu-id="3ebb6-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [<span data-ttu-id="3ebb6-131">Como criar um aplicativo ASP.NET com reconhecimento de declarações usando a autenticação baseada em formulários</span><span class="sxs-lookup"><span data-stu-id="3ebb6-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ebb6-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ebb6-132">See Also</span></span>  
 [<span data-ttu-id="3ebb6-133">Introdução ao WIF</span><span class="sxs-lookup"><span data-stu-id="3ebb6-133">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
