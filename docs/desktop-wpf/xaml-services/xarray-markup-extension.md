---
title: Extensão de marcação x:Array
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072042"
---
# <a name="xarray-markup-extension"></a>Extensão de marcação x:Array

Fornece suporte geral para matrizes de objetos em XAML através de uma extensão de marcação. Isso corresponde ao `x:ArrayExtension` tipo XAML em [MS-XAML].

## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`typeName`|O nome do tipo `x:Array` que seu testamento conterá. `typeName`pode ser (e muitas vezes é) prefixado para um namespace XAML que contém as definições do tipo XAML.|
|`arrayContents`|O conteúdo dos itens atribuídos à propriedade `ArrayExtension.Items` intrínseca. Normalmente, esses itens são especificados como um ou `x:Array` mais elementos de objeto contidos nas tags de abertura e fechamento. Espera-se que os objetos especificados aqui sejam atribuídos `typeName`ao tipo XAML especificado em .|

## <a name="remarks"></a>Comentários

`Type`é um atributo `x:Array` necessário para todos os elementos do objeto. Um `Type` valor de parâmetro não `x:Type` precisa usar uma extensão de marcação; o nome curto do tipo é um tipo XAML, que pode ser especificado como uma string.

Na implementação do .NET XAML Services, a relação entre <xref:System.Type> o tipo XAML de entrada e a CLR de saída do array criado é influenciada pelo contexto de serviço para extensões de marcação. A <xref:System.Type> saída <xref:System.Xaml.XamlType.UnderlyingType%2A> é do tipo XAML de entrada, depois de procurar o <xref:System.Xaml.XamlType> necessário <xref:System.Windows.Markup.IXamlTypeResolver> com base no contexto do esquema XAML e no serviço que o contexto fornece.

Quando processado, o conteúdo da matriz `ArrayExtension.Items` é atribuído à propriedade intrínseca. Na <xref:System.Windows.Markup.ArrayExtension> implementação, isso <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>é representado por .

Na implementação do .NET XAML Services, o manuseio <xref:System.Windows.Markup.ArrayExtension> dessa extensão de marcação é definido pela classe. <xref:System.Windows.Markup.ArrayExtension>não é selado e pode ser usado como base para uma implementação de extensão de marcação para um tipo de array personalizado.

`x:Array`é mais destinado à extensibilidade geral da linguagem em XAML. Mas `x:Array` também pode ser útil para especificar valores XAML de certas propriedades que tomam coleções suportadas por XAML como seu conteúdo de propriedade estruturado. Por exemplo, você pode especificar o conteúdo de uma <xref:System.Collections.IEnumerable> propriedade com um `x:Array` uso.

`x:Array` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. `x:Array`é parcialmente uma exceção a essa regra porque, `x:Array` em vez de fornecer tratamento alternativo de valor de atributo, fornece tratamento alternativo de seu conteúdo de texto interno. Esse comportamento permite que tipos que podem não ser suportados por um modelo de conteúdo existente sejam agrupados em uma matriz e referenciados posteriormente no code-behind acessando a matriz nomeada; você pode <xref:System.Array> chamar métodos para obter itens de matriz individuais.

Todas as extensões de marcação em{,} `)` XAML usam os aparelhos ( em sua sintaxe de atributo, que é a convenção pela qual um processador XAML reconhece que uma extensão de marcação deve processar o valor do atributo. Para obter mais informações sobre extensões de marcação em geral, consulte [Type Converters e Extensões de Marcação para XAML](type-converters-and-markup-extensions.md).

No XAML 2009, `x:Array` é definido como uma linguagem primitiva em vez de uma extensão de marcação. Para obter mais informações, consulte [Tipos incorporados para primitivos comuns da linguagem XAML](types-for-primitives.md).

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

Normalmente, os elementos `x:Array` do objeto que povoam um não são elementos que existem no namespace [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML e requerem um mapeamento de prefixo para um namespace XAML não padrão.

Por exemplo, o seguinte é uma matriz simples `sys` de duas `x`strings, com o prefixo (e também ) definido no nível da matriz.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Para tipos personalizados que são usados como elementos de matriz, a classe também deve suportar os requisitos para ser instanciado em XAML como elementos de objeto. Para obter mais informações, consulte [XAML e Classes Personalizadas para WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

## <a name="see-also"></a>Confira também

- [Extensões de marcação e XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Tipos migrados do WPF para System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
