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
ms.openlocfilehash: 23c483daed0156dd29134b255e9da2f7922980ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492776"
---
# <a name="xkey-directive"></a>Diretiva x:Key
Identifica os elementos que são criados e referenciados em um dicionário definido pelo XAML. Adicionando um `x:Key` valor para um elemento de objeto XAML é a maneira mais comum para identificar um recurso em um dicionário de recursos, por exemplo, em um WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Uso do atributo XAML (específico WPF)  
  
```  
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
|`stringKeyValue`|Uma cadeia de caracteres de texto a ser usado como uma chave. A cadeia de caracteres de texto deve estar em conformidade com o [gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
|`markupExtensionUsage`|Dentro dos delimitadores de extensão de marcação {}, um uso de extensão de marcação que fornece um objeto a ser usado como uma chave. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 `x:Key` suporta o conceito de dicionário de recursos XAML. XAML como uma linguagem não define uma implementação de dicionário de recursos, que é deixada para estruturas específicas de interface do usuário. Para saber mais sobre como dicionários de recursos XAML são implementados em WPF, consulte [recursos XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 No XAML 2006 e o WPF, `x:Key` deve ser fornecido como um atributo. Você ainda pode usar chaves não sequenciais, mas isso requer o uso de uma extensão de marcação para fornecer o valor não sequencial no formulário de atributo. Se você estiver usando o XAML 2009, `x:Key` pode ser especificado como um elemento oferecer suporte explícito a dicionários chaveados por tipos de objeto diferente de cadeias de caracteres sem a necessidade de uma extensão de marcação intermediária. Consulte a seção "XAML 2009" neste tópico. O restante da seção Observações se aplica especificamente à implementação do XAML 2006.  
  
 O valor do atributo `x:Key` pode ser qualquer cadeia de caracteres definida na [gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md) ou pode ser um objeto avaliado através de uma extensão de marcação. Consulte "Notas de uso do WPF" para obter um exemplo do WPF.  
  
 Elementos filho de um elemento pai que é uma <xref:System.Collections.IDictionary> implementação geralmente deve incluir um `x:Key` atributo que especifica um valor de chave exclusivo dentro desse dicionário. Estruturas podem implementar propriedades chave com alias para substituir `x:Key` em tipos específicos; tipos que definem tais propriedades devem ser atribuídos com <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 O equivalente em código de especificação `x:Key` é a chave que é usada para subjacente <xref:System.Collections.IDictionary>. Por exemplo, um `x:Key` que é aplicada em marcação para um recurso no WPF é equivalente ao valor da `key` parâmetro do <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> quando você adiciona o recurso a um WPF <xref:System.Windows.ResourceDictionary> no código.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Objetos filho de um pai do objeto que é um <xref:System.Collections.IDictionary> implementação, como o WPF <xref:System.Windows.ResourceDictionary>, normalmente devem incluir um `x:Key` atributo e o valor da chave devem ser exclusivo dentro desse dicionário. Há duas exceções notáveis:  
  
-   Alguns tipos WPF declaram uma chave implícita para uso do dicionário. Por exemplo, uma <xref:System.Windows.Style> com um <xref:System.Windows.Style.TargetType%2A>, ou uma <xref:System.Windows.DataTemplate> com um <xref:System.Windows.DataTemplate.DataType%2A>, podem estar em um <xref:System.Windows.ResourceDictionary> e usar a chave implícita.  
  
-   WPF suporta um conceito do dicionário de recursos mesclados. As chaves podem ser compartilhadas entre os dicionários mesclados e o comportamento da chave compartilhada pode ser acessado usando <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Para obter mais informações, consulte [Dicionários de recursos mesclados](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 No WPF XAML aplicativo e a implementação do modelo geral, a exclusividade de chave não é verificada pelo compilador de marcação XAML. Em vez disso, ausente ou não exclusivo `x:Key` valores causam erros de analisador XAML do tempo de carregamento. No entanto, a manipulação do Visual Studio de dicionários para o WPF frequentemente pode observar tais erros na fase de design.  
  
 Observe que na sintaxe mostrada, o <xref:System.Windows.ResourceDictionary> objeto está implícito em como o processador de XAML WPF produz uma coleção para preencher um <xref:System.Windows.FrameworkElement.Resources%2A> coleção. Um <xref:System.Windows.ResourceDictionary> normalmente não é fornecido explicitamente como um elemento na marcação, embora ele possa ser em alguns casos, se quisesse para fins de esclarecimento (seria um elemento de objeto de coleção entre o <xref:System.Windows.FrameworkElement.Resources%2A> popular de elemento de propriedade e os itens que o dicionário). Para obter informações sobre por que um objeto de coleção é quase sempre um elemento implícito na marcação, consulte [sintaxe de XAML em detalhes](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Na implementação do WPF XAML, o tratamento para chaves de dicionário de recurso é definido pelo <xref:System.Windows.ResourceKey> classe abstrata. No entanto, o processador de WPF XAML produz diferentes tipos de extensão subjacentes para chaves com base em seus usos. Por exemplo, a chave para um <xref:System.Windows.DataTemplate> ou qualquer classe derivada é tratada separadamente e produz um distintos <xref:System.Windows.DataTemplateKey> objeto.  
  
 As chaves e os nomes usam diretivas diferentes e elementos de linguagem (`x:Key` versus `x:Name`) na definição do XAML básica. Chaves e nomes também são usados em situações diferentes pela definição do WPF e aplicação desses conceitos. Para obter detalhes, consulte [Namescopes de XAML do WPF](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Conforme mencionado anteriormente, o valor de uma chave pode ser fornecido por meio de uma extensão de marcação e pode ser diferente de um valor de cadeia de caracteres. Um cenário de WPF de exemplo que é o valor da `x:Key` pode ser uma [ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md). Determinados controles expõem uma chave de estilo desse tipo para um recurso de estilo personalizado que influencia parte da aparência e comportamento do controle sem substituir totalmente o estilo. Um exemplo de tal chave é <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 O recurso de dicionário mesclado do WPF apresenta considerações adicionais para exclusividade de chave e o comportamento de pesquisa de chave. Para obter mais informações, consulte [Dicionários de recursos mesclados](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 alivia a restrição que `x:Key` sempre seja fornecido no formulário de atributo.  
  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não é compilado por marcação. Compilado por marcação XAML para WPF e o formato BAML de XAML têm suporte no momento, as palavras-chave do XAML 2009 e os recursos.  
  
 Em XAML 2009, você pode especificar `x:Key` elementos por meio do uso a seguir:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Uso do elemento XAML (somente de XAML 2009)  
  
```  
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
|`keyObject`|Elemento de objeto para o objeto que é usado como a chave para um determinado `object` em um dicionário especializado.|  
  
-   O recipiente/pai para esse tipo de uso não é mostrado aqui. `object` deve ser um filho de um elemento de objeto que representa uma implementação especializada de dicionário. `keyObject` deve ser uma instância do objeto (ou um valor de um tipo de valor) adequada como a chave para que a implementação especializada de dicionário específico.  
  
-   WPF não implementa os dicionários que exigem esse uso. Chaves de objeto é mais um recurso geral da linguagem XAML, possivelmente útil para certos cenários personalizados onde criar o dicionário em XAML é desejável. Para recursos WPF, como estilos implícitos que usam chaves não cadeia de caracteres para recursos, outras técnicas para o estabelecimento ou especificação das chaves existem, portanto não é necessário usar uma chave de objeto.  
  
-   *keyObject* também poderia ser um uso de extensão de marcação no formulário de elemento de objeto, em vez de uma instância de objeto direto.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight  
 `x:Key` para o Silverlight está documentado separadamente. Para obter mais informações, consulte [Namespace de XAML (x) Recursos de linguagem (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também
- [Recursos XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Recursos e código](../../../docs/framework/wpf/advanced/resources-and-code.md)
- [Extensão de marcação StaticResource](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
