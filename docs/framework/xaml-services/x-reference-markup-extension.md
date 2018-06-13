---
title: Extensão de marcação x:Reference
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562239"
---
# <a name="xreference-markup-extension"></a>Extensão de marcação x:Reference
Faz referência a uma instância que é declarada em outro lugar na marcação XAML. A referência a um elemento `x:Name`.  
  
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
 `x:Reference` fornece suporte de nível de linguagem XAML para um conceito de referência de elemento caso contrário, foi implementado em estruturas específicas, como WPF.  
  
## <a name="xreference-and-wpf"></a>x: referência e WPF  
 No WPF e XAML 2006, referências de elemento são endereçadas pelo recurso de nível da estrutura de <xref:System.Windows.Data.Binding.ElementName%2A> associação. Para a maioria dos aplicativos do WPF e cenários, <xref:System.Windows.Data.Binding.ElementName%2A> associação ainda deve ser usada. Exceções a essa orientação geral podem incluir casos onde não há contexto de dados ou outras considerações de escopo que tornarem a associação de dados impraticável e compilação de marcação não estiver envolvida.  
  
 `x:Reference` uma construção é definida em XAML 2009. No WPF, você pode usar os recursos de XAML 2009, mas apenas para XAML que não é compilado marcação do WPF. Compilação de marcação XAML e o formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de linguagem XAML 2009.
