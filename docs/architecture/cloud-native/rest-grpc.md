---
title: REST e gRPC
description: Saiba mais sobre o gRPC, sua função em aplicativos nativos de nuvem e como ele difere do HTTP REST
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: 80960a9042b1514fb78e7a8c993a1854067407e8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417130"
---
# <a name="rest-and-grpc"></a>REST e gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Até agora neste livro, nos concentramos na comunicação [baseada em REST](https://docs.microsoft.com/azure/architecture/best-practices/api-design) . O REST é um estilo de arquitetura que promove a interoperabilidade entre sistemas de computadores distribuídos. Ele usa um modelo de solicitação/resposta em que cada resposta do servidor é para uma solicitação do cliente. Embora seja amplamente popular, o REST não é perfeito para cada problema. Uma tecnologia de comunicação mais recente, chamada gRPC, está ganhando popularidade rapidamente e dando seu caminho ao mundo nativo da nuvem.

## <a name="grpc"></a>gRPC

gRPC é uma comunicação de software livre originada no Google. Ele foi criado sobre o modelo de [RPC (chamada de procedimento remoto)](https://en.wikipedia.org/wiki/Remote_procedure_call) , popular em computação distribuída. Após esse modelo, um programa cliente local expõe um método em processo para executar uma operação. Em segundo plano, essa chamada é invocada em um microserviço fora de processo em uma rede distribuída. O desenvolvedor codifica a operação como uma chamada de procedimento local. A plataforma subjacente abstrai a comunicação, a serialização e a execução da rede ponto a ponto.

o gRPC é uma estrutura de RPC moderna que é leve e altamente funcional. Ele usa HTTP/2 para seu protocolo de transporte. Embora seja compatível com HTTP 1,1, o HTTP/2 apresenta muitos recursos avançados:

- Embora HTTP 1,1 envie dados como texto não criptografado, HTTP/2 é um protocolo binário. Ele analisa os dados mais rapidamente usando menos memória, reduz a latência de rede com as melhorias relacionadas à velocidade e gerencia os recursos de rede com mais eficiência.
- Embora o HTTP 1,1 esteja limitado ao processamento de uma solicitação/resposta de ida e volta por vez, o HTTP/2 dá suporte à multiplexação ou a várias solicitações paralelas pela mesma conexão.
- O HTTP/2 dá suporte à comunicação full-duplex ou bidirecional, em que tanto o cliente quanto o servidor podem se comunicar ao mesmo tempo. O cliente pode carregar dados de solicitação ao mesmo tempo em que o servidor está enviando dados de resposta de retorno.
- O streaming é criado no HTTP/2, o que significa que tanto as solicitações quanto as respostas podem transmitir de forma assíncrona grandes conjuntos de dados.
- Combinando gRPC e HTTP/2, o desempenho aumenta drasticamente. Na linguagem [Windows Communication Foundation (WCF)](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) , o desempenho do gRPC atende e excede a velocidade e a eficiência das [associações NetTcp](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8). No entanto, diferentemente do NetTCP, o gRPC não é restrito às C# linguagens da Microsoft, como ou VB.net.

o gRPC tem suporte nas plataformas mais populares, incluindo Java C#,, Golang e NodeJS.

## <a name="protocol-buffers"></a>Buffers de protocolo

o gRPC adota outra tecnologia de software livre chamada [buffers de protocolo](https://developers.google.com/protocol-buffers/docs/overview) ou mensagens Protobuf para enviar e receber dados. Semelhante a um [contrato de dados do WCF](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-data-contracts), o Protobuf serializa dados estruturados para leitura e gravação de sistemas. Ele reduz a sobrecarga de que os formatos legíveis, como XML ou JSON, incorrem.

Muitas técnicas de serialização de objeto refletem na estrutura de objetos de dados em tempo de execução. O Protobuf exige que você defina a estrutura antecipadamente com uma linguagem independente de plataforma (linguagem de buffer de protocolo). Cada definição é armazenada em um arquivo ". proto". Em seguida, usando o compilador Protobuf, "Proton", você gera o código do cliente e do servidor para qualquer uma das plataformas com suporte. O código gerado é otimizado para serialização/desserialização rápida de dados. Em tempo de execução, cada mensagem é encapsulada no contrato de serviço fortemente tipado e serializada em uma representação Protobuf padrão.

## <a name="grpc-support-in-net"></a>suporte do gRPC no .NET

O Microsoft .NET Core Framework 3,0 inclui ferramentas e suporte nativo para gRPC. A Figura 4-20 mostra o modelo do Visual Studio 2019 que aplica Scaffold um projeto de esqueleto gRPC para um serviço gRPC. Observe como o .NET Core dá suporte às plataformas Windows, Linux e macOS.

![Suporte do gRPC no Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Figura 4-20**. suporte do gRPC no Visual Studio 2019

O .NET Core 3,0 integra perfeitamente o gRPC à sua estrutura, incluindo roteamento de ponto de extremidade, suporte interno de IoC e registro em log. O servidor Web Kestrel de software livre dá suporte total a conexões HTTP/2.

A Figura 4-21 mostra a estrutura de um serviço gRPC no Visual Studio 2019. Observe como a estrutura de pastas inclui pastas para os arquivos proto e o código de serviço.

![projeto gRPC no Visual Studio 2019](./media/grpc-project.png  )

**Figura 4-21**. projeto gRPC no Visual Studio 2019

## <a name="grpc-usage"></a>Uso de gRPC

o gRPC é bem adequado para os seguintes cenários:

- Comunicação de baixa latência e alta taxa de transferência. o gRPC é ótimo para microserviços leves em que a eficiência é fundamental.
- Comunicação ponto a ponto em tempo real. o gRPC tem um excelente suporte para streaming bidirecional. os serviços gRPCs podem enviar mensagens em tempo real sem sondagem.
- Ambientes poliglota – as ferramentas de gRPC dão suporte às linguagens de desenvolvimento mais populares, o que o torna uma boa opção para ambientes com vários idiomas.
- Ambientes com restrição de rede – as mensagens gRPC são serializadas com Protobuf, um formato de mensagem leve. Uma mensagem gRPC é sempre menor do que uma mensagem JSON equivalente.

No momento da elaboração deste livro, a maioria dos navegadores tem suporte limitado para gRPC. gRPC usa intensamente recursos HTTP/2 e nenhum navegador fornece o nível de controle necessário em relação a solicitações da Web para dar suporte a um cliente gRPC. gRPC normalmente é usado para a comunicação interna de microserviço com o Microservice. A Figura 4-22 mostra um padrão de uso simples, mas comum.

![Padrões de uso do gRPC](./media/grpc-usage.png)

**Figura 4-22**. padrões de uso do gRPC

Observação na figura anterior como o tráfego de front-end é invocado com HTTP enquanto o microserviço de back-end para o Microservice usa gRPC.

Olhando para a frente, gRPC poderia desempenhar uma função importante no dethroning da predominância do REST para sistemas nativos de nuvem. Os benefícios de desempenho e a facilidade de desenvolvimento são muito bons para se passar. No entanto, não cometa nenhum erro, o REST ainda estará disponível por muito tempo. Ele ainda está em Excel para APIs expostas publicamente e por motivos de compatibilidade com versões anteriores.

>[!div class="step-by-step"]
>[Anterior](service-to-service-communication.md)
>[Próximo](service-mesh-communication-infrastructure.md)
