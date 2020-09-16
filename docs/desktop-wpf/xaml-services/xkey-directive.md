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
ms.openlocfilehash: 7e4e9cbded01297818f9f01df01e95e94d7dc4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548267"
---
# <a name="xkey-directive"></a>Diretiva x:Key
Identifica exclusivamente os elementos que são criados e referenciados em um dicionário definido por XAML. Adicionar um `x:Key` valor a um elemento de objeto XAML é a maneira mais comum de identificar um recurso em um dicionário de recursos, por exemplo, em um WPF <xref:System.Windows.ResourceDictionary> .  
  
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
|`markupExtensionUsage`|Dentro dos delimitadores de extensão de marcação {} , um uso de extensão de marcação que fornece um objeto a ser usado como chave. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 `x:Key` dá suporte ao conceito de dicionário de recursos XAML. O XAML como um idioma não define uma implementação de dicionário de recursos, que é deixada para estruturas de interface do usuário específicas. Para saber mais sobre como os dicionários de recursos XAML são implementados no WPF, consulte [recursos XAML](../fundamentals/xaml-resources-define.md).  
  
 No XAML 2006 e no WPF, `x:Key` deve ser fornecido como um atributo. Você ainda pode usar chaves sem cadeia de caracteres, mas isso requer um uso de extensão de marcação para fornecer o valor de não cadeia de caracteres no formato de atributo. Se você estiver usando o XAML 2009, `x:Key` pode ser especificado como um elemento, para dar suporte explicitamente a dicionários com chave para os tipos de objeto que não sejam cadeias de caracteres sem exigir uma extensão de marcação intermediária. Consulte a seção "XAML 2009" neste tópico. O restante da seção de comentários se aplica especificamente à implementação do XAML 2006.  
  
 O valor do atributo de `x:Key` pode ser qualquer cadeia de caracteres definida na [Gramática XamlName](xamlname-grammar.md) ou pode ser um objeto avaliado por meio de uma extensão de marcação. Consulte "observações de uso do WPF" para obter um exemplo do WPF.  
  
 Os elementos filho de um elemento pai que é uma <xref:System.Collections.IDictionary> implementação normalmente devem incluir um `x:Key` atributo que especifica um valor de chave exclusivo dentro desse dicionário. As estruturas podem implementar propriedades de chave com alias para substituir por `x:Key` tipos específicos; tipos que definem essas propriedades devem ser atribuídos com <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> .  
  
 O código equivalente de especificar `x:Key` é a chave que é usada para o subjacente <xref:System.Collections.IDictionary> . Por exemplo, um `x:Key` que é aplicado na marcação de um recurso no WPF é equivalente ao valor do `key` parâmetro de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> quando você adiciona o recurso a um WPF <xref:System.Windows.ResourceDictionary> no código.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Os objetos filho de um objeto pai que é uma <xref:System.Collections.IDictionary> implementação, como o WPF <xref:System.Windows.ResourceDictionary> , normalmente devem incluir um `x:Key` atributo e o valor da chave deve ser exclusivo dentro desse dicionário. Há duas exceções notáveis:  
  
- Alguns tipos do WPF declaram uma chave implícita para uso de dicionário. Por exemplo, um <xref:System.Windows.Style> com um <xref:System.Windows.Style.TargetType%2A> , ou um <xref:System.Windows.DataTemplate> com um <xref:System.Windows.DataTemplate.DataType%2A> , pode estar em um <xref:System.Windows.ResourceDictionary> e usar a chave implícita.  
  
- O WPF dá suporte a um conceito de dicionário de recursos mesclado. As chaves podem ser compartilhadas entre os dicionários mesclados e o comportamento de chave compartilhada pode ser acessado usando <xref:System.Windows.FrameworkContentElement.FindResource%2A> . Para obter mais informações, consulte [Dicionários de recursos mesclados](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).  
  
 Na implementação geral do WPF XAML e no modelo de aplicativo, a exclusividade da chave não é verificada pelo compilador de marcação XAML. Em vez disso, valores ausentes ou não exclusivos `x:Key` causam erros de analisador XAML em tempo de carregamento. No entanto, a manipulação de dicionários do Visual Studio para o WPF geralmente pode observar esses erros na fase de design.  
  
 Observe que na sintaxe mostrada, o <xref:System.Windows.ResourceDictionary> objeto é implícito em como o processador XAML do WPF produz uma coleção para popular uma <xref:System.Windows.FrameworkElement.Resources%2A> coleção. <xref:System.Windows.ResourceDictionary>Normalmente, um não é fornecido explicitamente como um elemento na marcação, embora possa estar em alguns casos, se desejar a clareza (seria um elemento de objeto de coleção entre o <xref:System.Windows.FrameworkElement.Resources%2A> elemento de propriedade e os itens dentro do que popular o dicionário). Para obter informações sobre por que um objeto de coleção é quase sempre um elemento implícito na marcação, consulte [sintaxe XAML em detalhes](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail).  
  
 Na implementação XAML do WPF, a manipulação de chaves de dicionário de recursos é definida pela <xref:System.Windows.ResourceKey> classe abstract. No entanto, o processador WPF XAML produz tipos diferentes de extensão subjacentes para chaves com base em seus usos. Por exemplo, a chave de uma <xref:System.Windows.DataTemplate> ou de qualquer classe derivada é tratada separadamente e produz um <xref:System.Windows.DataTemplateKey> objeto distinto.  
  
 Chaves e nomes usam diretivas e elementos de linguagem diferentes ( `x:Key` versus `x:Name` ) na definição XAML básica. As chaves e os nomes também são usados em situações diferentes pela definição do WPF e pela aplicação desses conceitos. Para obter detalhes, consulte [NAMESCOPE XAML do WPF](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes).  
  
 Como mencionado anteriormente, o valor de uma chave pode ser fornecido por meio de uma extensão de marcação e pode ser diferente de um valor de cadeia de caracteres. Um cenário de exemplo do WPF é que o valor de `x:Key` pode ser um [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension). Determinados controles expõem uma chave de estilo desse tipo para um recurso de estilo personalizado que influencia parte da aparência e comportamento desse controle sem substituir totalmente o estilo. Um exemplo de tal chave é <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> .  
  
 O recurso de dicionário mesclado do WPF apresenta considerações adicionais para a exclusividade de chave e o comportamento de pesquisa de chave. Para obter mais informações, consulte [Dicionários de recursos mesclados](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).  
  
## <a name="xaml-2009"></a>XAML 2009  
 O XAML 2009 libera a restrição que `x:Key` sempre é fornecida no formato de atributo.  
  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja compilado por marcação. O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.  
  
 Em XAML 2009, você pode especificar `x:Key` elementos com o uso a seguir:  
  
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
  
- O contêiner/pai para esse tipo de uso não é mostrado aqui. `object` deve ser um filho de um elemento Object que representa uma implementação de dicionário especializada. `keyObject` deve ser uma instância de objeto (ou um valor de um tipo de valor) que seja apropriado como a chave para essa implementação de dicionário especializada específica.  
  
- O WPF não implementa dicionários que exigem esse uso. As chaves de objeto são mais um recurso geral da linguagem XAML, possivelmente útil para determinados cenários de dicionário personalizado em que a criação do dicionário em XAML é desejável. Para recursos do WPF, como estilos implícitos que usam chaves que não são de cadeia de caracteres para recursos, outras técnicas para estabelecer ou especificar as chaves existem, portanto usar uma chave de objeto não é necessário.  
  
- `keyObject` também pode ser um uso de extensão de marcação no formulário de elemento de objeto, em vez de uma instância de objeto direto.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight  
 `x:Key` para o Silverlight é documentado separadamente. Para obter mais informações, consulte [XAML namespace (x:) Recursos de linguagem (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Confira também

- [Recursos XAML](../fundamentals/xaml-resources-define.md)
- [Recursos e código](/dotnet/desktop/wpf/advanced/resources-and-code)
- [Extensão de marcação StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
