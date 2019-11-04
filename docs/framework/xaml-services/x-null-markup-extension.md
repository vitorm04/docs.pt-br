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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459938"
---
# <a name="xnull-markup-extension"></a>Extensão de marcação x:Null
Especifica `null` como um valor para um membro XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Comentários  
 A palavra-chave para uma referência C# nula C++ em e é nula. A palavra-chave Microsoft Visual Basic para uma referência nula é `Nothing`, mas você sempre usa `{x:Null}` como o uso do XAML, independentemente do idioma code-behind que você associa ao XAML.  
  
 A extensão de marcação de `x:Null` não tem nenhuma propriedade configurável.  
  
 Um uso nulo geralmente é associado à exposição de membro XAML de um valor de <xref:System.Nullable%601> CLR.  
  
 A `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as chaves (`{,}`) para escapar da manipulação de valores de atributo para serem diferentes de literais ou referências de manipulador de eventos. A sintaxe de atributo é a sintaxe usada com mais frequência com essa extensão de marcação. Uma sintaxe de elemento de objeto `<x:Null />` é tecnicamente possível, mas raramente é usada porque a extensão de marcação `x:Null` não tem parâmetros posicionais ou argumentos de construção.  
  
 Para obter informações sobre extensões de marcação, consulte [extensões de marcação e WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Em .NET Framework serviços XAML, o tratamento para essa extensão de marcação é definido pela classe <xref:System.Windows.Markup.NullExtension>.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Observe que `null` não é necessariamente o valor inicial de indefinição para uma propriedade de dependência de tipo de referência. O valor padrão inicial pode variar para cada propriedade de dependência e pode ser baseado em metadados específicos da propriedade. Muitas propriedades de dependência não aceitam `null` como um valor, seja por meio de marcação ou código devido a suas implementações de retorno de chamada de validação. Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Visão geral de XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML do WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
