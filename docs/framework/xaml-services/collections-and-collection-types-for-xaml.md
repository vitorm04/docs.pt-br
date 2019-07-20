---
title: Coleções e tipos de coleção para XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 63f6346837f77dbdbdcb4a90ec5af725be69ee02
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364331"
---
# <a name="collections-and-collection-types-for-xaml"></a>Coleções e tipos de coleção para XAML

Este tópico descreve como definir propriedades de tipos que se destinam a dar suporte a uma coleção e para dar suporte à sintaxe XAML para criar uma instância de itens de coleção como filhos de elemento de um elemento de objeto pai ou elemento de propriedade.

## <a name="xaml-collection-concepts"></a>Conceitos da coleção XAML

Conceitualmente, qualquer relação em XAML em que há vários itens filho dentro do escopo de um elemento de objeto XAML ou elemento de propriedade XAML deve ser implementado como uma coleção. Essa coleção deve ser associada a uma propriedade XAML específica do tipo XAML que é o pai nessa relação. A propriedade deve ser uma coleção porque um processador XAML espera atribuir cada item na marcação a ser um item recém-adicionado da propriedade de coleção de backup.

No nível da linguagem XAML, os requisitos exatos do suporte à coleta não estão totalmente definidos. O conceito de que uma coleção pode ser uma lista ou um dicionário (mas não ambos) é definido no nível de linguagem XAML, mas os tipos de suporte que representam listas ou dicionários não são definidos pela linguagem XAML.

Em .NET Framework serviços XAML, o conceito de suporte à coleção XAML é definido mais claramente em termos de .NET Framework tipos de backup. Especificamente, o suporte a XAML para coleções baseia-se em vários conceitos .NET Framework e APIs que são usadas para listas e dicionários em geral .NET Framework programação.

1. A <xref:System.Collections.IList> interface indica uma coleção de listas.

2. A <xref:System.Collections.IDictionary> interface indica uma coleção de dicionário.

3. <xref:System.Array>representa uma matriz e uma matriz dá suporte <xref:System.Collections.IList> a métodos.

Em cada um desses conceitos de coleção, um processador XAML .NET Framework serviços XAML espera chamar o `Add` método em uma instância específica do tipo da propriedade de coleção. Ou, em um cenário de serialização, um processador XAML produz instâncias de tipo XAML discretas para cada item encontrado na lista, no dicionário ou na matriz com base no conceito específico da coleção de "itens". Estes são: <xref:System.Collections.IList.Item%2A>; ; o explícito <xref:System.Array.System%23Collections%23IList%23Item%2A> para <xref:System.Array>. <xref:System.Collections.IDictionary.Item%2A>

## <a name="generic-collections"></a>Coleções genéricas

As coleções genéricas podem ser úteis para programação de .NET Framework geral e também podem ser usadas para propriedades da coleção XAML. No entanto, as <xref:System.Collections.Generic.IList%601> interfaces <xref:System.Collections.Generic.IDictionary%602> genéricas e não são identificadas por .NET Framework processadores XAML serviços XAML como sendo equivalentes ao <xref:System.Collections.IList> não <xref:System.Collections.IDictionary>genérico ou. Em vez de implementar as interfaces, uma abordagem recomendada para tipos de propriedade de coleção genérica é derivar <xref:System.Collections.Generic.List%601> das <xref:System.Collections.Generic.Dictionary%602>classes ou. Essas classes implementam as interfaces não genéricas e, portanto, incluem o suporte esperado para coleções XAML na implementação de base.

## <a name="read-only-collections-and-initialization-logic"></a>Coleções somente leitura e lógica de inicialização

Em .NET Framework programação, é um padrão de design comum fazer qualquer propriedade que contenha um valor de uma coleção como uma coleção somente leitura. Esse padrão permite que a instância proprietária da propriedade de coleção controle melhor o que acontece com a coleção. Especificamente, o padrão impede a substituição acidental de toda a coleção preexistente, definindo a propriedade. Nesse padrão, qualquer acesso à coleção por chamadores deve ser feito chamando métodos ou propriedades com suporte pelo tipo de coleção e/ou pelas interfaces de coleção relevantes, <xref:System.Collections.IList>como.

O uso desse padrão implica que qualquer classe que expõe uma propriedade de coleção somente leitura deve primeiro inicializar essa propriedade para manter uma coleção vazia. Normalmente, a inicialização é executada como parte do comportamento de construção da classe. Para ser útil para XAML, é importante que essa lógica seja sempre referenciada pelo construtor sem parâmetros, porque o XAML geralmente chama o construtor sem parâmetros antes de processar as propriedades (Propriedades de coleção ou de outra forma).

## <a name="xaml-type-system-support-and-collections"></a>Suporte e coleções do sistema de tipos XAML

Além da mecânica básica de análise de XAML e preenchimento ou serialização de propriedades de coleção, o sistema de tipos XAML conforme implementado em .NET Framework serviços XAML inclui vários recursos de design que pertencem a coleções em XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A>retornará true se o tipo XAML for apoiado por um tipo que fornece suporte à coleção XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>e <xref:System.Xaml.XamlType.IsArray%2A> pode identificar ainda mais qual modo de coleta o tipo XAML dá suporte. Para processadores XAML personalizados baseados em .NET Framework serviços XAML e o sistema de tipos XAML, mas não com base em <xref:System.Xaml.XamlWriter> implementações existentes, saber qual modo de coleta é usado pode ser necessário para saber qual método invocar processamento da coleção.

3. Cada um dos valores de propriedade anteriores é potencialmente influenciado por <xref:System.Xaml.XamlType.LookupCollectionKind%2A> substituições de em um tipo XAML.
