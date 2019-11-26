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
ms.openlocfilehash: 8321a09db31c9f6d2103a252a195fcdbf8da3e66
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283851"
---
# <a name="xkey-directive"></a>Diretiva x:Key
Identifica exclusivamente os elementos que são criados e referenciados em um dicionário definido por XAML. Adicionar um valor de `x:Key` a um elemento de objeto XAML é a maneira mais comum de identificar um recurso em um dicionário de recursos, por exemplo, em um <xref:System.Windows.ResourceDictionary>do WPF.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Uso do atributo XAML (específico do WPF)  
  
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
|`stringKeyValue`|Uma cadeia de texto a ser usada como chave. A cadeia de texto deve estar de acordo com a [Gramática XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|Dentro dos delimitadores de extensão de marcação {}, um uso de extensão de marcação que fornece um objeto a ser usado como chave. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 `x:Key` dá suporte ao conceito de dicionário de recursos XAML. O XAML como um idioma não define uma implementação de dicionário de recursos, que é deixada para estruturas de interface do usuário específicas. Para saber mais sobre como os dicionários de recursos XAML são implementados no WPF, consulte [recursos XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 No XAML 2006 e no WPF, `x:Key` deve ser fornecido como um atributo. Você ainda pode usar chaves sem cadeia de caracteres, mas isso requer um uso de extensão de marcação para fornecer o valor de não cadeia de caracteres no formato de atributo. Se você estiver usando o XAML 2009, `x:Key` poderá ser especificado como um elemento, para dar suporte explicitamente a dicionários com chave de tipos de objetos diferentes de cadeias de caracteres sem exigir uma extensão de marcação intermediária. Consulte a seção "XAML 2009" neste tópico. O restante da seção de comentários se aplica especificamente à implementação do XAML 2006.  
  
 O valor do atributo de `x:Key` pode ser qualquer cadeia de caracteres definida na [Gramática XamlName](xamlname-grammar.md) ou pode ser um objeto avaliado por meio de uma extensão de marcação. Consulte "observações de uso do WPF" para obter um exemplo do WPF.  
  
 Os elementos filho de um elemento pai que é uma implementação de <xref:System.Collections.IDictionary> normalmente devem incluir um atributo `x:Key` que especifica um valor de chave exclusivo dentro desse dicionário. As estruturas podem implementar propriedades de chave com alias para substituir `x:Key` em tipos específicos; tipos que definem essas propriedades devem ser atribuídos com <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 O código equivalente à especificação de `x:Key` é a chave usada para o <xref:System.Collections.IDictionary>subjacente. Por exemplo, um `x:Key` aplicado na marcação de um recurso no WPF é equivalente ao valor do parâmetro `key` de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> quando você adiciona o recurso a um <xref:System.Windows.ResourceDictionary> do WPF no código.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Os objetos filho de um objeto pai que é uma implementação <xref:System.Collections.IDictionary>, como o <xref:System.Windows.ResourceDictionary>do WPF, normalmente devem incluir um atributo `x:Key`, e o valor da chave deve ser exclusivo dentro desse dicionário. Há duas exceções notáveis:  
  
- Alguns tipos do WPF declaram uma chave implícita para uso de dicionário. Por exemplo, um <xref:System.Windows.Style> com um <xref:System.Windows.Style.TargetType%2A>, ou um <xref:System.Windows.DataTemplate> com um <xref:System.Windows.DataTemplate.DataType%2A>, pode estar em um <xref:System.Windows.ResourceDictionary> e usar a chave implícita.  
  
- O WPF dá suporte a um conceito de dicionário de recursos mesclado. As chaves podem ser compartilhadas entre os dicionários mesclados e o comportamento de chave compartilhada pode ser acessado usando <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Para obter mais informações, consulte [Dicionários de recursos mesclados](../wpf/advanced/merged-resource-dictionaries.md).  
  
 Na implementação geral do WPF XAML e no modelo de aplicativo, a exclusividade da chave não é verificada pelo compilador de marcação XAML. Em vez disso, valores de `x:Key` ausentes ou não exclusivos causam erros de analisador XAML em tempo de carregamento. No entanto, a manipulação de dicionários do Visual Studio para o WPF geralmente pode observar esses erros na fase de design.  
  
 Observe que na sintaxe mostrada, o objeto <xref:System.Windows.ResourceDictionary> é implícito em como o processador XAML do WPF produz uma coleção para popular uma coleção de <xref:System.Windows.FrameworkElement.Resources%2A>. Um <xref:System.Windows.ResourceDictionary> normalmente não é fornecido explicitamente como um elemento na marcação, embora possa estar em alguns casos, se desejado para fins de clareza (seria um elemento de objeto de coleção entre o elemento de propriedade <xref:System.Windows.FrameworkElement.Resources%2A> e os itens dentro que preenchem o dicionário). Para obter informações sobre por que um objeto de coleção é quase sempre um elemento implícito na marcação, consulte [sintaxe XAML em detalhes](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 Na implementação XAML do WPF, a manipulação de chaves de dicionário de recursos é definida pela classe abstrata <xref:System.Windows.ResourceKey>. No entanto, o processador WPF XAML produz tipos diferentes de extensão subjacentes para chaves com base em seus usos. Por exemplo, a chave para um <xref:System.Windows.DataTemplate> ou qualquer classe derivada é tratada separadamente e produz um objeto <xref:System.Windows.DataTemplateKey> distinto.  
  
 Chaves e nomes usam diferentes diretivas e elementos de linguagem (`x:Key` versus `x:Name`) na definição XAML básica. As chaves e os nomes também são usados em situações diferentes pela definição do WPF e pela aplicação desses conceitos. Para obter detalhes, consulte [NAMESCOPE XAML do WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Como mencionado anteriormente, o valor de uma chave pode ser fornecido por meio de uma extensão de marcação e pode ser diferente de um valor de cadeia de caracteres. Um cenário de exemplo do WPF é que o valor de `x:Key` pode ser um [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Determinados controles expõem uma chave de estilo desse tipo para um recurso de estilo personalizado que influencia parte da aparência e comportamento desse controle sem substituir totalmente o estilo. Um exemplo de tal chave é <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 O recurso de dicionário mesclado do WPF apresenta considerações adicionais para a exclusividade de chave e o comportamento de pesquisa de chave. Para obter mais informações, consulte [Dicionários de recursos mesclados](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 O XAML 2009 libera a restrição que `x:Key` sempre ser fornecida no formato de atributo.  
  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja compilado por marcação. O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.  
  
 Em XAML 2009, você pode especificar `x:Key` elementos por meio do seguinte uso:  
  
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
|`keyObject`|Elemento Object para o objeto que é usado como a chave para um determinado `object` em um dicionário especializado.|  
  
- O contêiner/pai para esse tipo de uso não é mostrado aqui. `object` deve ser um filho de um elemento Object que representa uma implementação de dicionário especializada. Espera-se que `keyObject` seja uma instância de objeto (ou um valor de um tipo de valor) que seja apropriado como a chave para essa implementação de dicionário especializada específica.  
  
- O WPF não implementa dicionários que exigem esse uso. As chaves de objeto são mais um recurso geral da linguagem XAML, possivelmente útil para determinados cenários de dicionário personalizado em que a criação do dicionário em XAML é desejável. Para recursos do WPF, como estilos implícitos que usam chaves que não são de cadeia de caracteres para recursos, outras técnicas para estabelecer ou especificar as chaves existem, portanto usar uma chave de objeto não é necessário.  
  
- *keyObject* também pode ser um uso de extensão de marcação no formulário de elemento de objeto, em vez de uma instância de objeto direta.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight  
 o `x:Key` para Silverlight é documentado separadamente. Para obter mais informações, consulte [XAML namespace (x:) Recursos de linguagem (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também

- [Recursos XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Recursos e código](../wpf/advanced/resources-and-code.md)
- [Extensão de marcação StaticResource](../wpf/advanced/staticresource-markup-extension.md)
