---
title: Abordagens de arquitetura - aplicativos sem servidor
description: Uma introdução à arquitetura de abordagens para criar aplicativos corporativos baseados em nuvem, de arquiteturas de N camadas sem servidor.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 21e191f17e7d0b4f2d64454fb14c46a4831a8375
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "49369667"
---
# <a name="architecture-approaches"></a>Abordagens de arquitetura

Noções básicas sobre as abordagens existentes para arquitetar aplicativos empresariais ajuda a esclarecer o papel desempenhado sem servidor. Há muitas abordagens e padrões que evoluíram ao longo de décadas de desenvolvimento de software, e todas têm seus próprios prós e contras. Em muitos casos, a solução definitiva não pode envolver a decidir sobre uma abordagem única, mas pode integrar várias abordagens. Cenários de migração geralmente envolvem o deslocamento da abordagem de arquitetura de um para outro através de uma abordagem híbrida.

Este capítulo fornece uma visão geral de ambos os padrões de arquitetura lógica e física para aplicativos corporativos.

## <a name="architecture-patterns"></a>Padrões de arquitetura

Aplicativos de negócios modernos siga uma variedade de padrões de arquitetura. Esta seção representa uma pesquisa de padrões comuns. Os padrões listados aqui não são necessariamente todas as práticas recomendadas, mas ilustram diferentes abordagens.

Para obter mais informações, consulte [guia de arquitetura de aplicativo do Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monolitos

Muitos aplicativos de negócios seguem um padrão de monólito. Os aplicativos herdados geralmente são implementados como monolitos. No padrão de monólito, todas as preocupações de aplicativo estão contidas em uma única implantação. Tudo, desde a interface do usuário para chamadas de banco de dados está incluído na mesma base de código.

![Arquitetura de monólito](./media/monolith-architecture.png)

Há várias vantagens para a abordagem de monólito. Geralmente é mais fácil puxe para baixo de uma única base de código e começar a trabalhar. Tempo de aprendizado pode ser menor e criação de ambientes de teste é tão simple quanto fornecendo uma nova cópia. O monolito pode ser projetado para incluir vários componentes e aplicativos.

Infelizmente, o padrão de monolito tende a dividir em grande escala. Principais desvantagens da abordagem monólito incluem:

* Difícil de trabalhar em paralelo na mesma base de código.
* Qualquer alteração, não importa como trivial, exige a implantação de uma nova versão do aplicativo inteiro.
* Refatoração potencialmente afeta todo o aplicativo.
* Geralmente a única solução para dimensionar é criar várias cópias de muitos recursos do monólito.
* Como expandir de sistemas ou adquiridos de outros sistemas, integração pode ser difícil.
* Pode ser difícil de testar devido à necessidade de configurar o monolito inteiro.
* Reutilização de código é um desafio e outros aplicativos acabam tendo suas próprias cópias do código.

Muitas empresas olham para a nuvem como uma oportunidade para migrar aplicativos monólito e ao mesmo tempo refatorá-los para mais padrões utilizáveis. É comum para quebrar a aplicativos individuais e componentes para permitir que eles possam ser mantida, implantados e dimensionados separadamente.

## <a name="n-layer-applications"></a>Aplicativos de N-camadas

Lógica de aplicativo da partição de aplicativo de N camadas em camadas específicas. As camadas mais comuns incluem:

* Interface do usuário
* lógica de negócios
* Acesso aos dados

Outras camadas podem incluir o middleware, processamento em lotes e API. É importante observar que as camadas são lógicas. Embora elas são desenvolvidas em isolamento, eles podem todos ser implantados para a mesma plataforma de destino.

![Arquitetura de N-camadas](./media/n-layer-architecture.png)

Há várias vantagens para a abordagem de N-camadas, incluindo:

* Refatoração é isolada em uma camada.
* As equipes de forma independente podem criar, testar, implantar e manter a camadas separadas.
* Camadas podem ser alternadas, por exemplo a camada de dados pode acessar vários bancos de dados sem a necessidade de alterações para a camada de interface do usuário.

Sem servidor pode ser usada para implementar uma ou mais camadas.

## <a name="microservices"></a>Microsserviços

**[Microsserviços](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)**  arquiteturas contêm características comuns incluem:

* Aplicativos são compostos por vários serviços pequenos.
* Cada serviço é executado em seu próprio processo.
* Os serviços são alinhados em torno de domínios de negócios.
* Os serviços se comunicam por APIs leves, normalmente usando HTTP como o transporte.
* Serviços podem ser implantados e atualizados independentemente.
* Os serviços não são dependentes de um único armazenamento de dados.
* O sistema foi projetado com falha em mente e o aplicativo poderá ser executado mesmo quando determinados serviços falham.

Microsserviços não precisam ser mutuamente exclusivos para outras abordagens de arquitetura. Por exemplo, uma arquitetura de N camadas pode usar microsserviços para a camada intermediária. Também é possível implementar microsserviços em uma variedade de maneiras de diretórios virtuais em hosts do IIS para contêineres. As características dos microsserviços tornam especialmente ideais para implementações sem servidor.

![Arquitetura de microsserviços](./media/microservices-architecture.png)

Os profissionais de arquiteturas de microsserviços incluem:

* Refatoração geralmente é isolada em um único serviço.
* Os serviços podem ser atualizados independentemente uns dos outros.
* Resiliência e a elasticidade podem ser ajustados à demanda de serviços individuais.
* Desenvolvimento pode ocorrer em paralelo entre plataformas e equipes diferentes.
* É mais fácil escrever testes abrangentes para os serviços isolados.

Microsserviços vêm com seus próprios desafios, incluindo:

* Determinando quais serviços estão disponíveis e como chamá-los.
* Gerenciando o ciclo de vida de serviços.
* Noções básicas sobre como os serviços se encaixam no aplicativo geral.
* Testes de sistema completo de chamadas feitas entre diferentes serviços.

Finalmente, há soluções para atender a todos esses desafios, incluindo tocar os benefícios sem servidor que serão discutidos posteriormente.

>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](architecture-deployment-approaches.md)
