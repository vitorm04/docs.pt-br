---
title: Extensão de marcação x:Reference
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938873"
---
# <a name="xreference-markup-extension"></a>Extensão de marcação x:Reference
Faz referência a uma instância que é declarada em outro lugar na marcação XAML. A referência se refere a um elemento `x:Name`.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`instancexName`|O `x:Name` valor (ou valor da <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identificado propriedade) da instância referenciada.|  
  
## <a name="remarks"></a>Comentários  
 `x:Reference` fornece suporte de nível de linguagem XAML para um conceito de referência de elemento caso contrário, foi implementado em estruturas específicas, como o WPF.  
  
## <a name="xreference-and-wpf"></a>x: referência e WPF  
 No WPF e XAML 2006, referências de elemento são endereçadas pelo recurso de nível de estrutura de <xref:System.Windows.Data.Binding.ElementName%2A> associação. Para a maioria dos cenários e aplicativos do WPF <xref:System.Windows.Data.Binding.ElementName%2A> associação ainda deve ser usada. Exceções a essas diretrizes gerais podem incluir casos onde não há contexto de dados ou outras considerações de escopo que tornam impraticável a vinculação de dados e compilação de marcação não está envolvida.  
  
 `x:Reference` Um constructo é definido em XAML 2009. No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não é compilado por marcação do WPF. XAML compilado por marcação e o formato BAML de XAML não têm suporte no momento, as palavras-chave de linguagem XAML 2009 e os recursos.
