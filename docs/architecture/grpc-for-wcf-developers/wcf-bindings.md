---
title: Ligações e transportes WCF - gRPC para desenvolvedores WCF
description: Saiba como as diferentes ligações e transportes wcf se comparam ao gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 3a295268b486578c70c2c98f1d05f89070daaeb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147718"
---
# <a name="wcf-bindings-and-transports"></a>Associações e transportes do WCF

O Windows Communication Foundation (WCF) possui *vinculações incorporadas* que especificam diferentes protocolos de rede, formatos de fio e outros detalhes de implementação. gRPC efetivamente tem apenas um protocolo de rede e um formato de fio. (Tecnicamente, você *pode* personalizar o formato do fio, mas isso está além do escopo deste livro.) É provável que você descubra que o gRPC oferece a melhor solução na maioria dos casos.

O que se segue é uma breve discussão sobre as vinculações mais relevantes do WCF e como elas se comparam aos seus equivalentes no gRPC.

## <a name="nettcp"></a>NetTCP

A vinculação NetTCP do WCF permite conexões persistentes, pequenas mensagens e mensagens bidirecionais. Mas ele funciona apenas entre clientes .NET e servidores. O gRPC permite a mesma funcionalidade, mas é suportado em várias linguagens e plataformas de programação.

o gRPC tem muitas características da vinculação NetTCP do WCF, mas nem sempre são implementados da mesma maneira. Por exemplo, no WCF, a criptografia é controlada através da configuração e tratada na estrutura. No gRPC, a criptografia é alcançada no nível de conexão através de HTTP/2 sobre TLS.

## <a name="http"></a>HTTP

A vinculação WCF chamada BasicHttpBinding é geralmente baseada em texto e usa SOAP como formato de fio. É lento comparado com a ligação NetTCP. Geralmente é usado para fornecer interoperabilidade entre plataformas ou conexão por infra-estrutura de internet.

O equivalente em gRPC usa HTTP/2 como camada de transporte subjacente com o formato binário de fio Protobuf para mensagens. Assim, ele pode oferecer desempenho no nível de serviço NetTCP e interoperabilidade multiplataforma completa com todas as linguagens e frameworks de programação modernas.

## <a name="named-pipes"></a>Pipes nomeados

O WCF forneceu uma ligação *de tubos nomeada* para comunicação entre processos na mesma máquina física. A primeira versão do ASP.NET Core gRPC não suporta tubos nomeados. Adicionar suporte a cliente saques (e soquetes de domínio Unix) é uma meta para uma versão futura.

## <a name="msmq"></a>MSMQ

O MSMQ é uma fila de mensagens proprietária do Windows. A vinculação do WCF ao MSMQ permite solicitações de "fogo e esquecimento" de clientes que podem ser processadas a qualquer momento no futuro. O gRPC não fornece nativamente nenhuma funcionalidade de fila de mensagens.

A melhor alternativa é usar diretamente um sistema de mensagens como Azure Service Bus, RabbitMQ ou Kafka. Você pode implementar isso com o cliente colocando mensagens diretamente na fila, ou um serviço de streaming de clientes gRPC que enfileira as mensagens.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (também conhecido como WCF `WebGet` `WebInvoke` REST), com os atributos e atributos, permitiu que você desenvolvesse APIs RESTful que pudessem falar JSON em um momento em que isso era menos comum. Se você tiver uma API RESTful construída com O WCF REST, considere migrar-a para um aplicativo de API Web MVC de ASP.NET regular. Essa migração forneceria a mesma funcionalidade de uma conversão para gRPC.

>[!div class="step-by-step"]
>[Próximo](wcf-endpoints-grpc-methods.md)
>[anterior](rpc-types.md)
