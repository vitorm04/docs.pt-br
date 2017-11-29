---
title: "Coleções e tipos de coleção para XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
caps.latest.revision: "2"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 991360433b5fb09c13e59f63be94e0fa0ec94b61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="collections-and-collection-types-for-xaml"></a>Coleções e tipos de coleção para XAML
Este tópico descreve como definir propriedades de tipos que se destinam para dar suporte a uma coleção e para dar suporte a sintaxe XAML para criar uma instância de coleção de itens como elementos filho de um elemento do objeto pai ou um elemento de propriedade.  
  
## <a name="xaml-collection-concepts"></a>Conceitos de coleção de XAML  
 Conceitualmente, qualquer relação em XAML, onde há vários itens filho dentro do escopo de um elemento de objeto XAML ou elemento de propriedade XAML deve ser implementado como uma coleção. Essa coleção deve ser associada uma determinada propriedade XAML do tipo de XAML que é o pai na relação. A propriedade deve ser uma coleção porque espera que um processador XAML atribuir a cada item na marcação para ser um novo item da propriedade de coleção de backup.  
  
 No nível de linguagem XAML, os requisitos exatos de suporte de coleção não estão totalmente definidos. O conceito que uma coleção pode ser uma lista ou um dicionário (mas não ambos) é definido no nível de linguagem XAML, mas os tipos de backup representam ou listas ou dicionários não está definida, a linguagem XAML.  
  
 Em serviços XAML do .NET Framework, o conceito de suporte de coleção de XAML mais claramente é definido em termos de fazendo tipos do .NET Framework. Especificamente, o suporte XAML para coleções baseia-se em vários conceitos do .NET Framework e APIs que são usadas para listas e dicionários na programação geral do .NET Framework.  
  
1.  O <xref:System.Collections.IList> interface indica uma coleção de lista.  
  
2.  O <xref:System.Collections.IDictionary> interface indica uma coleção dicionary.  
  
3.  <xref:System.Array>representa uma matriz, uma matriz de oferecer suporte a <xref:System.Collections.IList> métodos.  
  
 Em cada um desses conceitos de coleção, um processador de XAML do .NET Framework XAML serviços espera chamar o `Add` método em uma instância específica do tipo da propriedade de coleção. Ou, em um cenário de serialização, um processador XAML produz instâncias de tipo XAML discretas para cada item encontrado na lista, dicionário ou matriz com base em um determinado conceito da cada coleção de "Itens". Esses são: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; explícita <xref:System.Array.System%23Collections%23IList%23Item%2A> para <xref:System.Array>.  
  
## <a name="generic-collections"></a>Coleções genéricas  
 Coleções genéricas podem ser úteis para gerais de programação .NET Framework e também podem ser usadas para propriedades de coleção de XAML. No entanto, as interfaces genérica <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IDictionary%602> não são identificadas pelos processadores XAML de serviços XAML do .NET Framework como sendo equivalente para não genéricas <xref:System.Collections.IList> ou <xref:System.Collections.IDictionary>. Em vez de implementar as interfaces, uma abordagem recomendada para tipos de propriedade de coleção genérica é derivar as classes <xref:System.Collections.Generic.List%601> ou <xref:System.Collections.Generic.Dictionary%602>. Essas classes implementam as interfaces não genéricas e, portanto, incluem o suporte esperado para coleções XAML na implementação de base.  
  
## <a name="read-only-collections-and-initialization-logic"></a>Coleções somente leitura e lógica de inicialização  
 Na programação do .NET Framework, é um padrão de design comum para tornar qualquer propriedade que contém um valor de uma coleção como uma coleção somente leitura. Esse padrão permite que a instância que possui a propriedade de coleção para controlar melhor o que acontece na coleção. Especificamente, o padrão impede a substituição acidental de toda a coleção já existente, definindo a propriedade. Nesse padrão, qualquer acesso à coleção de chamadores em vez disso, deve ser feito ao chamar métodos ou propriedades com suporte, como o tipo de coleção e/ou as interfaces de coleção relevantes <xref:System.Collections.IList>.  
  
 Usando esse padrão significa que qualquer classe que expõe uma propriedade de coleção somente leitura deve inicializar primeiro essa propriedade para manter uma coleção vazia. Normalmente, a inicialização é executada como parte do comportamento de construção para a classe. Para ser útil para XAML, é importante que essa lógica é sempre referenciada pelo construtor padrão, pois o XAML geralmente chama o construtor padrão antes de processar as propriedades (Propriedades de coleção ou de outra forma).  
  
## <a name="xaml-type-system-support-and-collections"></a>Coleções e suporte do sistema de tipo XAML  
 Além os mecanismos básicos de analisando o XAML e popular ou serializar as propriedades de coleção, o sistema de tipo XAML conforme implementado no serviços de XAML do .NET Framework inclui vários recursos de design que pertencem às coleções em XAML.  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A>Retorna true se o tipo de XAML é apoiado por um tipo que fornece suporte a coleções XAML.  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A>e <xref:System.Xaml.XamlType.IsArray%2A> possível identificar o tipo de XAML dá suporte ao modo de coleta. Para XAML personalizada processadores que são baseados em serviços XAML do .NET Framework e o XAML digite sistema mas não com base em existente <xref:System.Xaml.XamlWriter> implementações, saber qual modo de coleta é usado pode ser necessário para saber qual método chamar para processamento de coleção.  
  
3.  Cada um dos valores de propriedade anterior potencialmente são influenciados por substituições de <xref:System.Xaml.XamlType.LookupCollectionKind%2A> em um tipo XAML.
