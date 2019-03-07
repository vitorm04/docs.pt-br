---
title: Coleções e tipos de coleção para XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 4123b64545f7c47a96c4cae496046a89b7e576b0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494617"
---
# <a name="collections-and-collection-types-for-xaml"></a>Coleções e tipos de coleção para XAML

Este tópico descreve como definir propriedades de tipos que se destinam para dar suporte a uma coleção e para dar suporte a sintaxe XAML para criar uma instância de coleção de itens como filhos do elemento de um elemento de propriedade ou elemento do objeto pai.

## <a name="xaml-collection-concepts"></a>Conceitos de coleção de XAML

Conceitualmente, qualquer relacionamento no XAML, onde há vários itens filho dentro do escopo de um elemento de objeto XAML ou elemento de propriedade XAML deve ser implementado como uma coleção. Essa coleção deve ser associada uma determinada propriedade XAML do tipo XAML que é o pai na relação. A propriedade deve ser uma coleção porque espera que um processador XAML atribuir a cada item na marcação para ser um item recém-adicionado da propriedade de coleção de backup.

No nível da linguagem XAML, os requisitos exatos de suporte de coleção não são totalmente definidos. O conceito que uma coleção pode ser tanto uma lista ou um dicionário (mas não ambos) é definido no nível da linguagem XAML, mas quais tipos de suporte representam ambos listas ou dicionários não é definido pela linguagem XAML.

Nos serviços de XAML do .NET Framework, o conceito de suporte de coleção de XAML é mais claramente definido em termos de tipos de suporte do .NET Framework. Especificamente, o suporte a XAML para coleções baseia-se em várias APIs que são usadas para listas e dicionários na programação do .NET Framework geral e conceitos do .NET Framework.

1. O <xref:System.Collections.IList> interface indica uma coleção de lista.

2. O <xref:System.Collections.IDictionary> interface indica uma coleção de dicionário.

3. <xref:System.Array> representa uma matriz e uma matriz dá suporte a <xref:System.Collections.IList> métodos.

Em cada um desses conceitos de coleção, um processador XAML de serviços de XAML do .NET Framework espera chamar o `Add` método em uma instância específica do tipo da propriedade de coleção. Ou, em um cenário de serialização, um processador XAML produz instâncias de tipo XAML discretas para cada item encontrado na lista, dicionário ou matriz com base no conceito de específico da cada coleção de "Itens". Esses são: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; explícita <xref:System.Array.System%23Collections%23IList%23Item%2A> para <xref:System.Array>.

## <a name="generic-collections"></a>Coleções genéricas

Coleções genéricas podem ser útil para gerais de programação .NET Framework e também podem ser usadas para propriedades de coleção de XAML. No entanto, o genérico interfaces <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IDictionary%602> não são identificadas pelos processadores XAML de serviços de XAML do .NET Framework como sendo equivalente não genérico <xref:System.Collections.IList> ou <xref:System.Collections.IDictionary>. Em vez de implementar as interfaces, uma abordagem recomendada para tipos de propriedade de coleção genérica é derivar de classes <xref:System.Collections.Generic.List%601> ou <xref:System.Collections.Generic.Dictionary%602>. Essas classes implementam as interfaces não genéricas e, portanto, incluem o suporte esperado para coleções de XAML na implementação de base.

## <a name="read-only-collections-and-initialization-logic"></a>Coleções somente leitura e a lógica de inicialização

Na programação do .NET Framework, é um padrão de design comum para tornar qualquer propriedade que contém um valor de uma coleção como uma coleção somente leitura. Esse padrão permite que a instância que possui a propriedade de coleção para controlar melhor o que acontece com a coleção... Especificamente, o padrão impede a substituição acidental de toda a coleção já existente, definindo a propriedade. Nesse padrão, qualquer acesso à coleção por chamadores em vez disso, deve ser feito ao chamar métodos ou propriedades como compatíveis com o tipo de coleção e/ou as interfaces de coleção relevantes, como <xref:System.Collections.IList>.

Usando esse padrão significa que qualquer classe que expõe uma propriedade de coleção somente leitura deve inicializar primeiro essa propriedade para manter uma coleção vazia. Normalmente, a inicialização é executada como parte do comportamento de construção para a classe. Para ser útil para XAML, é importante que tal lógica sempre é referenciada pelo construtor padrão, pois o XAML geralmente chama o construtor padrão antes do processamento das propriedades (Propriedades de coleção ou de outra forma).

## <a name="xaml-type-system-support-and-collections"></a>Coleções e suporte do sistema de tipo XAML

Além da mecânica básica da análise de XAML e preencher ou serializar as propriedades de coleção, o sistema de tipos XAML como implementado no serviços de XAML do .NET Framework inclui vários recursos de design que pertencem às coleções em XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A> Retorna VERDADEIRO se o tipo XAML é apoiado por um tipo que fornece suporte de coleção de XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A> e <xref:System.Xaml.XamlType.IsArray%2A> possível identificar o tipo XAML dá suporte ao modo de coleta. Para XAML personalizado processadores que são baseados em serviços de XAML do .NET Framework e o XAML sistema de tipo, mas não com base em existente <xref:System.Xaml.XamlWriter> implementações, saber o modo de coleta é usado pode ser necessário para saber qual método chamar para processamento de coleção.

3. Cada um dos valores de propriedade anterior potencialmente são influenciados por substituições de <xref:System.Xaml.XamlType.LookupCollectionKind%2A> em um tipo XAML.
