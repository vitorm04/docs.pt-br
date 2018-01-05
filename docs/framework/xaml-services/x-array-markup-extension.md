---
title: "Extensão de marcação x:Array"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2304ba68956b705904c72e29a17bdac4536c79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xarray-markup-extension"></a>Extensão de marcação x:Array
Fornece suporte geral para matrizes de objetos por meio de uma extensão de marcação XAML. Isso corresponde do `x:ArrayExtension` tipo XAML em [MS-XAML].  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`typeName`|O nome do tipo que seu `x:Array` conterá. `typeName`pode ser (e geralmente é) o prefixo para uma XAML definições de tipo de namespace que contém o XAML.|  
|`arrayContents`|O conteúdo de itens que é atribuído a intrínseca `ArrayExtension.Items` propriedade. Normalmente, esses itens são especificados como um ou mais elementos de objeto dentro de `x:Array` marcas abertura e fechamento. Os objetos especificados aqui devem ser atribuível ao tipo de XAML especificado em `typeName`.|  
  
## <a name="remarks"></a>Comentários  
 `Type`é um atributo necessário para todos os `x:Array` elementos de objeto. Um `Type` o valor do parâmetro não é necessário usar um `x:Type` extensão de marcação; curto nome do tipo é um tipo XAML, que pode ser especificado como uma cadeia de caracteres.  
  
 A implementação de serviços XAML do .NET Framework, a relação entre o tipo de XAML de entrada e saída CLR <xref:System.Type> da matriz criada é influenciado pelo contexto de serviço para extensões de marcação. A saída <xref:System.Type> é o <xref:System.Xaml.XamlType.UnderlyingType%2A> do tipo de entrada XAML, depois de pesquisar necessários <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e o <xref:System.Windows.Markup.IXamlTypeResolver> fornece o contexto de serviço.  
  
 Quando processado, o conteúdo da matriz é atribuído para a `ArrayExtension.Items` propriedade intrínseca. No <xref:System.Windows.Markup.ArrayExtension> implementação, isso é representado por <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 Na implementação de serviços XAML do .NET Framework, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.Markup.ArrayExtension> classe. <xref:System.Windows.Markup.ArrayExtension>não for fechada e pode ser usado como base para uma implementação de extensão de marcação para um tipo personalizado de matriz.  
  
 `x:Array`é que mais destinado geral extensibilidade de idioma em XAML. Mas `x:Array` também pode ser útil para especificar os valores de determinadas propriedades que usam coleções de suporte para XAML como sua propriedade estruturada conteúdo XAML. Por exemplo, você pode especificar o conteúdo de um <xref:System.Collections.IEnumerable> propriedade com um `x:Array` uso.  
  
 `x:Array` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. `x:Array`é uma exceção a essa regra parcialmente, porque em vez de fornecer o tratamento do valor de atributo alternativo, `x:Array` fornece tratamento alternativo de seu conteúdo de texto interno. Esse comportamento permite que os tipos que não podem ter suporte por um modelo de conteúdo existente para ser agrupadas em uma matriz e referenciados mais tarde no code-behind, acessando a matriz nomeada; Você pode chamar <xref:System.Array> métodos para obter itens individuais de matriz.  
  
 Todas as extensões de marcação XAML usam as chaves ({,}`)` em sua sintaxe de atributo, que é a convenção pela qual um processador XAML reconhece que uma extensão de marcação deve processar o valor do atributo. Para obter mais informações sobre extensões de marcação em geral, consulte [conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 XAML 2009, `x:Array` é definido como uma linguagem primitiva em vez de uma extensão de marcação. Para obter mais informações, consulte [tipos internos para primitivos de linguagem XAML comum](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Normalmente, os elementos de objeto que preenche um `x:Array` não são elementos que existem no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] do namespace XAML e exigem um mapeamento de prefixo para um namespace XAML não padrão.  
  
 Por exemplo, o seguinte é uma matriz simples de duas cadeias de caracteres, com o `sys` prefixo (e também `x`) definidos no nível da matriz.  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 Para tipos personalizados que são usados como elementos de matriz, a classe também deve dar suporte aos requisitos de serem instanciados em XAML, como elementos de objeto. Para obter mais informações, consulte [XAML e Classes personalizadas para WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Consulte também  
 [Extensões de marcação e XAML do WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Tipos migrados do WPF para System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
