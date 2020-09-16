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
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549438"
---
# <a name="xnull-markup-extension"></a>Extensão de marcação x:Null

Especifica `null` como um valor para um membro XAML.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Comentários

A palavra-chave para uma referência nula em C# e C++ é nula. A palavra-chave Microsoft Visual Basic para uma referência nula é `Nothing` , mas você sempre usa `{x:Null}` como o uso do XAML, independentemente do idioma code-behind que você associar ao XAML.

A `x:Null` extensão de marcação não tem nenhuma propriedade configurável.

Um uso nulo geralmente é associado à exposição de membro XAML de um <xref:System.Nullable%601> valor CLR.

A `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as chaves ( `{,}` ) para escapar a manipulação de valores de atributo para que sejam diferentes de literais ou referências de manipulador de eventos. A sintaxe de atributo é a sintaxe usada com mais frequência com essa extensão de marcação. Uma sintaxe de elemento de objeto `<x:Null />` é tecnicamente possível, mas raramente é usada porque a `x:Null` extensão de marcação não tem parâmetros posicionais ou argumentos de construção.

Para obter informações sobre extensões de marcação, consulte [extensões de marcação e WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).

Nos serviços XAML do .NET, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.NullExtension> classe.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

Observe que `null` não é necessariamente o valor inicial de redefinição para uma propriedade de dependência de tipo de referência. O valor padrão inicial pode variar para cada propriedade de dependência e pode ser baseado em metadados específicos da propriedade. Muitas propriedades de dependência não são aceitas `null` como um valor, seja por meio de marcação ou código, devido a suas implementações de retorno de chamada de validação. Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](/dotnet/desktop/wpf/advanced/dependency-properties-overview).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
