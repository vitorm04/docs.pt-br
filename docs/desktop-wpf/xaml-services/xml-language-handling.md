---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071440"
---
# <a name="xmllang-handling-in-xaml"></a>Tratamento de xml:lang em XAML

O `xml:lang` atributo é um atributo definido por XML que declara as informações de linguagem e cultura para um elemento em XML. Este mesmo significado do atributo persiste em XAML; no entanto, algumas considerações adicionais se aplicam.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|*rfc3066lang*|Uma string que é derivada do padrão [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) e identifica uma língua ou uma região de idioma. Quando é o último, a língua e a região são separadas por um único hífen. Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e formato.|

## <a name="remarks"></a>Comentários

A definição `xml:lang` para [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] o atributo `xml:lang` em é derivada como um "atributo especial" pelo World Wide Web Consortium (W3C) para XML. As informações de linguagem e cultura são potencialmente processadas de diferentes formas por elementos, dependendo de suas implementações; no entanto, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] não há `xml:lang` processamento padrão do atributo.

O valor padrão `xml:lang` do atributo é uma seqüência de string vazia no nível de atributo.

Os `xml:lang` efeitos atributos e o valor do atributo são geralmente perpetuados `xml:lang` aos elementos infantis, quando interpretados por sistemas que atuam sobre valores.

Quando interpretado por escritores XAML de .NET XAML Services, um `xml:lang` valor pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos na representação de objeto subjacente; no entanto, esse comportamento depende se `xml:lang` o valor especificado é uma construção válida para essas classes.

Os frameworks podem criar associações entre propriedades `xml:lang` definidas por <xref:System.Windows.Markup.XmlLangPropertyAttribute> framework e o significado de em XML aplicando-se à propriedade.

## <a name="wpf-usage-nodes"></a>Dedos de uso do WPF

Para elementos que são <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>classes derivadas de <xref:System.Windows.FrameworkElement.Language%2A> ou , você `xml:lang` pode usar a propriedade de dependência equivalente em vez do atributo. Por padrão, <xref:System.Windows.FrameworkElement.Language%2A> a propriedade usa "en-US" se não for definida de outra `xml:lang` forma, seja através da propriedade ou através do processamento do atributo.

## <a name="see-also"></a>Confira também

- [Globalização do WPF](../../framework/wpf/advanced/globalization-for-wpf.md)
