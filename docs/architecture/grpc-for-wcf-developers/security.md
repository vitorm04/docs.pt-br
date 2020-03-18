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
# <a name="security-in-grpc-applications"></a>Segurança em aplicativos gRPC

Em qualquer cenário do mundo real, garantir aplicações e serviços é essencial. A segurança abrange três áreas-chave:

* Criptografando o tráfego da rede para evitar que hackers mal-intencionados o interceptem.
* Autenticação de clientes e servidores para estabelecer identidade e confiança.
* Autorizando os clientes a controlar o acesso aos sistemas e aplicar permissões com base na identidade.

> [!NOTE]
> *A autenticação* está preocupada em estabelecer a identidade de um cliente ou servidor. *A autorização* está preocupada em determinar se um cliente tem permissão para acessar um recurso ou emitir um comando.

Este capítulo abrangerá as facilidades para autenticação e autorização no gRPC para ASP.NET Core. Também discutirá a segurança da rede através de conexões criptografadas TLS.

## <a name="wcf-authentication-and-authorization"></a>Autenticação e autorização do WCF

Na Windows Communication Foundation (WCF), a autenticação e a autorização foram tratadas de diferentes formas, dependendo dos transportes e ligações que estão sendo utilizados. O WCF apoiou vários\* padrões de segurança WS. Ele também suportava a autenticação do Windows para serviços HTTP em execução em serviços IIS ou NetTCP entre sistemas Windows.

## <a name="grpc-authentication-and-authorization"></a>autenticação e autorização gRPC

A autenticação e a autorização do gRPC funcionam em dois níveis:

* A autenticação/autorização de nível de chamada geralmente é tratada através de tokens que são aplicados em metadados quando a chamada é feita.
* A autenticação em nível de canal usa um certificado de cliente aplicado no nível de conexão. Ele também pode incluir credenciais de autenticação/autorização de nível de chamada a serem aplicadas automaticamente a cada chamada no canal.

Você pode usar ambos ou ambos os mecanismos para ajudar a proteger o seu serviço.

A implementação do Núcleo ASP.NET do gRPC suporta autenticação e autorização através da maioria dos mecanismos padrão ASP.NET Core:

- Autenticação de chamadas
  - Azure Active Directory
  - Servidor de identidade
  - Token do Portador JWT
  - OAuth 2.0
  - OpenID Connect
  - O certificado do provedor de identidade do Web Services Federation
- Autenticação de canal
  - Certificado do cliente

Os métodos de autenticação de chamadas são todos *baseados em tokens*. A única diferença real é como os tokens são gerados e as bibliotecas que são usadas para validar os tokens no serviço ASP.NET Core.

Para obter mais informações, consulte o artigo [autenticação e autorização.](/aspnet/core/grpc/authn-and-authz)

> [!NOTE]
> Quando você está usando gRPC através de uma conexão HTTP/2 criptografada por TLS, todo o tráfego entre clientes e servidores é criptografado, mesmo que você não use autenticação em nível de canal.

Este capítulo mostrará como aplicar credenciais de chamada e credenciais de canal a um serviço gRPC. Ele também mostrará como usar credenciais de um cliente gRPC .NET Core para autenticar com o serviço.

>[!div class="step-by-step"]
>[Próximo](client-libraries.md)
>[anterior](call-credentials.md)
