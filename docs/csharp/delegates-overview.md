---
title: Introdução a Delegados
description: Saiba mais sobre delegados neste tópico de visão geral que apresenta os conceitos básicos e discute as metas de design da linguagem para delegados.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: d42d9d10aeaa153f12933fa3a59e58719f7741e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-delegates"></a>Introdução a Delegados

[Anterior](delegates-events.md)

Os delegados fornecem um mecanismo de *associação tardia* no .NET. Associação tardia significa que você cria um algoritmo em que o chamador também fornece pelo menos um método que implementa a parte do algoritmo.

Por exemplo, considere classificar uma lista de estrelas em um aplicativo de astronomia.
Você pode optar por classificar as estrelas por sua distância da terra ou a magnitude da estrela ou seu brilho percebido.

Em todos esses casos, o método Sort() faz essencialmente a mesma coisa: organiza os itens na lista com base em alguma comparação. O código que compara duas estrelas é diferente para cada uma das ordenações de classificação.

Esses tipos de soluções foram usados no software por meio século.
O conceito de delegado de linguagem C# fornece suporte de linguagem de primeira classe e segurança de tipos em torno do conceito.

Como você verá posteriormente nesta série, o código C# que você escreve para algoritmos como esse é seguro quanto ao tipo e aproveita a linguagem e o compilador para garantir que os tipos correspondem aos argumentos e tipos de retorno.

## <a name="language-design-goals-for-delegates"></a>Metas de design da linguagem para delegados

Os designers de linguagem enumeraram várias metas para o recurso que eventualmente se tornaram delegados.

A equipe queria um constructo de linguagem comum que pudesse ser usada qualquer algoritmo de associação tardia. Isso permite aos desenvolvedores aprender um conceito e usar esse conceito entre muitos problemas de software diferentes.

Em segundo lugar, a equipe queria dar suporte a chamadas de método single ou multicast. (Delegados multicast são delegados em que vários métodos foram encadeados. Você verá exemplos [posteriormente nesta série](delegate-class.md). 

A equipe queria delegados para dar suporte à mesma segurança de tipos que os desenvolvedores esperam de todos os constructos de C#. 

Por fim, a equipe reconheceu que um padrão de eventos é um padrão específico em que delegados ou qualquer algoritmo de associação tardia é muito útil. A equipe quis garantir que o código para delegados pudesse fornecer a base para o padrão de evento .NET.

O resultado de todo esse trabalho era o suporte do delegado e do evento no C# e .NET. Os demais artigos nessa seção abordarão os recursos da linguagem, o suporte da biblioteca e as expressões comuns que são usadas ao trabalhar com delegados.

Você aprenderá sobre a palavra-chave `delegate` e qual código ela gera. Você aprenderá sobre os recursos na classe `System.Delegate` e como esses recursos são usados. Você aprenderá como criar delegados de segurança de tipos e como criar métodos que podem ser invocados por meio de delegados. Você também aprenderá a trabalhar com eventos e delegados usando expressões Lambda. Você verá onde delegados se tornam um dos blocos de construção para LINQ. Você aprenderá como os delegados são a base para o padrão de evento do .NET e como eles são diferentes.

Em geral, você verá como os delegados são parte integrante de programação em .NET e no trabalho com as APIs de estrutura.

Vamos começar.

[Avançar](delegate-class.md)
