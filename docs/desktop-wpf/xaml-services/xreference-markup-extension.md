---
title: Extensão de marcação x:Reference
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071377"
---
# <a name="xreference-markup-extension"></a>Extensão de marcação x:Reference

Faz referência a uma instância que é declarada em outro lugar na marcação XAML. A referência refere-se a `x:Name`um elemento.

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
|`instancexName`|O `x:Name` valor (ou <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>valor da propriedade -identificada) da instância referenciada.|

## <a name="remarks"></a>Comentários

`x:Reference`fornece suporte em nível de linguagem XAML para um conceito de referência de elemento que foi implementado de outra forma em estruturas específicas, como o WPF.

## <a name="xreference-and-wpf"></a>x:Referência e WPF

No WPF e no XAML 2006, as referências dos <xref:System.Windows.Data.Binding.ElementName%2A> elementos são abordadas pelo recurso de nível de estrutura da vinculação. Para a maioria dos aplicativos <xref:System.Windows.Data.Binding.ElementName%2A> e cenários do WPF, a vinculação ainda deve ser usada. Exceções a esta orientação geral podem incluir casos em que há contexto de dados ou outras considerações de escopo que tornam a vinculação de dados impraticável e onde a compilação de marcação não está envolvida.

`x:Reference`é uma construção definida em XAML 2009. No WPF, você pode usar os recursos do XAML 2009, mas apenas para XAML que não é compilado por marcação WPF. O XAML compilado por marcação e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do idioma XAML 2009.
