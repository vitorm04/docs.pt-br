---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 98bfabba96e5805b96c63eb02233b15eae233cc0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740569"
---
# <a name="xmllang-handling-in-xaml"></a>Tratamento de xml:lang em XAML
O atributo `xml:lang` é um atributo definido por XML que declara as informações de idioma e cultura de um elemento em XML. Esse mesmo significado do atributo persiste em XAML; no entanto, algumas considerações adicionais se aplicam.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Uma cadeia de caracteres que é derivada do padrão [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) e identifica um idioma ou uma região de idioma. Quando é o último, o idioma e a região são separados por um único hífen. Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e o formato.|  
  
## <a name="remarks"></a>Comentários  
 A definição do atributo `xml:lang` no [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é derivada de `xml:lang` conforme definido como um "atributo especial" pelo World Wide Web Consortium (W3C) for XML. As informações de linguagem e cultura são potencialmente processadas de maneiras diferentes por elementos, dependendo de suas implementações; no entanto, não há nenhum [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processamento padrão do atributo `xml:lang`.  
  
 O valor padrão do atributo `xml:lang` é uma cadeia de caracteres vazia no nível de atributo.  
  
 Os efeitos de atributo `xml:lang` e o valor do atributo são geralmente perpetuados para elementos filho, quando interpretados por sistemas que atuam em valores `xml:lang`.  
  
 Quando interpretado por gravadores XAML de .NET Framework serviços XAML, um valor de `xml:lang` pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos na representação de objeto subjacente; no entanto, esse comportamento depende se o valor especificado para `xml:lang` é uma construção válida para essas classes.  
  
 As estruturas podem criar associações entre propriedades definidas pela estrutura e o significado de `xml:lang` em XML aplicando <xref:System.Windows.Markup.XmlLangPropertyAttribute> à propriedade.  
  
## <a name="wpf-usage-nodes"></a>Nós de uso do WPF  
 Para elementos que são classes derivadas de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, você pode usar a propriedade de dependência <xref:System.Windows.FrameworkElement.Language%2A> equivalente em vez do atributo de `xml:lang`. Por padrão, a propriedade <xref:System.Windows.FrameworkElement.Language%2A> usa "en-US" se não for definida de outra forma, por meio da propriedade ou pelo processamento do atributo `xml:lang`.  
  
## <a name="see-also"></a>Consulte também

- [Globalização para WPF](../wpf/advanced/globalization-for-wpf.md)
