---
title: Conversores de tipo e extensões de marcação para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: bee94b03d4fd6e6f5ef8571e83f554b381dd6582
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071650"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Conversores de tipo e extensões de marcação para XAML

Conversores de tipo e extensões de marcação são duas técnicas que sistemas do tipo XAML e escritores XAML usam para gerar componentes de gráficos de objetos. Embora compartilhem algumas características, conversores de tipo e extensões de marcação são representados de forma diferente em um fluxo de nós XAML. Neste conjunto de documentação, conversores de tipo, extensões de marcação e construções semelhantes são às vezes chamados coletivamente de conversores de valor.

## <a name="value-converters"></a>Conversores de valor

No XAML, conversores de valor são usados para vários cenários. A lista a seguir mostra os diferentes tipos de conversores de valor em XAML:

- Conversor de tipo

- Extensão de marcação

- Serializador de valor

- Classe ou classe de suporte relacionada sustam a lógica de uma sintaxe de texto XAML

## <a name="type-converters"></a>Conversores de tipo

Na definição de .NET XAML Services, conversores <xref:System.ComponentModel.TypeConverter> de tipo são classes derivadas da classe CLR. <xref:System.ComponentModel.TypeConverter>é uma classe que estava no .NET antes do XAML existir. Seu objetivo original era suportar janelas de propriedade e metáforas de edição semelhantes baseadas em texto para propriedades IDE. A introdução de XAML <xref:System.ComponentModel.TypeConverter> para .NET usa para converter uma sintaxe de texto (como encontrado em um valor de atributo ou um nó de valor XAML) em um objeto. <xref:System.ComponentModel.TypeConverter>também pode ser usado para serializar um valor de objeto à sintaxe de texto. <xref:System.ComponentModel.TypeConverter>também foi usado em implementações XAML específicas de estrutura anteriores no Windows Presentation Foundation (WPF) e na Windows Communication Foundation (WCF). Para obter mais <xref:System.ComponentModel.TypeConverter> informações sobre o in XAML, consulte [Type Converters for XAML Overview](type-converters-overview.md).

## <a name="markup-extensions"></a>Extensões de marcação

Na implementação do .NET XAML Services, as <xref:System.Windows.Markup.MarkupExtension> extensões de marcação são classes que derivam da classe. As extensões de markup são um conceito que, nesta forma, é originada pela linguagem XAML. Você pode pensar em uma extensão de marcação como sendo algo como uma seqüência de fuga extensível que chama para uma classe de serviço para fornecer sua lógica. Em termos de marcação, os processadores XAML reconhecem universalmente uma extensão de marcação por uma seqüência de texto que começa com uma chave de abertura ({) em uma seqüência de texto.

As extensões de marcação diferem dos conversores de tipo. Conversores de tipo são tipicamente associados a tipos ou membros. Eles são invocados quando uma criação de gráfico de objeto ou uma serialização encontra sintaxe de texto que está associada a essas entidades.

As extensões de marcação estão associadas a uma única classe de serviço de suporte, mas podem ser aplicadas para qualquer valor de membro. (No entanto, você pode implementar sua extensão de marcação para restringir deliberadamente seu uso a determinados membros ou tipos de destino, usando o contexto do serviço.) As extensões de marcação podem substituir uma associação de conversor de tipo. Ou você pode usá-los para especificar um valor de atributo para membros que não suportariam uma sintaxe de texto.

Para obter mais informações sobre o padrão de implementação de extensão de marcação para XAML, consulte [Extensões de marcação para visão geral XAML](markup-extensions-overview.md).

## <a name="value-serializers"></a>Serializadores de valor

A <xref:System.Windows.Markup.ValueSerializer> é um conversor de tipo especializado que é otimizado para converter um objeto em uma string. A <xref:System.Windows.Markup.ValueSerializer> para XAML pode `ConvertFrom` não implementar o método em tudo. Uma <xref:System.Windows.Markup.ValueSerializer> implementação obtém serviços de <xref:System.ComponentModel.TypeConverter> forma que seja como uma implementação. Os métodos virtuais `context` fornecem um parâmetro de entrada. O `context` parâmetro é <xref:System.Windows.Markup.IValueSerializerContext>do tipo , <xref:System.IServiceProvider> que herda <xref:System.IServiceProvider.GetService%2A> da interface e tem um método.

No sistema do tipo XAML e para implementações de escritores XAML que usam processamento de loop de nó XAML <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> para serialização, um conversor de valor que está associado a um tipo ou membro é relatado por sua própria propriedade. O significado para os escritores XAML <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> que <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> realizam serialização é que se a e existir, o conversor de tipo deve ser usado para o caminho de carga e o serializador de valor deve ser usado para o caminho de salvamento. Se <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existe, mas <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> é, `null`o conversor de tipo também é usado para o caminho de salvamento.

## <a name="other-value-converters"></a>Outros conversores de valor

Um conversor de valor é extensível além dos padrões específicos de um conversor de tipo ou de uma extensão de marcação. No entanto, essa personalização também exigiria a redefinição do sistema do tipo XAML, conforme fornecido pelo .NET XAML Services. O sistema do tipo XAML existente tem representações e sistemas de relatórios para conversores de tipo, extensões de marcação e serializadores de valor, mas não para formas personalizadas de conversão de valor. Se você quiser criar conversores <xref:System.Xaml.Schema.XamlValueConverter%601> de valor personalizados, use o tipo.

## <a name="type-converters-and-markup-extensions-in-combination"></a>Tipo conversores e extensões de marcação em combinação

Extensões de marcação e conversores de tipo são usados para diferentes situações em XAML. Embora o contexto esteja disponível para usos de extensão de marcação, o comportamento de conversão de tipos de propriedades em que uma extensão de marcação fornece um valor geralmente não é verificado em implementações de extensão de marcação. Em outras palavras, mesmo que uma extensão `ProvideValue` de marcação retorne uma seqüência de texto como sua saída, o comportamento de conversão de tipo nessa string conforme aplicado a um tipo de valor de propriedade ou propriedade específica não é invocado. Geralmente, o objetivo de uma extensão de marcação é processar uma string e retornar um objeto sem qualquer tipo de conversor envolvido.

## <a name="service-context-for-a-value-converter"></a>Contexto de serviço para um conversor de valor

Quando você implementa um conversor de valor, muitas vezes você precisa acessar um contexto no qual o conversor de valor é aplicado. Esse contexto é conhecido como contexto de serviço. O contexto do serviço pode incluir informações como o contexto ativo do esquema XAML, acesso ao sistema de mapeamento de tipo que o contexto do esquema XAML e o escritor de objetos XAML fornecem, e assim por diante. Para obter mais informações sobre os contextos de serviço disponíveis para um conversor de valor e como acessar os serviços que um contexto de serviço pode fornecer, consulte [Contextos de serviço disponíveis para converter conversores de tipo e extensões de marcação](service-contexts-with-type-converters-and-markup-extensions.md).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Visão geral das extensões de marcação para XAML](markup-extensions-overview.md)
- [Visão geral de conversores de tipo para XAML](type-converters-overview.md)
- [Contextos de serviço disponíveis para conversores de tipo e extensões de marcação](service-contexts-with-type-converters-and-markup-extensions.md)
