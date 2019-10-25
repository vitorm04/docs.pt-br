---
title: Associações e transportes do WCF – gRPC para desenvolvedores do WCF
description: Saiba como as diferentes associações e transportes do WCF se comparam ao gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 34321395ddd7059ac7e3c268e313a03251662911
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846049"
---
# <a name="wcf-bindings-and-transports"></a>Associações e transportes do WCF

O WCF tem muitas *associações* internas diferentes que especificam diferentes protocolos de rede, formatos de conexão e outros detalhes de implementação. gRPC efetivamente tem apenas um protocolo de rede e um formato de conexão (tecnicamente, o formato de conexão *pode* ser personalizado, mas isso está além do escopo deste livro). É provável que você descubra que o gRPC oferece a melhor solução na maioria dos casos. O que vem a seguir é uma breve discussão sobre as associações do WCF mais relevantes e como elas se comparam com o equivalente em gRPC.

## <a name="nettcp"></a>NetTCP

A associação NetTCP do WCF permite conexões persistentes, mensagens pequenas e mensagens de duas vias, mas só funciona entre clientes e servidores .NET. o gRPC permite a mesma funcionalidade, mas tem suporte em várias linguagens de programação e plataformas. o gRPC tem muitos dos recursos da associação do WCF NetTCP, embora nem sempre seja implementado da mesma maneira. Por exemplo, no WCF, a criptografia é controlada por meio da configuração e manipulada na estrutura. No gRPC, a criptografia é obtida no nível de conexão usando HTTP/2 em TLS.

## <a name="http"></a>HTTP

BasicHttpBinding do WCF geralmente é baseado em texto, usando SOAP como o formato de conexão e é lento em comparação com a associação NetTCP. Ele é geralmente usado para fornecer interoperabilidade entre plataformas ou conexão pela infra-estrutura da Internet. O equivalente em gRPC — porque ele usa HTTP/2 como a camada de transporte subjacente com o formato de conexão de Protobuf binário para mensagens — pode oferecer desempenho de nível de serviço NetTCP, mas com total interoperabilidade entre plataformas com todas as linguagens de programação modernas e estruturas.

## <a name="named-pipes"></a>Pipes nomeados

O WCF forneceu uma associação de pipes nomeados para comunicação entre processos no mesmo computador físico. Os pipes nomeados não têm suporte na primeira versão do ASP.NET Core gRPC. Adicionar suporte de cliente e servidor para pipes nomeados (e soquetes de domínio do UNIX) é uma meta para uma versão futura.

## <a name="msmq"></a>MSMQ

O MSMQ é uma fila de mensagens do Windows proprietária. A ligação do WCF com o MSMQ permite solicitações "disparar e esquecer" de clientes que podem ser processados a qualquer momento no futuro. o gRPC não fornece uma funcionalidade de fila de mensagens nativamente. A melhor alternativa seria usar diretamente um sistema de mensagens como o barramento de serviço do Azure, RabbitMQ ou Kafka. Isso pode ser implementado com o cliente que está colocando mensagens diretamente na fila ou um serviço de streaming de cliente gRPC que enfileira as mensagens.

## <a name="webhttpbinding"></a>WebHttpBinding

O WebHttpBinding (também conhecido como WCF ReST), com os atributos `WebGet` e `WebInvoke`, permitiu que você desenvolva APIs ReSTful que poderiam falar JSON por vez quando isso fosse menos comum do que agora. Portanto, se você tiver uma API RESTful criada com o WCF REST, considere migrá-la para um aplicativo de API Web do MVC ASP.NET Core regular, que forneceria funcionalidade equivalente, em vez de converter para gRPC.

>[!div class="step-by-step"]
>[Anterior](wcf-endpoints-grpc-methods.md)
>[Próximo](rpc-types.md)
