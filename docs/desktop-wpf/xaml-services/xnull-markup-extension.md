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
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071426"
---
# <a name="xnull-markup-extension"></a>Extensão de marcação x:Null

Especifica `null` como um valor para um membro XAML.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Comentários

A palavra-chave para uma referência nula em C# e C++ é nula. A palavra-chave Microsoft Visual Basic `Nothing`para uma `{x:Null}` referência nula é , mas você sempre usa como o uso XAML, independentemente de qual linguagem de código atrás você associa com o XAML.

A `x:Null` extensão de marcação não tem propriedades definidas.

Um uso nulo é frequentemente associado com a <xref:System.Nullable%601> exposição do membro XAML de um valor CLR.

A `x:Null` extensão de marcação, como todas as extensões`{,}`de marcação XAML, usa as chaves ( ) para escapar do manuseio de valores de atributo suscitados por literais ou referências de manipulador de eventos. Sintaxe de atributo é a sintaxe mais usada com esta extensão de marcação. Uma sintaxe `<x:Null />` de elemento de objeto é `x:Null` tecnicamente possível, mas raramente é usada porque a extensão de marcação não tem parâmetros posicionais ou argumentos de construção.

Para obter informações sobre extensões de marcação, consulte [Extensões de marcação e WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Nos Serviços XAML .NET, o manuseio desta extensão de marcação é definido pela <xref:System.Windows.Markup.NullExtension> classe.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

Observe `null` que não é necessariamente o valor inicial não definido para uma propriedade de dependência de tipo de referência. O valor padrão inicial pode variar para cada propriedade de dependência e pode ser baseado em metadados específicos da propriedade. Muitas propriedades de dependência `null` não aceitam como valor, seja através de marcação ou código por causa de suas implementações de chamada de validação. Para obter mais informações sobre propriedades de dependência, consulte [Visão geral das propriedades de dependência](../../framework/wpf/advanced/dependency-properties-overview.md).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
