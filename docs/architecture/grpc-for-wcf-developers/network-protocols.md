---
title: Protocolos de rede-gRPC para desenvolvedores do WCF
description: Uma visão geral dos protocolos de rede gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 5e837738bd345608ca7119d04c9221acb220c276
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971711"
---
# <a name="network-protocols"></a>Protocolos de rede

Ao contrário do WCF, o gRPC usa HTTP/2 como base para sua rede. Isso oferece vantagens significativas em relação ao WCF e ao SOAP, que operam apenas no HTTP/1.1. Para os desenvolvedores que desejam usar o gRPC, Considerando que não há nenhuma alternativa ao HTTP/2, parece ser o momento ideal para explorar o HTTP/2 mais detalhadamente e identificar benefícios adicionais ao usar o gRPC.

O HTTP/2, lançado pela Internet Engineering Task Force no 2015, foi derivado do protocolo SPDY experimental, que já estava sendo usado pelo Google. Ele foi projetado especificamente para ser mais eficiente, mais rápido e mais seguro do que o HTTP/1.1.

## <a name="key-features-of-http2"></a>Principais recursos do HTTP/2

A lista a seguir mostra alguns dos principais recursos e vantagens do HTTP/2:

### <a name="binary-protocol"></a>Protocolo binário

Os ciclos de solicitação/resposta não precisam mais de comandos de texto. Isso simplifica e acelera a implementação de comandos. Especificamente, a análise de dados é mais rápida e usa menos memória, a latência de rede é reduzida com melhorias de desempenho óbvias em relação à velocidade, e há um melhor uso geral dos recursos de rede.

### <a name="streams"></a>Fluxos

Os fluxos permitem a criação de conexões de longa duração entre o remetente e o destinatário, sobre os quais várias mensagens ou quadros podem ser enviados de forma assíncrona. Vários fluxos podem operar de forma independente em uma única conexão HTTP/2.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Solicitação de multiplexação em uma única conexão TCP

Esse recurso é uma das inovações mais importantes do HTTP/2. Ao permitir várias solicitações paralelas de dados, agora é possível baixar arquivos da Web simultaneamente a partir de um único servidor. Os sites são carregados mais rapidamente e a necessidade de otimização é reduzida. Bloqueio de Head-of-line (Chol), onde as respostas que estão prontas devem aguardar para serem enviadas até que uma solicitação anterior seja concluída, também é atenuada (embora o bloqueio de Chol ainda possa ocorrer no nível de transporte TCP).

### <a name="nettcp-like-performance-cross-platform"></a>Desempenho do tipo NetTCP, plataforma cruzada

Fundamentalmente, a combinação de gRPC e HTTP/2 oferece aos desenvolvedores pelo menos a velocidade equivalente e a eficiência das associações NetTCP para o WCF e, em alguns casos, ainda mais velocidade e eficiência. No entanto, diferentemente do NetTCP, gRPC sobre HTTP/2 não é restrito a aplicativos .NET.

>[!div class="step-by-step"]
>[Anterior](interface-definition-language.md)
>[Próximo](why-grpc.md)
