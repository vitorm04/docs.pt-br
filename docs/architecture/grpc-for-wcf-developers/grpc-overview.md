---
title: Visão geral do gRPC-gRPC para desenvolvedores do WCF
description: Saiba mais sobre o conjunto de princípios que orienta o desenvolvimento do gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6980b473a6f9852a4e4f396355e98e2d3300cabe
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846651"
---
# <a name="grpc-overview"></a>Visão geral do gRPC

Depois de examinar o Genesis do WCF e do gRPC no último capítulo, este capítulo considerará alguns dos principais recursos do gRPC e como eles se comparam ao WCF.

ASP.NET Core 3,0 é a primeira versão do ASP.NET que dá suporte nativamente ao gRPC como cidadão de primeira classe, com as equipes da Microsoft contribuindo para a implementação oficial do .NET do gRPC. É recomendável como a melhor abordagem para a criação de aplicativos distribuídos com o .NET que podem interoperar com todas as outras linguagens de programação e estruturas principais.

## <a name="key-principles"></a>Principais princípios

Conforme discutido no capítulo 1, o Google queria usar a introdução do HTTP/2 para substituir o Stubby, sua infraestrutura de RPC de uso geral interna. gRPC, com base em Stubby, agora pode aproveitar a padronização e estender sua aplicabilidade à computação móvel, à nuvem e à Internet das Coisas.

Para conseguir isso, a [CNCF (nuvem Native Computing Foundation)](https://www.cncf.io/) estabeleceu um conjunto de princípios que regeria o gRPC. A lista a seguir mostra as mais relevantes, que se preocupam principalmente com a maximização da acessibilidade e usabilidade:

- **Gratuito e aberto** – todos os artefatos devem ser de código aberto com licenciamento que não restrinja os desenvolvedores de adotar o gRPC.
- **Cobertura e simplicidade** – o gRPC deve estar disponível em todas as plataformas populares e simples o suficiente para criar em qualquer plataforma.
- **Interoperabilidade e alcance** – deve ser possível usar o gRPC em qualquer rede, independentemente da largura de banda ou da latência, usando padrões de rede amplamente disponíveis.
- **Uso geral e desempenho** – a estrutura deve ser utilizável por uma ampla gama de casos de uso possível, sem comprometer o desempenho.
- **Streaming** – o protocolo deve fornecer semântica de streaming para grandes conjuntos de dados ou mensagens assíncronas.
- **Troca de metadados** – o protocolo permite que dados não comerciais, como tokens de autenticação, sejam tratados separadamente dos dados corporativos reais.
- **Códigos de status padronizados** – a variabilidade dos códigos de erro deve ser reduzida para tornar as decisões de tratamento de erros mais claras e, em que o tratamento de erros mais avançado é necessário, um mecanismo deve ser fornecido para gerenciar isso na troca de metadados.

>[!div class="step-by-step"]
>[Anterior](introduction.md)
>[Próximo](approach.md)
