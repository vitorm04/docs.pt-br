---
title: Protocolos WS-*-gRPC para desenvolvedores do WCF
description: Revisão dos protocolos WS-* com suporte do WCF e das alternativas disponíveis com o gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4e7b80df182fb69cc51e14738e59ad87efaf5dd2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846038"
---
# <a name="ws--protocols"></a>Protocolos WS-\*

Um dos verdadeiros benefícios de trabalhar com o Windows Communication Foundation (WCF) era que ele oferecia suporte a muitos dos protocolos padrão _WS-\*_ existentes. Esta seção abordará brevemente como o gRPC gerencia os mesmos protocolos WS-\* e discutirá quais opções estão disponíveis quando não houver nenhuma alternativa.

## <a name="metadata-exchange---ws-policy-ws-discovery-and-so-on"></a>Metadados Exchange-WS-Policy, WS-Discovery e assim por diante

Os serviços SOAP expõem documentos de esquema WSDL (linguagem de descrição de serviços Web) com informações como formatos de dados, operações ou opções de comunicação. Esse esquema pode ser usado para gerar o código do cliente.

o gRPC funciona melhor quando servidores e clientes são gerados a partir dos mesmos arquivos de `.proto`, mas uma extensão opcional de reflexão de servidor fornece uma maneira de expor informações dinâmicas de um servidor em execução. Para obter mais informações, consulte o pacote NuGet [Grpc. Reflection](https://nuget.org/packages/Grpc.Reflection) e o artigo de [reflexão do C# servidor Grpc](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

O protocolo WS-Discovery é usado para localizar serviços em uma rede local. os serviços gRPCs geralmente estão localizados usando DNS ou um registro de serviço, como Consul ou ZooKeeper.

## <a name="security--ws-security-ws-federation-xml-encryption-and-so-on"></a>Segurança – WS-Security, WS-Federation, criptografia XML e assim por diante

A segurança, a autenticação e a autorização são abordadas com muito mais detalhes no [capítulo 6](security.md). Mas vale a pena observar que, ao contrário do WCF, o gRPC não dá suporte a WS-Security, WS Federation ou criptografia XML. Mesmo assim, o gRPC fornece excelente segurança; todo o tráfego de rede gRPC é criptografado automaticamente ao usar HTTP/2 por TLS, e certificados X509 podem ser usados para autenticação mútua de cliente/servidor.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC não fornece um equivalente a WS-ReliableMessaging. A semântica de repetição deve ser tratada no código, possivelmente com uma biblioteca como [Polly](https://github.com/App-vNext/Polly). Ao executar em ambientes de orquestração kubernetes ou similares, as [malhas de serviço](service-mesh.md) também podem ajudar a fornecer mensagens confiáveis entre serviços.

## <a name="ws-transaction-ws-coordination"></a>WS-Transaction, WS-Coordination

A implementação do WCF de transações distribuídas usa o Windows ' Microsoft Coordenador de Transações Distribuídas ou o MSDTC. Ele funciona com gerenciadores de recursos que dão suporte especificamente a ele, como SQL Server, MSMQ ou sistemas de arquivos do Windows. No mundo de microserviços modernos, em parte devido à maior variedade de tecnologias em uso, ainda não há nenhum equivalente. Para obter uma discussão sobre transações, consulte [o apêndice a](appendix.md).

>[!div class="step-by-step"]
>[Anterior](error-handling.md)
>[Próximo](migrate-wcf-to-grpc.md)
