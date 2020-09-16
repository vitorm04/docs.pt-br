---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 92d1eda62ff394df54d9607bab46d9950681e603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548202"
---
# <a name="xmllang-handling-in-xaml"></a>Tratamento de xml:lang em XAML

O `xml:lang` atributo é um atributo definido por XML que declara as informações de idioma e cultura de um elemento em XML. Esse mesmo significado do atributo persiste em XAML; no entanto, algumas considerações adicionais se aplicam.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|*rfc3066lang*|Uma cadeia de caracteres que é derivada do padrão [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) e identifica um idioma ou uma região de idioma. Quando é o último, o idioma e a região são separados por um único hífen. Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e o formato.|

## <a name="remarks"></a>Comentários

A definição para o `xml:lang` atributo no [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é derivada de `xml:lang` conforme definido como um "atributo especial" pelo World Wide Web Consortium (W3C) para XML. As informações de linguagem e cultura são potencialmente processadas de maneiras diferentes por elementos, dependendo de suas implementações; no entanto, não há nenhum [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processamento padrão do `xml:lang` atributo.

O valor padrão do `xml:lang` atributo é uma cadeia de caracteres vazia no nível de atributo.

Os `xml:lang` efeitos de atributo e o valor do atributo são geralmente perpetuais para elementos filho, quando interpretados por sistemas que atuam em `xml:lang` valores.

Quando interpretado por gravadores XAML dos serviços XAML .NET, um `xml:lang` valor pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos na representação de objeto subjacente; no entanto, esse comportamento depende se o valor especificado para `xml:lang` é uma construção válida para essas classes.

As estruturas podem criar associações entre propriedades definidas pela estrutura e o significado de `xml:lang` em XML aplicando- <xref:System.Windows.Markup.XmlLangPropertyAttribute> se à propriedade.

## <a name="wpf-usage-nodes"></a>Nós de uso do WPF

Para elementos que são classes derivadas de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> , você pode usar a <xref:System.Windows.FrameworkElement.Language%2A> propriedade de dependência equivalente em vez do `xml:lang` atributo. Por padrão, a <xref:System.Windows.FrameworkElement.Language%2A> propriedade usa "en-US" se não for definida de outra forma, por meio da propriedade ou pelo processamento do `xml:lang` atributo.

## <a name="see-also"></a>Confira também

- [Globalização do WPF](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
