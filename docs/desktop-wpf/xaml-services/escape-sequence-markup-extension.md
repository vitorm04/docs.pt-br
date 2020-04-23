---
title: '{}Seqüência de fuga - Extensão de marcação'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071741"
---
# <a name="-escape-sequence--markup-extension"></a>{}Extensão de seqüência de fuga / extensão de marcação

Fornece a seqüência de fuga XAML para valores de atributo. A seqüência de fuga permite que os valores subseqüentes no atributo sejam interpretados como literal.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a>Uso do elemento propriedade XAML

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|*literalValor*|A seqüência literal que segue a seqüência de fuga. Normalmente, esta seqüência contém uma cinta aberta ou fechada ({ ou }).|

## <a name="remarks"></a>Comentários

A seqüência de fuga ({}) é usada para que uma cinta aberta ({) possa ser usada como um caractere literal em XAML.

Os leitores XAML normalmente usam a cinta aberta ({) para denotar o ponto de entrada de uma extensão de marcação; no entanto, primeiro verificam o próximo caractere para determinar se é uma cinta de fechamento (}). Somente quando as duas{}chaves são adjacentes, são consideradas uma seqüência de fuga.

Se a seqüência de fuga for encontrada, o leitor XAML deve processar o restante da seqüência como uma string. No entanto, se a seqüência de fuga for aplicada a um membro que tenha um conversor de tipo, a string pode sofrer conversão de tipo quando for interpretada por um escritor XAML.

A seqüência de escape não é uma extensão de marcação e não é apoiada por uma classe. No entanto, é uma convenção que os leitores XAML (incluindo leitores XAML personalizados) devem respeitar.

Uma marca de cotação (") não pode ser usada como uma seqüência de fuga desta maneira. Se você precisar definir uma marca de cotação como um valor de propriedade para uma propriedade não contente, use a sintaxe do elemento de propriedade e coloque a marca de cotação como uma string dentro do elemento de propriedade ou use uma entidade de caractere XML. Para uma propriedade de conteúdo, a marca de cotação pode ser todo o conteúdo.

A seqüência de fuga ({}) é freqüentemente necessária ao especificar um tipo XML que deve incluir um qualificador de namespace em um local onde uma extensão de marcação XAML pode aparecer. Este local inclui o início de um valor de atributo XAML e em uma extensão de marcação imediatamente após um sinal igual (=). O exemplo a seguir mostra seqüências de fuga para um namespace XML que aparece no início de um valor de atributo XAML.

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a>Confira também

- [Conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions.md)
- [Entidades e XAML de caractere XML](xml-character-entities.md)
