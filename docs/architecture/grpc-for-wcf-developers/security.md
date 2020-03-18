---
title: Segurança em aplicativos gRPC - gRPC para desenvolvedores WCF
description: Visão geral da autenticação e autorização de chamadas e canais no gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147809"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="0c047-103">Segurança em aplicativos gRPC</span><span class="sxs-lookup"><span data-stu-id="0c047-103">Security in gRPC applications</span></span>

<span data-ttu-id="0c047-104">Em qualquer cenário do mundo real, garantir aplicações e serviços é essencial.</span><span class="sxs-lookup"><span data-stu-id="0c047-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="0c047-105">A segurança abrange três áreas-chave:</span><span class="sxs-lookup"><span data-stu-id="0c047-105">Security covers three key areas:</span></span>

* <span data-ttu-id="0c047-106">Criptografando o tráfego da rede para evitar que hackers mal-intencionados o interceptem.</span><span class="sxs-lookup"><span data-stu-id="0c047-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="0c047-107">Autenticação de clientes e servidores para estabelecer identidade e confiança.</span><span class="sxs-lookup"><span data-stu-id="0c047-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="0c047-108">Autorizando os clientes a controlar o acesso aos sistemas e aplicar permissões com base na identidade.</span><span class="sxs-lookup"><span data-stu-id="0c047-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="0c047-109">*A autenticação* está preocupada em estabelecer a identidade de um cliente ou servidor.</span><span class="sxs-lookup"><span data-stu-id="0c047-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="0c047-110">*A autorização* está preocupada em determinar se um cliente tem permissão para acessar um recurso ou emitir um comando.</span><span class="sxs-lookup"><span data-stu-id="0c047-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="0c047-111">Este capítulo abrangerá as facilidades para autenticação e autorização no gRPC para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c047-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="0c047-112">Também discutirá a segurança da rede através de conexões criptografadas TLS.</span><span class="sxs-lookup"><span data-stu-id="0c047-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="0c047-113">Autenticação e autorização do WCF</span><span class="sxs-lookup"><span data-stu-id="0c047-113">WCF authentication and authorization</span></span>

<span data-ttu-id="0c047-114">Na Windows Communication Foundation (WCF), a autenticação e a autorização foram tratadas de diferentes formas, dependendo dos transportes e ligações que estão sendo utilizados.</span><span class="sxs-lookup"><span data-stu-id="0c047-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="0c047-115">O WCF apoiou vários\* padrões de segurança WS.</span><span class="sxs-lookup"><span data-stu-id="0c047-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="0c047-116">Ele também suportava a autenticação do Windows para serviços HTTP em execução em serviços IIS ou NetTCP entre sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="0c047-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="0c047-117">autenticação e autorização gRPC</span><span class="sxs-lookup"><span data-stu-id="0c047-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="0c047-118">A autenticação e a autorização do gRPC funcionam em dois níveis:</span><span class="sxs-lookup"><span data-stu-id="0c047-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="0c047-119">A autenticação/autorização de nível de chamada geralmente é tratada através de tokens que são aplicados em metadados quando a chamada é feita.</span><span class="sxs-lookup"><span data-stu-id="0c047-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="0c047-120">A autenticação em nível de canal usa um certificado de cliente aplicado no nível de conexão.</span><span class="sxs-lookup"><span data-stu-id="0c047-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="0c047-121">Ele também pode incluir credenciais de autenticação/autorização de nível de chamada a serem aplicadas automaticamente a cada chamada no canal.</span><span class="sxs-lookup"><span data-stu-id="0c047-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="0c047-122">Você pode usar ambos ou ambos os mecanismos para ajudar a proteger o seu serviço.</span><span class="sxs-lookup"><span data-stu-id="0c047-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="0c047-123">A implementação do Núcleo ASP.NET do gRPC suporta autenticação e autorização através da maioria dos mecanismos padrão ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="0c047-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="0c047-124">Autenticação de chamadas</span><span class="sxs-lookup"><span data-stu-id="0c047-124">Call authentication</span></span>
  - <span data-ttu-id="0c047-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="0c047-125">Azure Active Directory</span></span>
  - <span data-ttu-id="0c047-126">Servidor de identidade</span><span class="sxs-lookup"><span data-stu-id="0c047-126">IdentityServer</span></span>
  - <span data-ttu-id="0c047-127">Token do Portador JWT</span><span class="sxs-lookup"><span data-stu-id="0c047-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="0c047-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="0c047-128">OAuth 2.0</span></span>
  - <span data-ttu-id="0c047-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="0c047-129">OpenID Connect</span></span>
  - <span data-ttu-id="0c047-130">O certificado do provedor de identidade do Web Services Federation</span><span class="sxs-lookup"><span data-stu-id="0c047-130">WS-Federation</span></span>
- <span data-ttu-id="0c047-131">Autenticação de canal</span><span class="sxs-lookup"><span data-stu-id="0c047-131">Channel authentication</span></span>
  - <span data-ttu-id="0c047-132">Certificado do cliente</span><span class="sxs-lookup"><span data-stu-id="0c047-132">Client certificate</span></span>

<span data-ttu-id="0c047-133">Os métodos de autenticação de chamadas são todos *baseados em tokens*.</span><span class="sxs-lookup"><span data-stu-id="0c047-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="0c047-134">A única diferença real é como os tokens são gerados e as bibliotecas que são usadas para validar os tokens no serviço ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c047-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="0c047-135">Para obter mais informações, consulte o artigo [autenticação e autorização.](/aspnet/core/grpc/authn-and-authz)</span><span class="sxs-lookup"><span data-stu-id="0c047-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="0c047-136">Quando você está usando gRPC através de uma conexão HTTP/2 criptografada por TLS, todo o tráfego entre clientes e servidores é criptografado, mesmo que você não use autenticação em nível de canal.</span><span class="sxs-lookup"><span data-stu-id="0c047-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="0c047-137">Este capítulo mostrará como aplicar credenciais de chamada e credenciais de canal a um serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="0c047-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="0c047-138">Ele também mostrará como usar credenciais de um cliente gRPC .NET Core para autenticar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="0c047-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0c047-139">[Próximo](client-libraries.md)
>[anterior](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="0c047-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
