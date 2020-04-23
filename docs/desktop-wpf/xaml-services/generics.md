---
title: Genéricos em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9354f74b978652c36df28a91a6b9db5cfff4bb1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071734"
---
# <a name="generics-in-xaml"></a>Genéricos em XAML

.NET XAML Services <xref:System.Xaml?displayProperty=fullName> conforme implementado fornece suporte para o uso de tipos CLR genéricos. Esse suporte inclui especificar as restrições dos genéricos como um argumento `Add` de tipo e impor a restrição chamando o método apropriado para casos de coleta genérica. Este tópico descreve aspectos do uso e referência de tipos genéricos em XAML.

## <a name="xtypearguments"></a>X:typearguments

`x:TypeArguments`é uma diretiva definida pela língua XAML. Quando é usado como membro de um tipo XAML que `x:TypeArguments` é apoiado por um tipo genérico, passa argumentos do tipo de restrição do genérico para o construtor de apoio. Para obter a sintaxe de referência que `x:TypeArguments`diz respeito ao uso de serviços .NET XAML, que inclui exemplos de sintaxe, consulte [x:TypeArguments Directive](xtypearguments-directive.md).

Porque `x:TypeArguments` pega uma string, e tem backup do conversor de tipo, é normalmente declarado no uso de XAML como um atributo.

No fluxo de nó XAML, as `x:TypeArguments` informações declaradas <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> podem `StartObject` ser obtidas a partir de uma posição no fluxo de nó. O valor <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> de retorno <xref:System.Xaml.XamlType> é uma lista de valores. A determinação de saber se um tipo XAML <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>representa um tipo genérico pode ser feita ligando .

## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Regras e Convenções de Sintaxe para Genéricos em XAML

Em XAML, um tipo genérico deve ser sempre representado como um genérico constrangido. Um genérico sem restrições nunca está presente no sistema do tipo XAML ou em um fluxo de nó XAML e não pode ser representado na marcação XAML. Um genérico pode ser referenciado dentro da sintaxe de atributo XAML para `x:TypeArguments`casos em que `x:Type` é uma restrição de tipo aninhada de um genérico sendo referenciado por , ou para casos em que fornece uma referência tipo CLR para um tipo genérico. A referência a genéricos <xref:System.Xaml.Schema.XamlTypeTypeConverter> é suportada através da classe definida pelo .NET XAML Services.

O formulário de sintaxe de <xref:System.Xaml.Schema.XamlTypeTypeConverter> atributo XAML habilitado pela convenção típica de sintaxe MSIL / CLR que usa suportes angulares para tipos e restrições de genéricos e, em vez disso, substitui parênteses para o recipiente de restrição. Para um exemplo, consulte [x:Diretiva TypeArguments](xtypearguments-directive.md).

## <a name="generics-and-xaml-2009-features"></a>Características de Genéricos e XAML 2009

Se você usar o XAML 2009 em vez de mapear os tipos de base clr para obter tipos XAML para primitivos `x:TypeArguments`de linguagem comum, você pode usar os tipos [embutidos XAML 2009](types-for-primitives.md) como itens de informação em . Por exemplo, você pode declarar o seguinte (mapeamentos de prefixo não mostrados, mas `x` é o espaço de nome XAML da linguagem XAML para XAML 2009):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

## <a name="generics-support-in-wpf"></a>Suporte a genéricos no WPF

Para o uso do XAML 2006 ao direcionar especificamente o WPF, `x:TypeArguments` [x:Class](xclass-directive.md) também deve ser fornecido no mesmo elemento que , e esse elemento deve ser o elemento raiz em um documento XAML. O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo. Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>.

As possíveis soluções alternativas para suportar usos genéricos incluem a definição de uma extensão de marcação personalizada que pode retornar tipos genéricos, ou fornecer uma definição de classe de embalagem que deriva de um tipo genérico, mas achata a restrição genérica em sua própria definição de classe.

No WPF você pode usar os recursos xaml 2009 juntamente com `x:TypeArguments`, mas apenas para XAML solto (XAML que não é compilado de marcação). O XAML compilado por marcação para WPF e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do XAML 2009.

Fluxos de trabalho personalizados no Windows Workflow Foundation para .NET Framework 3.5 não suportam o uso genérico de XAML.

## <a name="see-also"></a>Confira também

- [Diretiva x:TypeArguments](xtypearguments-directive.md)
- [Diretiva x:Class](xclass-directive.md)
- [Tipos inseridos para primitivos de linguagem XML comuns](types-for-primitives.md)
