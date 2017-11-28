---
title: Suporte do .NET Core
description: "Saiba mais sobre os diferentes suportes de séries de versões (LTS e Atual) para .NET Core"
keywords: ".NET, .NET Core, lts, atual, fts, suporte, séries de suporte, acompanhamentos de suporte, Ciclo de vida, séries de versões"
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: fedc7025-f320-4cba-957b-ef74885f66de
ms.openlocfilehash: 254611ef05af22eea616fcfe3288239a744e0ccc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-support"></a>Suporte do .NET Core

Esta é uma descrição geral do suporte do .NET Core.

## <a name="lts-and-current-release-trains"></a>Séries da Versões Atual e LTS

Ter duas séries de versões de suporte é um conceito comum usado no mundo dos softwares, especialmente para projetos com código-fonte aberto, como o .NET Core. O .NET Core possui as seguintes séries de versões: [Suporte a Longo Prazo (LTS)](https://en.wikipedia.org/wiki/Long-term_support) e Atual. As versões de LTS são mantidas pela estabilidade ao longo do seu ciclo de vida, recebendo correções para problemas importantes e correções de segurança. O novo recurso funciona e correções de bug adicionais ocorrem nas versões Atuais. De uma perspectiva de suporte, essas séries de versões têm os seguintes atributos de ciclo de vida de suporte.

As versões de LTS têm
* Suporte por três anos após a data de disponibilidade geral de uma versão de LTS
* Ou por um ano após a disponibilização de uma versão subsequente do LTS

As versões atuais têm
* Suporte dentro da mesma janela de três anos como a versão de LTS pai
* Suporte por três meses após a disponibilização geral de uma versão Atual subsequente
* E por um ano após a disponibilização de uma versão subsequente do LTS

## <a name="versioning"></a>Controle de versão
As novas versões de LTS são marcadas por um aumento no número da versão Principal. As versões atuais têm o mesmo número Principal que as séries de LTS correspondentes e são marcadas por um aumento no número de versão Secundária. Por exemplo, 1.0.3 seria LTS e 1.1.0 seria Atual. Atualizações de correção de bug para o incremento da série da versão de Patch. Para saber mais sobre o esquema de controle de versão, confira [Controle de versão do .NET Core](index.md).

## <a name="what-causes-updates-in-lts-and-current-trains"></a>O que causa as atualizações em séries de LTS e Atuais?
Para entender quais alterações específicas, como correções de bugs ou a adição de APIs, motivam atualizações para os números de versão, veja a seção de Árvore de Decisão na [Documentação de Controle de Versão](index.md). Não há um conjunto de regras de ouro que decide quais alterações são aplicadas na ramificação de LTS da Atual. Normalmente, os patches e as atualizações de segurança necessários que corrigem o comportamento esperado são motivos para atualizar a ramificação de LTS. Nós também pretendemos dar suporte a sistemas operacionais de desenvolvedor de área de trabalho recentes na ramificação de LTS, muito embora isso nem sempre seja possível. Uma boa maneira de acompanhar quais sistemas operacionais, correções e APIs têm suporte em uma determinada versão é procurar suas [notas de versão](https://github.com/dotnet/core/tree/master/release-notes) no GitHub.

### <a name="further-reading"></a>Leitura adicional
* [Folha informativa sobre o ciclo de vida do suporte do .NET Core](https://www.microsoft.com/net/core/support)
* [Versões e sistemas operacionais com suporte atualmente](https://github.com/dotnet/core/blob/master/roadmap.md)
