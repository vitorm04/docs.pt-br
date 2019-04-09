---
title: Extensão de marcação x:Null
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: e46d8561b62d9137d4fed4df447338a97fc0577b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100802"
---
# <a name="xnull-markup-extension"></a>Extensão de marcação x:Null
Especifica `null` como um valor para um membro XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Comentários  
 A palavra-chave para uma referência nula no C# e [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] é nulo. É a palavra-chave do Microsoft Visual Basic para uma referência nula `Nothing`, mas você sempre usar `{x:Null}` como o uso XAML independentemente qual idioma de lógica que você associar com o XAML.  
  
 O `x:Null` extensão de marcação não possui propriedades configuráveis.  
  
 Um uso nulo geralmente está associado com a exposição de membro XAML de um CLR <xref:System.Nullable%601> valor.  
  
 O `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as chaves (`{,}`) para escapar o tratamento de valores de atributo para ser diferente de literais ou referências de manipulador de eventos. Sintaxe de atributo é a sintaxe mais frequentemente usada com essa extensão de marcação. Uma sintaxe de elemento de objeto `<x:Null />` é tecnicamente possível, mas raramente é usado porque o `x:Null` extensão de marcação não tem parâmetros posicionais ou argumentos de construção.  
  
 Para obter informações sobre extensões de marcação, consulte [extensões de marcação e XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Nos serviços de XAML do .NET Framework, o tratamento para essa extensão de marcação é definido pelo <xref:System.Windows.Markup.NullExtension> classe.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Observe que `null` não é necessariamente o valor inicial para uma propriedade de dependência do tipo de referência. O valor padrão inicial pode variar para cada propriedade de dependência e pode ser com base nos metadados de propriedade específica. Muitas propriedades de dependência não aceitam `null` como um valor, por meio de marcação ou código devido a suas implementações de retorno de chamada de validação. Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Visão geral de XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Extensões de marcação e XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
