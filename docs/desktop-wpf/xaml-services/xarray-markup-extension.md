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
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555166"
---
# <a name="xarray-markup-extension"></a>Extensão de marcação x:Array

Fornece suporte geral para matrizes de objetos em XAML por meio de uma extensão de marcação. Isso corresponde ao `x:ArrayExtension` tipo XAML em [MS-XAML].

## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`typeName`|O nome do tipo que seu `x:Array` conterá. `typeName` pode ser (e geralmente é) prefixado para um namespace XAML que contém as definições de tipo XAML.|
|`arrayContents`|O conteúdo dos itens que é atribuído à `ArrayExtension.Items` propriedade intrínseca. Normalmente, esses itens são especificados como um ou mais elementos de objeto contidos nas `x:Array` marcas de abertura e fechamento. Os objetos especificados aqui devem ser atribuíveis ao tipo XAML especificado em `typeName` .|

## <a name="remarks"></a>Comentários

`Type` é um atributo necessário para todos os `x:Array` elementos de objeto. Um `Type` valor de parâmetro não precisa usar uma `x:Type` extensão de marcação; o nome curto do tipo é um tipo XAML, que pode ser especificado como uma cadeia de caracteres.

Na implementação de serviços XAML .NET, a relação entre o tipo XAML de entrada e o CLR <xref:System.Type> de saída da matriz criada é influenciada pelo contexto de serviço para extensões de marcação. A saída <xref:System.Type> é o <xref:System.Xaml.XamlType.UnderlyingType%2A> do tipo XAML de entrada, depois de Pesquisar o necessário <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e no <xref:System.Windows.Markup.IXamlTypeResolver> serviço que o contexto fornece.

Quando processado, o conteúdo da matriz é atribuído à `ArrayExtension.Items` propriedade intrínseca. Na <xref:System.Windows.Markup.ArrayExtension> implementação, isso é representado por <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> .

Na implementação de serviços XAML .NET, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.ArrayExtension> classe. <xref:System.Windows.Markup.ArrayExtension> Não é lacrado e pode ser usado como base para uma implementação de extensão de marcação para um tipo de matriz personalizado.

`x:Array` é mais destinado à extensibilidade de idioma geral em XAML. Mas `x:Array` também pode ser útil para especificar valores XAML de determinadas propriedades que usam coleções com suporte a XAML como seu conteúdo de propriedade estruturada. Por exemplo, você pode especificar o conteúdo de uma <xref:System.Collections.IEnumerable> propriedade com um `x:Array` uso.

`x:Array` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. `x:Array` é parcialmente uma exceção a essa regra porque, em vez de fornecer tratamento alternativo de valor de atributo, `x:Array` o fornece tratamento alternativo de seu conteúdo de texto interno. Esse comportamento permite que os tipos que não tenham suporte de um modelo de conteúdo existente sejam agrupados em uma matriz e referenciados posteriormente no code-behind acessando a matriz nomeada; Você pode chamar <xref:System.Array> métodos para obter itens de matriz individuais.

Todas as extensões de marcação em XAML usam as chaves ( {,} `)` em sua sintaxe de atributo, que é a Convenção pela qual um processador XAML reconhece que uma extensão de marcação deve processar o valor do atributo. Para obter mais informações sobre extensões de marcação em geral, consulte [conversores de tipos e extensões de marcação para XAML](type-converters-and-markup-extensions.md).

No XAML 2009, `x:Array` é definido como um primitivo de linguagem em vez de uma extensão de marcação. Para obter mais informações, consulte [tipos internos para primitivos comuns de linguagem XAML](types-for-primitives.md).

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

Normalmente, os elementos de objeto que populam um `x:Array` não são elementos que existem no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] namespace XAML e exigem um mapeamento de prefixo para um namespace XAML não padrão.

Por exemplo, a seguir está uma matriz simples de duas cadeias de caracteres, com o `sys` prefixo (e também `x` ) definido no nível da matriz.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Para tipos personalizados que são usados como elementos de matriz, a classe também deve dar suporte aos requisitos para ser instanciada em XAML como elementos de objeto. Para obter mais informações, consulte [XAML e classes personalizadas para WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).

## <a name="see-also"></a>Confira também

- [Extensões de marcação e XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [Tipos migrados do WPF para System.Xaml](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
