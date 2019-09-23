---
title: Segurança em aplicativos gRPC – gRPC para desenvolvedores do WCF
description: Visão geral de autenticação e autorização de canal e chamada no gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184137"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="dc47e-103">Segurança em aplicativos gRPC</span><span class="sxs-lookup"><span data-stu-id="dc47e-103">Security in gRPC applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="dc47e-104">Em qualquer cenário do mundo real, a proteção de aplicativos e serviços é essencial.</span><span class="sxs-lookup"><span data-stu-id="dc47e-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="dc47e-105">A segurança abrange três áreas principais: criptografando o tráfego de rede para impedir que ele seja interceptado por atores ruins; Autenticando clientes e servidores para estabelecer identidade e confiança; e autorizar clientes a controlar o acesso a sistemas e aplicar permissões com base na identidade.</span><span class="sxs-lookup"><span data-stu-id="dc47e-105">Security covers three key areas: encrypting network traffic to prevent it from being intercepted by bad actors; authenticating clients and servers to establish identity and trust; and authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="dc47e-106">A **autenticação** se preocupa com o estabelecimento da identidade de um cliente ou servidor.</span><span class="sxs-lookup"><span data-stu-id="dc47e-106">**Authentication** is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="dc47e-107">A **autorização** está preocupada com a determinação se um cliente tem permissão para acessar um recurso ou emitir um comando.</span><span class="sxs-lookup"><span data-stu-id="dc47e-107">**Authorization** is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="dc47e-108">Este capítulo abordará as instalações de autenticação e autorização no gRPC para ASP.NET Core e discutirá a segurança de rede usando conexões criptografadas TLS.</span><span class="sxs-lookup"><span data-stu-id="dc47e-108">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core, and discuss network security using TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="dc47e-109">Autenticação e autorização do WCF</span><span class="sxs-lookup"><span data-stu-id="dc47e-109">WCF authentication and authorization</span></span>

<span data-ttu-id="dc47e-110">No WCF, a autenticação e a autorização foram manipuladas de maneiras diferentes, dependendo dos transportes e das associações que estão sendo usadas.</span><span class="sxs-lookup"><span data-stu-id="dc47e-110">In WCF, authentication and authorization were handled in different ways depending on the transports and bindings being used.</span></span> <span data-ttu-id="dc47e-111">O WCF tem suporte para\* vários padrões WS-Security, bem como a autenticação do Windows para serviços http em execução no IIS ou em serviços NetTcp entre sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="dc47e-111">WCF supported various WS-\* security standards, as well as Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="dc47e-112">autenticação e autorização do gRPC</span><span class="sxs-lookup"><span data-stu-id="dc47e-112">gRPC authentication and authorization</span></span>

<span data-ttu-id="dc47e-113">a autenticação e a autorização do gRPC funcionam em dois níveis.</span><span class="sxs-lookup"><span data-stu-id="dc47e-113">gRPC authentication and authorization works on two levels.</span></span> <span data-ttu-id="dc47e-114">A autenticação/autorização em nível de chamada geralmente é manipulada usando tokens que são aplicados nos metadados quando a chamada é feita.</span><span class="sxs-lookup"><span data-stu-id="dc47e-114">Call-level authentication/authorization is usually handled using tokens that are applied in metadata when the call is made.</span></span> <span data-ttu-id="dc47e-115">A autenticação no nível do canal usa um certificado de cliente que é aplicado no nível de conexão e também pode incluir credenciais de autenticação/autorização em nível de chamada a serem aplicadas a cada chamada no canal automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dc47e-115">Channel-level authentication uses a client certificate that is applied at the connection level, and can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> <span data-ttu-id="dc47e-116">Você pode usar um ou ambos os mecanismos para proteger seu serviço.</span><span class="sxs-lookup"><span data-stu-id="dc47e-116">You can use either or both of these mechanisms to secure your service.</span></span>

<span data-ttu-id="dc47e-117">A implementação de ASP.NET Core do gRPC dá suporte à autenticação e autorização usando a maioria dos mecanismos de ASP.NET Core padrão:</span><span class="sxs-lookup"><span data-stu-id="dc47e-117">The ASP.NET Core implementation of gRPC supports authentication and authorization using most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="dc47e-118">Chamar autenticação</span><span class="sxs-lookup"><span data-stu-id="dc47e-118">Call authentication</span></span>
  - <span data-ttu-id="dc47e-119">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="dc47e-119">Azure Active Directory</span></span>
  - <span data-ttu-id="dc47e-120">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="dc47e-120">IdentityServer</span></span>
  - <span data-ttu-id="dc47e-121">Token de portador JWT</span><span class="sxs-lookup"><span data-stu-id="dc47e-121">JWT Bearer Token</span></span>
  - <span data-ttu-id="dc47e-122">OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="dc47e-122">OAuth 2.0</span></span>
  - <span data-ttu-id="dc47e-123">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="dc47e-123">OpenID Connect</span></span>
  - <span data-ttu-id="dc47e-124">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="dc47e-124">WS-Federation</span></span>
- <span data-ttu-id="dc47e-125">Autenticação de canal</span><span class="sxs-lookup"><span data-stu-id="dc47e-125">Channel authentication</span></span>
  - <span data-ttu-id="dc47e-126">Certificado do cliente</span><span class="sxs-lookup"><span data-stu-id="dc47e-126">Client Certificate</span></span>

<span data-ttu-id="dc47e-127">Os métodos de autenticação de chamada são todos baseados em *tokens*.</span><span class="sxs-lookup"><span data-stu-id="dc47e-127">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="dc47e-128">A única diferença real é como o token é gerado e as bibliotecas que são usadas para validar os tokens no serviço de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc47e-128">The only real difference is how the token is generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="dc47e-129">Para obter mais informações, consulte a [documentação de autenticação e autorização em Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="dc47e-129">For more information, see the [Authentication and authorization documentation on Microsoft Docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span></span>

> [!NOTE]
> <span data-ttu-id="dc47e-130">Ao usar o gRPC em uma conexão HTTP/2 criptografada por TLS, todo o tráfego entre clientes e servidores é criptografado, mesmo que você não use a autenticação no nível do canal.</span><span class="sxs-lookup"><span data-stu-id="dc47e-130">When using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="dc47e-131">Este capítulo mostrará como aplicar credenciais de chamada e credenciais de canal a um serviço gRPC e como usar credenciais de um cliente gRPC do .NET Core para autenticar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="dc47e-131">This chapter will show how to apply call credentials and channel credentials to a gRPC service, and how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dc47e-132">[Anterior](client-libraries.md)
>[Próximo](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="dc47e-132">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
