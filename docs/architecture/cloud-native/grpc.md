---
title: gRPC
description: Saiba mais sobre o gRPC, seu papel em aplicativos nativos da nuvem e como ele difere da comunicação HTTP RESTful.
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 28a07ad5ec105d3fc5b65e4cf0ac0cd85eb16627
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80524169"
---
# <a name="grpc"></a>gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Até agora neste livro, nos concentramos na comunicação baseada em [REST.](https://docs.microsoft.com/azure/architecture/best-practices/api-design) Vimos que rest é um estilo arquitetônico flexível que define operações baseadas em CRUD contra recursos da entidade. Os clientes interagem com recursos em HTTP com um modelo de comunicação de solicitação/resposta. Embora o REST seja amplamente implementado, uma nova tecnologia de comunicação, o gRPC, ganhou um enorme impulso em toda a comunidade nativa da nuvem.

## <a name="what-is-grpc"></a>O que é gRPC?

gRPC é uma estrutura moderna e de alto desempenho que evolui o antigo protocolo de chamada de [procedimento remoto (RPC).](https://en.wikipedia.org/wiki/Remote_procedure_call) No nível de aplicativo, o gRPC simplifica as mensagens entre clientes e serviços back-end. Originário do Google, o gRPC é de código aberto e faz parte do ecossistema de ofertas nativas em nuvem da [Cloud-Native Computing Foundation (CNCF).](https://www.cncf.io/) A CNCF considera o gRPC um [projeto de incubação.](https://github.com/cncf/toc/blob/master/process/graduation_criteria.adoc) Incubar significa que os usuários finais estão usando a tecnologia em aplicações de produção, e o projeto tem um número saudável de colaboradores.

Um aplicativo cliente gRPC típico exporá uma função local em processo que implementa uma operação de negócios. Sob as tampas, essa função local invoca outra função em uma máquina remota. O que parece ser uma chamada local torna-se essencialmente uma chamada fora de processo transparente para um serviço remoto. O encanamento RPC abstrai a comunicação de rede ponto a ponto, serialização e execução entre computadores.

Em aplicativos nativos da nuvem, os desenvolvedores geralmente trabalham em linguagens de programação, frameworks e tecnologias. Essa *interoperabilidade* complica os contratos de mensagens e o encanamento necessário para a comunicação entre plataformas.  o gRPC fornece uma "camada horizontal uniforme" que abstrai essas preocupações. Os desenvolvedores codificam em sua plataforma nativa focada na funcionalidade de negócios, enquanto o gRPC lida com o encanamento de comunicação.

O gRPC oferece suporte abrangente nas pilhas de desenvolvimento mais populares, incluindo Java, JavaScript, C#, Go, Swift e NodeJS.

## <a name="grpc-benefits"></a>Benefícios gRPC

O gRPC usa HTTP/2 para seu protocolo de transporte. Embora compatível com HTTP 1.1, HTTP/2 possui muitos recursos avançados:

- Um protocolo binário para transporte de dados - ao contrário do HTTP 1.1, que envia dados como texto claro.
- Multiplear o suporte para enviar várias solicitações paralelas sobre a mesma conexão - HTTP 1.1 limita o processamento a uma mensagem de solicitação/resposta por vez.
- Comunicação bidirecional full-duplex para enviar solicitações de clientes e respostas do servidor simultaneamente.
- Streaming integrado que permite solicitações e respostas para transmitir de forma assíncrona grandes conjuntos de dados.

gRPC é leve e de alto desempenho. Pode ser até 8x mais rápido que a serialização JSON com mensagens 60-80% menores. Na linguagem da Microsoft [Windows Communication Foundation (WCF),](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) o desempenho gRPC excede a velocidade e a eficiência das [ligações NetTCP](https://docs.microsoft.com/dotnet/api/system.servicemodel.nettcpbinding?view=netframework-4.8)altamente otimizadas. Ao contrário do NetTCP, que favorece a pilha da Microsoft, o gRPC é multiplataforma.

## <a name="protocol-buffers"></a>Buffers de protocolo

O gRPC adota uma tecnologia de código aberto chamada [Buffers de Protocolo](https://developers.google.com/protocol-buffers/docs/overview). Eles fornecem um formato de serialização altamente eficiente e neutro em plataforma para serializar mensagens estruturadas que os serviços enviam entre si. Usando um IDL (Interface Definition Language, linguagem de definição de interface multiplataforma), os desenvolvedores definem um contrato de serviço para cada microserviço. O contrato, implementado como `.proto` um arquivo baseado em texto, descreve os métodos, entradas e saídas de cada serviço. O mesmo arquivo de contrato pode ser usado para clientes e serviços gRPC construídos em diferentes plataformas de desenvolvimento.

Usando o arquivo proto, o compilador `protoc`Protobuf, gera código de cliente e serviço para sua plataforma de destino. O código inclui os seguintes componentes:

- Objetos fortemente digitados, compartilhados pelo cliente e pelo serviço, que representam as operações de serviço e os elementos de dados para uma mensagem.
- Uma classe base fortemente digitada com o encanamento de rede necessário que o serviço gRPC remoto pode herdar e estender.
- Um stub de cliente que contém o encanamento necessário para invocar o serviço gRPC remoto.

Em tempo de execução, cada mensagem é serializada como uma representação Protobuf padrão e trocada entre o cliente e o serviço remoto. Ao contrário de JSON ou XML, as mensagens Protobuf são serializadas como bytes binários compilados.

O livro, [gRPC for WCF Developers](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/), disponível no site da Microsoft Architecture, fornece uma cobertura aprofundada de gRPC e Buffers de Protocolo.

## <a name="grpc-support-in-net"></a>suporte gRPC em .NET

O gRPC é integrado ao .NET Core 3.0 SDK ou posterior. As seguintes ferramentas o suportam:

- Visual Studio 2019, versão 16.3 ou posterior, com a carga de trabalho de desenvolvimento web instalada.
- Visual Studio Code
- o CLI dotnet

O SDK inclui ferramentas para roteamento de ponto final, IoC incorporado e registro. O servidor web Kestrel de código aberto suporta conexões HTTP/2. A Figura 4-20 mostra um modelo visual studio 2019 que andaimes um projeto esqueleto para um serviço gRPC. Observe como o .NET Core suporta totalmente o Windows, Linux e macOS.

![Suporte gRPC no Visual Studio 2019](./media/visual-studio-2019-grpc-template.png)

**Figura 4-20**. suporte a gRPC no Visual Studio 2019
  
A Figura 4-21 mostra o serviço gRPC esqueleto gerado a partir dos andaimes embutidos incluídos no Visual Studio 2019.  

![projeto gRPC no Visual Studio 2019](./media/grpc-project.png  )

**Figura 4-21**. projeto gRPC no Visual Studio 2019

Na figura anterior, observe o arquivo de descrição do proto e o código de serviço. Como você verá em breve, o Visual Studio gera configuração adicional tanto na classe Startup quanto no arquivo de projeto subjacente.

## <a name="grpc-usage"></a>uso de gRPC

Favor e gRPC para os seguintes cenários:

- Comunicação de microserviço de back-end síncrono onde uma resposta imediata é necessária para continuar o processamento.
- Ambientes poliglotas que precisam suportar plataformas de programação mista.
- Baixa latência e comunicação de alto rendimento onde o desempenho é crítico.
- Comunicação ponto a ponto em tempo real - o gRPC pode enviar mensagens em tempo real sem votação e tem excelente suporte para streaming bidirecional.
- Ambientes limitados à rede – as mensagens binárias gRPC são sempre menores do que uma mensagem JSON baseada em texto equivalente.

No momento, desta redação, o gRPC é usado principalmente com serviços back-end. A maioria dos navegadores modernos não pode fornecer o nível de controle HTTP/2 necessário para suportar um cliente gRPC front-end. Dito isto, há uma [iniciativa inicial](https://devblogs.microsoft.com/aspnet/grpc-web-experiment/) que permite a comunicação gRPC a partir de aplicativos baseados em navegador construídos com as tecnologias JavaScript ou Blazor WebAssembly. O [gRPC-Web para .NET](https://github.com/grpc/grpc/blob/master/doc/PROTOCOL-WEB.md) permite que um aplicativo gRPC ASP.NET Core suporte recursos gRPC em aplicativos de navegador:

- Clientes fortemente digitados gerados por código
- Mensagens compactas do Protobuf
- Streaming de servidor

## <a name="grpc-implementation"></a>implementação do gRPC

A arquitetura de referência de microserviço, [eShop on Containers](https://github.com/dotnet-architecture/eShopOnContainers), da Microsoft, mostra como implementar serviços gRPC em aplicativos .NET Core. A Figura 4-22 apresenta a arquitetura back-end.

![Arquitetura backend para eShop em Containers](./media/eshop-with-aggregators.png)

**Figura 4-22**. Arquitetura backend para eShop em Containers

Na figura anterior, observe como o eShop adota o [padrão Backend for Frontends](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) (BFF) expondo vários gateways de API. Discutimos o padrão BFF no início deste capítulo. Preste muita atenção ao microserviço Agregador (em cinza) que fica entre o Gateway de API de Compras Web e os microsserviços back-end Shopping. O Agregador recebe uma única solicitação de um cliente, despacha-a para vários microsserviços, agrega os resultados e os envia de volta ao cliente solicitante. Tais operações normalmente requerem comunicação síncrona para produzir uma resposta imediata. No eShop, as chamadas de back-end do Agregador são realizadas usando gRPC, conforme mostrado na Figura 4-23.

![gRPC em eShop em Containers](./media/grpc-implementation.png)

**Figura 4-23**. gRPC em eShop em Containers

A comunicação gRPC requer componentes do cliente e do servidor. Na figura anterior, observe como o Agregador de Compras implementa um cliente gRPC. O cliente faz chamadas síncronas de gRPC (em vermelho) para microsserviços back-end, cada um dos quais implementa um servidor gRPC. Tanto o cliente quanto o servidor aproveitam o encanamento gRPC incorporado do SDK .NET Core 3.0. Os *stubs do* lado do cliente fornecem o encanamento para invocar chamadas gRPC remotas. Os componentes do lado do servidor fornecem encanamento gRPC que as classes de serviço personalizadas podem herdar e consumir.

Microserviços que expõem uma API RESTful e uma comunicação gRPC exigem vários pontos finais para gerenciar o tráfego. Você abriria um ponto final que escuta o tráfego HTTP para as chamadas RESTful e outro para chamadas gRPC. O ponto final gRPC deve ser configurado para o protocolo HTTP/2 necessário para a comunicação gRPC.

Enquanto nos esforçamos para desacoplar microsserviços com padrões de comunicação assíncronos, algumas operações exigem chamadas diretas. o gRPC deve ser a principal escolha para a comunicação síncrona direta entre microserviços. Seu protocolo de comunicação de alto desempenho, baseado em HTTP/2 e buffers de protocolo, o torna uma escolha perfeita.

## <a name="looking-ahead"></a>Olhando para o futuro

Olhando para o futuro, o gRPC continuará a ganhar tração para sistemas nativos da nuvem. Os benefícios de desempenho e a facilidade de desenvolvimento são convincentes. No entanto, rest provavelmente vai estar por perto por um longo tempo. Ele se destaca por APIs expostas publicamente e por razões de compatibilidade retrógrada.

>[!div class="step-by-step"]
>[Próximo](service-to-service-communication.md)
>[anterior](service-mesh-communication-infrastructure.md)
