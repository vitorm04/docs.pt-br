---
title: Tratamento de xml:lang em XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 47dd34db82e796418b68fcf9b28ef3e4d4eaca4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xmllang-handling-in-xaml"></a>Tratamento de xml:lang em XAML
O `xml:lang` atributo é um [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-atributo definido que declara informações de idioma e cultura para um elemento no XML. O mesmo significado do atributo persiste no XAML; No entanto, algumas considerações adicionais se aplicam.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Uma cadeia de caracteres que é derivada de [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) padrão e identifica um idioma ou uma região de idioma. Quando for o último, o idioma e região são separados por um hífen. Consulte <xref:System.Windows.Markup.XmlLanguage> para obter mais informações sobre os valores e o formato.|  
  
## <a name="remarks"></a>Comentários  
 A definição para o `xml:lang` atributo [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é derivado do `xml:lang` como definido como um "atributo especial" pelo [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] para [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Informações de idioma e cultura pode ser processadas de diferentes maneiras por elementos, dependendo de suas implementações; No entanto, não há nenhum padrão [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] o processamento do `xml:lang` atributo.  
  
 O valor padrão de `xml:lang` atributo é uma cadeia de caracteres vazia no nível do atributo.  
  
 O `xml:lang` efeitos de atributo e o valor do atributo em geral são preservadas em elementos filho, interpretado pelos sistemas que atuam em `xml:lang` valores.  
  
 Interpretado pelos autores XAML de serviços XAML do .NET Framework, um `xml:lang` valor pode criar <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> objetos subjacentes do objeto representação; no entanto, esse comportamento depende de se o valor especificado para `xml:lang`é uma construção válida para essas classes.  
  
 Estruturas podem criar associações entre propriedades definidas pelo framework e o significado de `xml:lang` em XML, aplicando <xref:System.Windows.Markup.XmlLangPropertyAttribute> à propriedade.  
  
## <a name="wpf-usage-nodes"></a>Nós de uso do WPF  
 Para elementos que são classes derivadas de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, você pode usar o equivalente <xref:System.Windows.FrameworkElement.Language%2A> propriedade de dependência em vez do `xml:lang` atributo. Por padrão, o <xref:System.Windows.FrameworkElement.Language%2A> propriedade usa "en-US" se ele não é for definido, por meio da propriedade ou por meio do processamento de `xml:lang` atributo.  
  
## <a name="see-also"></a>Consulte também  
 [Globalização para WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
