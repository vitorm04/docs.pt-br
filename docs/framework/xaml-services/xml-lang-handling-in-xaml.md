---
title: Tratamento de xml:lang em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 508c1151b1b196a84b7c3a576e18d10c0a706fad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692384"
---
# <a name="xmllang-handling-in-xaml"></a>Tratamento de xml:lang em XAML
O `xml:lang` atributo é um [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-atributo definido que declara as informações de idioma e cultura de um elemento no XML. Esse mesmo significado do atributo persiste no XAML; No entanto, algumas considerações adicionais se aplicam.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Uma cadeia de caracteres que é derivada de [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) padrão e identifica um idioma ou uma região de idioma. Quando for o último, o idioma e região são separados por um hífen. Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e formato.|  
  
## <a name="remarks"></a>Comentários  
 A definição para o `xml:lang` de atributo em [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é derivado de `xml:lang` como definido como um "atributo especial" pela [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] para [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Informações de idioma e cultura pode ser processadas de diferentes maneiras por elementos, dependendo de suas implementações; No entanto, não há nenhum padrão [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processamento do `xml:lang` atributo.  
  
 O valor padrão de `xml:lang` atributo é uma cadeia de caracteres vazia no nível de atributo.  
  
 O `xml:lang` efeitos do atributo e o valor do atributo em geral são preservadas em elementos filho, quando interpretados por sistemas que atuam em `xml:lang` valores.  
  
 Ao ser interpretado por gravadores XAML de serviços de XAML do .NET Framework, um `xml:lang` valor pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos subjacente representação do objeto; no entanto, esse comportamento depende de se o valor especificado para `xml:lang`é uma construção válida para essas classes.  
  
 Estruturas podem criar associações entre propriedades definidos pela estrutura e o significado dos `xml:lang` no XML por meio da aplicação <xref:System.Windows.Markup.XmlLangPropertyAttribute> à propriedade.  
  
## <a name="wpf-usage-nodes"></a>Nós de uso do WPF  
 Para elementos que são classes derivadas de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, você pode usar o equivalente <xref:System.Windows.FrameworkElement.Language%2A> propriedade de dependência em vez do `xml:lang` atributo. Por padrão, o <xref:System.Windows.FrameworkElement.Language%2A> propriedade usa "en-US", se ele não é for definido, por meio da propriedade ou por meio do processamento de `xml:lang` atributo.  
  
## <a name="see-also"></a>Consulte também
- [Globalização para WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
