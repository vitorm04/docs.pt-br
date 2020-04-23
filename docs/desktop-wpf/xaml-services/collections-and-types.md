---
title: Coleções e tipos de coleção para XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 2ec58026c605df31489c8aab4c4cc714dab11474
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "82071293"
---
# <a name="collections-and-collection-types-for-xaml"></a>Tipos de coletas e coleções para XAML

Este artigo descreve como definir propriedades de tipos que se destinam a apoiar uma coleção e apoiar a sintaxe XAML para instanciar itens de coleta como elemento filho de um elemento de objeto pai ou elemento de propriedade.

## <a name="xaml-collection-concepts"></a>Conceitos de Coleção XAML

Conceitualmente, qualquer relação no XAML onde há vários itens infantis dentro do escopo de um elemento objeto XAML ou elemento de propriedade XAML deve ser implementado como uma coleção. Essa coleção deve estar associada a uma propriedade XAML específica do tipo XAML que é o pai nessa relação. A propriedade deve ser uma coleção porque um processador XAML espera atribuir cada item na marcação para ser um item recém-adicionado da propriedade de coleta de apoio.

No nível de linguagem XAML, os requisitos exatos do suporte à coleta não são totalmente definidos. O conceito de que uma coleção pode ser uma lista ou um dicionário (mas não ambos) é definido no nível de linguagem XAML, mas quais tipos de apoio representam listas ou dicionários não é definido pela língua XAML.

Nos Serviços XAML .NET, o conceito de suporte à coleção XAML é mais claramente definido em termos de tipos de suporte .NET. Especificamente, o suporte xaml para coleções é baseado em vários conceitos e APIs .NET que são usados para listas e dicionários em programação geral .NET.

1. A <xref:System.Collections.IList> interface indica uma coleção de listas.

2. A <xref:System.Collections.IDictionary> interface indica uma coleção de dicionários.

3. <xref:System.Array>representa uma matriz, e uma <xref:System.Collections.IList> matriz suporta métodos.

Em cada um desses conceitos de coleção, um processador .NET `Add` XAML Services XAML espera chamar o método em uma instância específica do tipo de propriedade de coleção. Ou, em um cenário de serialização, um processador XAML produz instâncias discretas do tipo XAML para cada item encontrado na lista, dicionário ou matriz com base no conceito específico de "Itens" de cada coleção. Estes itens são: <xref:System.Collections.IList.Item%2A?displayProperty=nameWithType>; <xref:System.Collections.IDictionary.Item%2A?displayProperty=nameWithType>; o <xref:System.Array.System%23Collections%23IList%23Item%2A?displayProperty=nameWithType> explícito <xref:System.Array>para .

## <a name="generic-collections"></a>Coleções Genéricas

Coleções genéricas podem ser úteis para programação geral .NET, e também podem ser usadas para propriedades de coleção XAML. No entanto, <xref:System.Collections.Generic.IList%601> as <xref:System.Collections.Generic.IDictionary%602> interfaces genéricas e não são identificadas pelos processadores XAML Services .NET como sendo equivalentes aos não genéricos <xref:System.Collections.IList> ou <xref:System.Collections.IDictionary>. Em vez de implementar as interfaces, uma abordagem recomendada para <xref:System.Collections.Generic.List%601> tipos <xref:System.Collections.Generic.Dictionary%602>de propriedade de coleta genérica é derivar das classes ou . Essas classes implementam as interfaces não genéricas e, portanto, incluem o suporte esperado para coleções XAML na implementação base.

## <a name="read-only-collections-and-initialization-logic"></a>Coleções somente leitura e lógica de inicialização

Na programação .NET, é um padrão de design comum fazer qualquer propriedade que detenha um valor de uma coleção como uma coleção somente leitura. Esse padrão permite que o caso que possui a propriedade de cobrança controle melhor o que acontece com a coleção.. Especificamente, o padrão impede a substituição acidental de toda a coleção pré-existente, definindo a propriedade. Neste padrão, qualquer acesso à coleção por chamadores deve ser feito por métodos de chamada ou propriedades suportadas pelo tipo de coleta e/ou pelas interfaces de coleta relevantes, tais como <xref:System.Collections.IList>.

O uso deste padrão implica que qualquer classe que exponha uma propriedade de coleção somente leitura deve primeiro inicializar essa propriedade para manter uma coleção vazia. Normalmente, a inicialização é realizada como parte do comportamento de construção da classe. Para ser útil para xaml, é importante que tal lógica seja sempre referenciada pelo construtor sem parâmetros, pois xAML geralmente chama o construtor sem parâmetros antes de processar as propriedades (propriedades de coleta ou não).

## <a name="xaml-type-system-support-and-collections"></a>Suporte e coleções do sistema do tipo XAML

Além da mecânica básica de analisar XAML e preencher ou serializar propriedades de coleção, o sistema tipo XAML implementado no .NET XAML Services inclui vários recursos de design que pertencem às coleções em XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A>retorna verdadeiro se o tipo XAML for suportado por um tipo que fornece suporte à coleção XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>e <xref:System.Xaml.XamlType.IsArray%2A> pode identificar ainda qual modo de coleta o tipo XAML suporta. Para processadores XAML personalizados que são baseados em Serviços XAML .NET <xref:System.Xaml.XamlWriter> e no sistema do tipo XAML, mas não com base nas implementações existentes, saber qual modo de coleta é usado pode ser necessário para saber qual método invocar para o processamento de coleta.

3. Cada um dos valores de propriedade anteriores é potencialmente influenciado por substituições de <xref:System.Xaml.XamlType.LookupCollectionKind%2A> um tipo XAML.
