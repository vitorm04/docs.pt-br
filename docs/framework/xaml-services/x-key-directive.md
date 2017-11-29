---
title: Diretiva x:Key
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5e2ad03fcb52db1ffdd01849381a392187082991
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xkey-directive"></a>Diretiva x:Key
Identifica os elementos que são criados e referenciados em um dicionário definido em XAML. Adicionando um `x:Key` valor para um elemento de objeto XAML é a maneira mais comum para identificar um recurso em um dicionário de recurso, por exemplo, em um WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Uso do atributo XAML (específico para WPF)  
  
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
|`stringKeyValue`|Uma cadeia de caracteres de texto a ser usado como uma chave. A cadeia de caracteres de texto deve estar de acordo com o [gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
|`markupExtensionUsage`|Dentro de {de delimitadores de extensão de marcação, um uso de extensão de marcação que fornece um objeto a ser usado como uma chave. Consulte Observações.|  
  
## <a name="remarks"></a>Comentários  
 `x:Key`oferece suporte ao conceito de dicionário de recurso XAML. XAML como uma linguagem não define uma implementação de dicionário de recurso, que é da esquerda para estruturas de interface de usuário específicas. Para saber mais sobre como os dicionários de recursos XAML são implementados no WPF, consulte [recursos XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Em 2006 XAML e WPF, `x:Key` deve ser fornecido como um atributo. Você ainda pode usar chaves não-String, mas isso requer o uso de uma extensão de marcação para fornecer o valor não na forma de atributo. Se você estiver usando XAML 2009, `x:Key` pode ser especificado como um elemento dar suporte a dicionários chaveados por tipos de objeto que explicitamente cadeias de caracteres sem a necessidade de uma extensão de marcação intermediária. Consulte a seção "XAML 2009" neste tópico. O restante da seção de comentários se aplica especificamente para a implementação de 2006 do XAML.  
  
 O valor do atributo `x:Key` pode ser qualquer cadeia de caracteres definida no [gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md) ou um objeto avaliado por meio de uma extensão de marcação. Consulte "Observações de uso do WPF" para obter um exemplo do WPF.  
  
 Elementos filho de um elemento pai que é uma <xref:System.Collections.IDictionary> implementação normalmente deve incluir um `x:Key` atributo que especifica um valor de chave exclusivo dentro desse dicionário. Estruturas podem implementar propriedades de chave de um alias para substituir `x:Key` em tipos específicos; tipos que definem propriedades devem ser atribuídos com <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 O equivalente em código especificando `x:Key` é a chave que é usada para subjacente <xref:System.Collections.IDictionary>. Por exemplo, um `x:Key` que é aplicada em marcação para um recurso no WPF é equivalente ao valor da `key` parâmetro <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> quando você adiciona o recurso a um WPF <xref:System.Windows.ResourceDictionary> no código.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Objetos filho de um pai do objeto que é um <xref:System.Collections.IDictionary> implementação, como o WPF <xref:System.Windows.ResourceDictionary>, normalmente deve incluir um `x:Key` atributo e o valor da chave devem ser exclusivo dentro desse dicionário. Há duas exceções importantes:  
  
-   Alguns tipos WPF declarar uma chave implícita para uso do dicionário. Por exemplo, um <xref:System.Windows.Style> com um <xref:System.Windows.Style.TargetType%2A>, ou um <xref:System.Windows.DataTemplate> com um <xref:System.Windows.DataTemplate.DataType%2A>, podem estar em um <xref:System.Windows.ResourceDictionary> e usar a chave implícita.  
  
-   WPF oferece suporte a um conceito de dicionário de recursos mesclados. As chaves podem ser compartilhadas entre os dicionários mesclados e o comportamento de chave compartilhado pode ser acessado usando <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Para obter mais informações, consulte [Dicionários de recursos mesclados](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 No WPF XAML implementação e aplicativo modelo geral, a chave exclusividade não é verificada pelo compilador de marcação XAML. Em vez disso, ausente ou não exclusivo `x:Key` valores causam erros de analisador do tempo de carregamento XAML. No entanto, [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] tratamento de dicionários para WPF muitas vezes pode observar esses erros na fase de design.  
  
 Observe que na sintaxe mostrada, o <xref:System.Windows.ResourceDictionary> objeto está implícito em como o processador de WPF XAML produz uma coleção para preencher uma <xref:System.Windows.FrameworkElement.Resources%2A> coleção. Um <xref:System.Windows.ResourceDictionary> não normalmente é fornecido explicitamente como um elemento na marcação, embora ele possa ser em alguns casos, se quisesse para fins de esclarecimento (seria um elemento de objeto de coleção entre o <xref:System.Windows.FrameworkElement.Resources%2A> popular de elemento de propriedade e os itens que o dicionário). Para obter informações sobre por que um objeto de coleção quase sempre é um elemento implícito na marcação, consulte [XAML sintaxe em detalhes](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Na implementação do WPF XAML, a manipulação de chaves do dicionário de recurso é definida pelo <xref:System.Windows.ResourceKey> classe abstrata. No entanto, o processador de WPF XAML produz diferentes tipos de extensão subjacentes para chaves com base em seus usos. Por exemplo, a chave para um <xref:System.Windows.DataTemplate> ou qualquer classe derivada é tratada separadamente e produz um distintos <xref:System.Windows.DataTemplateKey> objeto.  
  
 Chaves e nomes de usam diretivas diferentes e elementos de linguagem (`x:Key` versus `x:Name`) na definição de XAML básico. Chaves e nomes também são usados em situações diferentes pela definição do WPF e aplicativo desses conceitos. Para obter detalhes, consulte [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Como mencionado anteriormente, o valor de uma chave pode ser fornecido por meio de uma extensão de marcação e pode ser diferente de um valor de cadeia de caracteres. Um exemplo de cenário WPF que é o valor de `x:Key` pode ser um[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md). Certos controles expõem uma chave de estilo de tipo para um recurso de estilo personalizado que influencia a parte da aparência e comportamento do controle sem substituir totalmente o estilo. Um exemplo de tal chave é <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 O recurso de dicionário mesclado WPF apresenta considerações adicionais para exclusividade de chave e o comportamento de pesquisa de chave. Para obter mais informações, consulte [Dicionários de recursos mesclados](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 alivia a restrição que `x:Key` sempre ser fornecidos na forma de atributo.  
  
 No WPF, você pode usar recursos de XAML 2009, mas somente para XAML não marcação-compilado. Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009.  
  
 Em XAML 2009, você pode especificar `x:Key` elementos através do uso do seguinte:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Uso do elemento XAML (somente no XAML 2009)  
  
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
  
-   O contêiner/pai para esse tipo de uso não é mostrado aqui. `object`deve ser um filho de um elemento de objeto que representa uma implementação de dicionário especializado. `keyObject`deve ser uma instância do objeto (ou um valor de um tipo de valor) que é apropriado como a chave para que a implementação específica dicionário especializado.  
  
-   WPF não implementa dicionários que exigem esse uso. Chaves de objeto é mais um recurso geral da linguagem XAML, possivelmente útil para determinados cenários de dicionário personalizado que é desejável criar o dicionário em XAML. Para recursos do WPF como estilos implícitos que usam chaves de cadeia de caracteres não para recursos, outras técnicas para estabelecer ou especificando as chaves existem, portanto não é necessário usar uma chave de objeto.  
  
-   *keyObject* também pode ser um uso de extensão de marcação no formulário de elemento de objeto, em vez de uma instância de objeto direto.  
  
## <a name="silverlight-usage-notes"></a>Observações de uso do Silverlight  
 `x:Key`para o Silverlight é documentado separadamente. Para obter mais informações, consulte [Namespace XAML (x) Recursos de linguagem (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também  
 [Recursos XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Recursos e código](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Extensão de marcação StaticResource](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
