---
title: Diretiva x:Key
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: c05f98932ceceeb1530b34a09b1923f2af1378b5
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071496"
---
# <a name="xkey-directive"></a>Diretiva x:Key
Identifica exclusivamente elementos que são criados e referenciados em um dicionário definido pelo XAML. Adicionar `x:Key` um valor a um elemento de objeto XAML é a maneira mais comum <xref:System.Windows.ResourceDictionary>de identificar um recurso em um dicionário de recursos, por exemplo, em um WPF .  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Uso de atributo XAML (específico do WPF)  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`stringKeyValue`|Uma seqüência de texto para usar como chave. A seqüência de texto deve estar em conformidade com a [Gramática XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|Dentro dos delimitadores {}de extensão de marcação, um uso de extensão de marcação que fornece um objeto para usar como chave. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 `x:Key`suporta o conceito de dicionário de recursos XAML. XAML como um idioma não define uma implementação de dicionário de recursos, que é deixada para frameworks específicos de UI. Para saber mais sobre como os dicionários de recursos XAML são implementados no WPF, consulte [XAML Resources](../fundamentals/xaml-resources-define.md).  
  
 Em XAML 2006 e `x:Key` WPF, deve ser fornecido como um atributo. Você ainda pode usar chaves não string, mas isso requer um uso de extensão de marcação para fornecer o valor não string na forma de atributo. Se você estiver usando XAML `x:Key` 2009, pode ser especificado como um elemento, para suportar explicitamente dicionários chaveados por tipos de objeto sem strings sem precisar de um intermediário de extensão de marcação. Consulte a seção "XAML 2009" neste tópico. O restante da seção Observações aplica-se especificamente à implementação do XAML 2006.  
  
 O valor `x:Key` do atributo pode ser qualquer string definida na [Gramática XamlName](xamlname-grammar.md) ou pode ser um objeto avaliado através de uma extensão de marcação. Consulte "Notas de uso do WPF" para obter um exemplo do WPF.  
  
 Os elementos filho de <xref:System.Collections.IDictionary> um elemento pai `x:Key` que é uma implementação devem incluir tipicamente um atributo que especifica um valor-chave único dentro desse dicionário. Os frameworks podem implementar propriedades-chave `x:Key` aliased para substituir em determinados tipos; tipos que definem tais propriedades <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>devem ser atribuídos com .  
  
 O equivalente de `x:Key` código de especificação é a <xref:System.Collections.IDictionary>chave usada para o subjacente . Por exemplo, `x:Key` um que é aplicado na marcação de um recurso `key` no WPF é equivalente ao valor do parâmetro de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> quando você adiciona o recurso a um WPF <xref:System.Windows.ResourceDictionary> em código.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Objetos filho de um <xref:System.Collections.IDictionary> objeto pai que é <xref:System.Windows.ResourceDictionary>uma implementação, `x:Key` como o WPF, normalmente devem incluir um atributo, e o valor-chave deve ser único dentro desse dicionário. Há duas exceções notáveis:  
  
- Alguns tipos de WPF declaram uma chave implícita para o uso do dicionário. Por exemplo, <xref:System.Windows.Style> um <xref:System.Windows.Style.TargetType%2A>com <xref:System.Windows.DataTemplate> um <xref:System.Windows.DataTemplate.DataType%2A>, ou um <xref:System.Windows.ResourceDictionary> com um , pode estar em um e usar a chave implícita.  
  
- O WPF suporta um conceito de dicionário de recursos mesclado. As chaves podem ser compartilhadas entre os dicionários mesclados e o <xref:System.Windows.FrameworkContentElement.FindResource%2A>comportamento de chave compartilhada pode ser acessado usando . Para obter mais informações, consulte [Dicionários de recursos mesclados](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 No modelo geral de implementação e aplicativo do WPF XAML, a exclusividade chave não é verificada pelo compilador de marcação XAML. Em vez disso, `x:Key` valores ausentes ou não exclusivos causam erros de analisador XAML em tempo de carga. No entanto, o manuseio do Visual Studio de dicionários para WPF pode muitas vezes notar tais erros na fase de design.  
  
 Observe que na sintaxe <xref:System.Windows.ResourceDictionary> mostrada, o objeto está implícito em como o <xref:System.Windows.FrameworkElement.Resources%2A> processador WPF XAML produz uma coleção para preencher uma coleção. A <xref:System.Windows.ResourceDictionary> não é tipicamente fornecido explicitamente como um elemento na marcação, embora possa ser em alguns casos <xref:System.Windows.FrameworkElement.Resources%2A> se desejado para clareza (seria um elemento objeto de coleção entre o elemento de propriedade e os itens dentro desse dicionário). Para obter informações sobre por que um objeto de coleta é quase sempre um elemento implícito na marcação, consulte [XAML Sintaxe em detalhes](../../framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Na implementação do WPF XAML, o manuseio de <xref:System.Windows.ResourceKey> chaves de dicionário de recursos é definido pela classe abstrata. No entanto, o processador WPF XAML produz diferentes tipos de extensão subjacentes para chaves com base em seus usos. Por exemplo, a <xref:System.Windows.DataTemplate> chave para uma ou qualquer classe derivada é <xref:System.Windows.DataTemplateKey> manuseada separadamente e produz um objeto distinto.  
  
 Chaves e nomes usam diferentes`x:Key` diretivas e elementos de linguagem (versus `x:Name`) na definição xaml básica. Chaves e nomes também são usados em diferentes situações pela definição do WPF e aplicação desses conceitos. Para obter detalhes, consulte [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Como dito anteriormente, o valor de uma chave pode ser fornecido através de uma extensão de marcação e pode ser diferente de um valor de string. Um exemplo do cenário wpf `x:Key` é que o valor de pode ser um [ComponentResourceKey](../../framework/wpf/advanced/componentresourcekey-markup-extension.md). Certos controles expõem uma chave de estilo desse tipo para um recurso de estilo personalizado que influencia parte da aparência e comportamento desse controle sem substituir totalmente o estilo. Um exemplo dessa chave <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>é.  
  
 O recurso de dicionário mesclado do WPF introduz considerações adicionais para a singularidade chave e o comportamento de pesquisa chave. Para obter mais informações, consulte [Dicionários de recursos mesclados](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 relaxa `x:Key` a restrição que sempre é fornecida na forma de atributo.  
  
 No WPF, você pode usar os recursos do XAML 2009, mas apenas para XAML que não é compilado por marcação. O XAML compilado por marcação para WPF e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do XAML 2009.  
  
 Em XAML 2009, `x:Key` você pode especificar elementos através do seguinte uso:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Uso do elemento XAML (somente XAML 2009)  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`keyObject`|Elemento objeto para o objeto que é `object` usado como chave para um dado em um dicionário especializado.|  
  
- O recipiente/pai para este tipo de uso não é mostrado aqui. `object`espera-se que seja filho de um elemento objeto que representa uma implementação de dicionário especializado. `keyObject`espera-se que seja uma instância de objeto (ou um valor de um tipo de valor) que seja apropriada como a chave para essa implementação de dicionário especializado em particular.  
  
- O WPF não implementa dicionários que requerem esse uso. As teclas de objeto são mais uma característica geral da linguagem XAML, possivelmente útil para certos cenários de dicionário personalizados onde a criação do dicionário em XAML é desejável. Para recursos WPF, como estilos implícitos que usam chaves não-string para recursos, outras técnicas para estabelecer ou especificar as chaves existem, portanto, o uso de uma chave de objeto não é necessário.  
  
- `keyObject`também poderia ser um uso de extensão de marcação na forma de elemento de objeto, em vez de uma instância de objeto direto.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso da luz de prata  
 `x:Key`para Silverlight é documentado separadamente. Para obter mais informações, consulte [XAML Namespace (x:) Características da linguagem (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Confira também

- [Recursos XAML](../fundamentals/xaml-resources-define.md)
- [Recursos e código](../../framework/wpf/advanced/resources-and-code.md)
- [Extensão de marcação StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md)
