---
title: Abordagens de arquitetura - Aplicativos sem servidor
description: Uma introdução às abordagens de arquitetura para criar aplicativos corporativos baseados em nuvem, desde arquiteturas n-tier até sem servidor.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522902"
---
# <a name="architecture-approaches"></a>Abordagens de arquitetura

Entender as abordagens existentes para arquitetar aplicativos corporativos ajuda a esclarecer o papel desempenhado por sem servidor. Existem muitas abordagens e padrões que evoluíram ao longo de décadas de desenvolvimento de software, e todos têm seus próprios prós e contras. Em muitos casos, a solução final pode não envolver a decisão de uma única abordagem, mas pode integrar várias abordagens. Os cenários de migração geralmente envolvem a mudança de uma abordagem de arquitetura para outra através de uma abordagem híbrida.

Este capítulo fornece uma visão geral dos padrões de arquitetura lógica e física para aplicativos corporativos.

## <a name="architecture-patterns"></a>Padrões de arquitetura

Aplicações de negócios modernas seguem uma variedade de padrões de arquitetura. Esta seção representa um levantamento de padrões comuns. Os padrões listados aqui não são necessariamente todas as melhores práticas, mas ilustram diferentes abordagens.

Para obter mais informações, consulte [o guia de arquitetura de aplicativos do Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monólitos

Muitas aplicações de negócios seguem um padrão de monólito. Os aplicativos legados são frequentemente implementados como monólitos. No padrão do monólito, todas as preocupações com a aplicação estão contidas em uma única implantação. Tudo, desde a interface do usuário até as chamadas de banco de dados, está incluído na mesma base de código.

![Arquitetura monolito](./media/monolith-architecture.png)

Há várias vantagens para a abordagem do monolito. Muitas vezes é fácil puxar para baixo uma única base de código e começar a trabalhar. O tempo de rampa pode ser menor, e criar ambientes de teste é tão simples quanto fornecer uma nova cópia. O monólito pode ser projetado para incluir vários componentes e aplicações.

Infelizmente, o padrão do monólito tende a quebrar em escala. As principais desvantagens da abordagem do monolito incluem:

- Difícil trabalhar em paralelo na mesma base de código.
- Qualquer mudança, por mais trivial que seja, requer a implantação de uma nova versão de todo o aplicativo.
- A refatoração impacta potencialmente toda a aplicação.
- Muitas vezes, a única solução para escalar é criar cópias múltiplas e intensivas em recursos do monólito.
- À medida que os sistemas se expandem ou outros sistemas são adquiridos, a integração pode ser difícil.
- Pode ser difícil testar devido à necessidade de configurar todo o monólito.
- O reaproveitamento de códigos é desafiador e muitas vezes outros aplicativos acabam tendo suas próprias cópias de código.

Muitas empresas olham para a nuvem como uma oportunidade de migrar aplicativos de monolito e, ao mesmo tempo, refatorá-los para padrões mais utilizáveis. É comum quebrar os aplicativos e componentes individuais para permitir que sejam mantidos, implantados e dimensionados separadamente.

## <a name="n-layer-applications"></a>Aplicativos N-Layer

Lógica do aplicativo de partição de aplicativo de camada n em camadas específicas. As camadas mais comuns incluem:

- Interface do usuário
- Lógica de negócios
- Acesso de dados

Outras camadas podem incluir middleware, processamento de lotes e API. É importante notar que as camadas são lógicas. Embora sejam desenvolvidos isoladamente, podem ser todos implantados na mesma plataforma alvo.

![Arquitetura N-Camada](./media/n-layer-architecture.png)

Existem várias vantagens para a abordagem N-Layer, incluindo:

- A refatoração é isolada a uma camada.
- As equipes podem construir, testar, implantar e manter camadas separadas de forma independente.
- As camadas podem ser trocadas, por exemplo, a camada de dados pode acessar vários bancos de dados sem exigir alterações na camada de IA.

Sem servidor pode ser usado para implementar uma ou mais camadas.

## <a name="microservices"></a>Microsserviços

**[As arquiteturas de microserviços](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** contêm características comuns que incluem:

- As aplicações são compostas por vários pequenos serviços.
- Cada serviço é executado em seu próprio processo.
- Os serviços estão alinhados em torno de domínios de negócios.
- Os serviços se comunicam através de APIs leves, normalmente usando HTTP como transporte.
- Os serviços podem ser implantados e atualizados de forma independente.
- Os serviços não dependem de um único armazenamento de dados.
- O sistema é projetado com falha em mente, e o aplicativo ainda pode ser executado mesmo quando certos serviços falham.

Os microserviços não têm que ser mutuamente exclusivos de outras abordagens de arquitetura. Por exemplo, uma arquitetura N-Tier pode usar microsserviços para o nível intermediário. Também é possível implementar microsserviços de várias maneiras, desde diretórios virtuais em hosts IIS até contêineres. As características dos microserviços os tornam especialmente ideais para implementações sem servidor.

![Arquitetura de microsserviços](./media/microservices-architecture.png)

Os prós das arquiteturas de microsserviços incluem:

- A refatoração é muitas vezes isolada a um único serviço.
- Os serviços podem ser atualizados independentemente uns dos outros.
- A resiliência e a elasticidade podem estar sintonizadas com as demandas dos serviços individuais.
- O desenvolvimento pode acontecer em paralelo entre equipes e plataformas diferentes.
- É mais fácil escrever testes abrangentes para serviços isolados.

Os microserviços vêm com seus próprios desafios, incluindo:

- Determinando quais serviços estão disponíveis e como chamá-los.
- Gerenciando o ciclo de vida dos serviços.
- Entender como os serviços se encaixam na aplicação geral.
- Teste completo do sistema de chamadas feitas em serviços diferentes.

Em última análise, existem soluções para enfrentar todos esses desafios, incluindo aproveitar os benefícios dos sem servidor que são discutidos posteriormente.

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](architecture-deployment-approaches.md)
