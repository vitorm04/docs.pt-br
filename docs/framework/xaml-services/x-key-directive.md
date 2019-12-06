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
ms.openlocfilehash: 4ffd7a2922c7f3ba35ccb9ac7ce29a6a00cd99af
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837201"
---
# <a name="xkey-directive"></a>Diretiva x:Key
Identifica os elementos criados e referenciados em um dicionário XAML definido. Adicionar um valor de `x:Key` a um elemento de objeto XAML é a maneira mais comum de identificar um recurso em um dicionário de recurso, por exemplo, em um <xref:System.Windows.ResourceDictionary> do WPF.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Uso de atributo XAML (específico WPF)  
  
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
|`stringKeyValue`|Uma cadeia de caracteres de texto a ser usada como uma chave. A cadeia de texto deve estar de acordo com a [Gramática XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|Dentro dos delimitadores de extensão de marcação {}, um uso de extensão de marcação que fornece um objeto a ser usado como chave. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 `x:Key` suporta o conceito do dicionário de recursos XAML. XAML como uma linguagem não define uma implementação do dicionário de recursos, que é deixado para estruturas específicas de interface do usuário. Para saber mais sobre como os dicionários de recursos XAML são implementados no WPF, consulte [recursos XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 No XAML 2006 e no WPF, `x:Key` deve ser fornecido como um atributo. Você ainda pode usar chaves não sequenciais, mas isso requer um uso de extensão de marcação para fornecer o valor não sequencial no formulário de atributo. Se você estiver usando o XAML 2009, `x:Key` poderá ser especificado como um elemento, para dar suporte explicitamente a dicionários com chave de tipos de objetos diferentes de cadeias de caracteres sem exigir uma extensão de marcação intermediária. Consulte a seção "XAML 2009" neste tópico. O restante da seção de comentários se aplica especificamente à implementação do XAML 2006.  
  
 O valor do atributo de `x:Key` pode ser qualquer cadeia de caracteres definida na [Gramática XamlName](xamlname-grammar.md) ou pode ser um objeto avaliado por meio de uma extensão de marcação. Consulte "Notas de Uso do WPF" para ver um exemplo do WPF.  
  
 Elementos filho de uma elemento pai que é uma implementação de <xref:System.Collections.IDictionary> geralmente devem incluir um atributo `x:Key` que especifica um valor de chave exclusivo dentro desse dicionário. Estruturas podem implementar propriedades chave com alias para substituir `x:Key` em tipos específicos; tipos que definem tais propriedades devem ser atribuídos com <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 O equivalente do código de especificação de `x:Key` é a chave que é usada para o <xref:System.Collections.IDictionary>subjacente. Por exemplo, uma `x:Key` que é aplicada em marcação para um recurso no WPF é equivalente ao valor do parâmetro `key` de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> quando você adiciona o recurso a um WPF <xref:System.Windows.ResourceDictionary> no código.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Elementos filho de uma objeto pai que é uma implementação de <xref:System.Collections.IDictionary>, como <xref:System.Windows.ResourceDictionary> do WPF, normalmente devem incluir um atributo `x:Key` e o valor da chave deverá ser exclusivo nesse dicionário. Há duas exceções notáveis:  
  
- Alguns tipos de WPF declaram uma chave implícita para o uso do dicionário. Por exemplo, <xref:System.Windows.Style> com <xref:System.Windows.Style.TargetType%2A> ou <xref:System.Windows.DataTemplate> com <xref:System.Windows.DataTemplate.DataType%2A>, podem estar em <xref:System.Windows.ResourceDictionary> e usar a chave implícita.  
  
- WPF suporta um conceito do dicionário de recursos mesclados. As chaves podem ser compartilhados entre os dicionários mesclados e o comportamento da chave compartilhada pode ser acessado usando <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Para obter mais informações, consulte [Dicionários de recursos mesclados](../wpf/advanced/merged-resource-dictionaries.md).  
  
 No modelo geral de implementação e de aplicativo XAML do WPF, a exclusividade de chave não é verificada pelo compilador de marcação XAML. Em vez disso, valores `x:Key` ausentes e não exclusivos causam erros do analisador em tempo de carga XAML. No entanto, a manipulação de dicionários do Visual Studio para o WPF geralmente pode observar esses erros na fase de design.  
  
 Observe que, na sintaxe mostrada, o objeto <xref:System.Windows.ResourceDictionary> é implícito em como o processador XAML do WPF produz uma coleção para preencher uma coleção <xref:System.Windows.FrameworkElement.Resources%2A>. Um <xref:System.Windows.ResourceDictionary> normalmente não é fornecido explicitamente como um elemento na marcação, embora possa ser em alguns casos se desejado para fins de esclarecimento (seria um elemento de objeto de coleção entre o elemento de propriedade <xref:System.Windows.FrameworkElement.Resources%2A> e os itens dentro que preenchem o dicionário). Para obter informações sobre por que um objeto de coleção é quase sempre um elemento implícito na marcação, consulte [sintaxe XAML em detalhes](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 Na implementação XAML do WPF, a manipulação de chaves de dicionário de recurso é definida pela classe abstrata <xref:System.Windows.ResourceKey>. No entanto, o processador do WPF XAML produz diferentes tipos de extensão subjacentes para chaves com base em seus usos. Por exemplo, a chave para um <xref:System.Windows.DataTemplate> ou qualquer classe derivada é tratada separadamente, e produz um objeto <xref:System.Windows.DataTemplateKey> distinto.  
  
 As chaves e os nomes usam diretivas e elementos de linguagem diferentes (`x:Key` versus `x:Name`) na definição do XAML básico. As chaves e os nomes também são usados em situações diferentes pela definição do WPF e pela aplicação desses conceitos. Para obter detalhes, consulte [NAMESCOPE XAML do WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Conforme observado anteriormente, o valor de uma chave pode ser fornecido por um extensão de marcação e pode ser diferente de um valor de cadeia de caracteres. Um cenário de exemplo do WPF é que o valor de `x:Key` pode ser um [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Determinados controles expõem uma chave de estilo do tipo para um recurso de estilo personalizado que influencia parte da aparência e do comportamento do controle sem substituir totalmente o estilo. Um exemplo de tal chave é <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 O recurso de dicionário mesclado do WPF apresenta considerações adicionais para a exclusividade das chaves e o comportamento de pesquisa principal. Para obter mais informações, consulte [Dicionários de recursos mesclados](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 O XAML 2009 libera a restrição que `x:Key` sempre ser fornecida no formato de atributo.  
  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja compilado por marcação. O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.  
  
 Em XAML 2009, você pode especificar `x:Key` elementos por meio do seguinte uso:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Uso do elemento XAML (XAML2009 somente)  
  
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
|`keyObject`|Elemento de objeto para o objeto que é usado como a chave para um `object` determinado em um dicionário especializado.|  
  
- O recipiente/pai desse tipo de uso não é mostrado aqui. `object` é esperado ser um filho de um elemento de objeto que representa uma implementação especializada de dicionário. Espera-se que `keyObject` seja uma instância do objeto (ou um valor de um tipo de valor) adequada como a chave de uma determinada implementação especializada de dicionário.  
  
- WPF não implementa os dicionários que exigem esse uso. As chaves de objeto são mais um recurso geral de linguagem XAML, possivelmente útil para certos cenários personalizados onde criar o dicionário em XAML é desejável. Para recursos do WPF, como os estilos implícitos que usam chaves diferentes de cadeia de caracteres para recursos, existem outras técnicas para o estabelecimento ou especificação das chaves e, portanto o uso de uma chave de objeto não é necessário.  
  
- *keyObject* também pode ser um uso de extensão de marcação no formulário de elemento de objeto, em vez de uma instância de objeto direta.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight  
 `x:Key` para Silverlight está documentado separadamente. Para obter mais informações, consulte [XAML namespace (x:) Recursos de linguagem (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Consulte também

- [Recursos XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Recursos e código](../wpf/advanced/resources-and-code.md)
- [Extensão de marcação StaticResource](../wpf/advanced/staticresource-markup-extension.md)
