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
ms.openlocfilehash: 94cfaee9a0a9a9f3892b9df50ac59103709a3b14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562343"
---
# <a name="xnull-markup-extension"></a>Extensão de marcação x:Null
Especifica `null` como um valor para um membro XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Comentários  
 A palavra-chave para uma referência nula em c# e [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] é nulo. A palavra-chave do Microsoft Visual Basic para uma referência nula é `Nothing`, mas você sempre usar `{x:Null}` como o uso XAML independentemente qual idioma de lógica você associar o XAML.  
  
 O `x:Null` extensão de marcação não possui propriedades configuráveis.  
  
 Um uso nulo costuma está associado a exposição de membro XAML de um CLR <xref:System.Nullable%601> valor.  
  
 O `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as chaves (`{,}`) para escapar o tratamento de valores de atributo para ser diferente de literais ou referências de manipulador de eventos. Sintaxe de atributo é a sintaxe mais frequentemente usada com essa extensão de marcação. Uma sintaxe de elemento de objeto `<x:Null />` é tecnicamente possível, mas raramente é usada, pois o `x:Null` extensão de marcação não tem parâmetros posicionais ou argumentos de construção.  
  
 Para obter informações sobre extensões de marcação, consulte [extensões de marcação e WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Em serviços de XAML do .NET Framework, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.Markup.NullExtension> classe.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Observe que `null` não é necessariamente o valor inicial para uma propriedade de dependência de tipo de referência. O valor padrão inicial pode variar para cada propriedade de dependência e pode ser com base nos metadados de propriedade específica. Muitas propriedades de dependência não aceitam `null` como um valor, por meio de marcação ou código devido a suas implementações de retorno de chamada de validação. Para obter mais informações sobre propriedades de dependência, consulte [visão geral de propriedades de dependência](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML do WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
