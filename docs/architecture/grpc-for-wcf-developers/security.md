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
# <a name="security-in-grpc-applications"></a>Segurança em aplicativos gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Em qualquer cenário do mundo real, a proteção de aplicativos e serviços é essencial. A segurança abrange três áreas principais: criptografando o tráfego de rede para impedir que ele seja interceptado por atores ruins; Autenticando clientes e servidores para estabelecer identidade e confiança; e autorizar clientes a controlar o acesso a sistemas e aplicar permissões com base na identidade.

> [!NOTE]
> A **autenticação** se preocupa com o estabelecimento da identidade de um cliente ou servidor. A **autorização** está preocupada com a determinação se um cliente tem permissão para acessar um recurso ou emitir um comando.

Este capítulo abordará as instalações de autenticação e autorização no gRPC para ASP.NET Core e discutirá a segurança de rede usando conexões criptografadas TLS.

## <a name="wcf-authentication-and-authorization"></a>Autenticação e autorização do WCF

No WCF, a autenticação e a autorização foram manipuladas de maneiras diferentes, dependendo dos transportes e das associações que estão sendo usadas. O WCF tem suporte para\* vários padrões WS-Security, bem como a autenticação do Windows para serviços http em execução no IIS ou em serviços NetTcp entre sistemas Windows.

## <a name="grpc-authentication-and-authorization"></a>autenticação e autorização do gRPC

a autenticação e a autorização do gRPC funcionam em dois níveis. A autenticação/autorização em nível de chamada geralmente é manipulada usando tokens que são aplicados nos metadados quando a chamada é feita. A autenticação no nível do canal usa um certificado de cliente que é aplicado no nível de conexão e também pode incluir credenciais de autenticação/autorização em nível de chamada a serem aplicadas a cada chamada no canal automaticamente. Você pode usar um ou ambos os mecanismos para proteger seu serviço.

A implementação de ASP.NET Core do gRPC dá suporte à autenticação e autorização usando a maioria dos mecanismos de ASP.NET Core padrão:

- Chamar autenticação
  - Azure Active Directory
  - IdentityServer
  - Token de portador JWT
  - OAuth 2,0
  - OpenID Connect
  - WS-Federation
- Autenticação de canal
  - Certificado do cliente

Os métodos de autenticação de chamada são todos baseados em *tokens*. A única diferença real é como o token é gerado e as bibliotecas que são usadas para validar os tokens no serviço de ASP.NET Core.

Para obter mais informações, consulte a [documentação de autenticação e autorização em Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).

> [!NOTE]
> Ao usar o gRPC em uma conexão HTTP/2 criptografada por TLS, todo o tráfego entre clientes e servidores é criptografado, mesmo que você não use a autenticação no nível do canal.

Este capítulo mostrará como aplicar credenciais de chamada e credenciais de canal a um serviço gRPC e como usar credenciais de um cliente gRPC do .NET Core para autenticar com o serviço.

>[!div class="step-by-step"]
>[Anterior](client-libraries.md)
>[Próximo](call-credentials.md)
