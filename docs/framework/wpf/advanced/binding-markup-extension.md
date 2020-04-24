---
title: Extensão de marcação de associação
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: c6a424e085c7499db08d0a7e6b652f45fb2cdd70
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644079"
---
# <a name="binding-markup-extension"></a>Extensão de marcação de associação
Adia um valor da propriedade para ser um valor de associação de dados, criando um objeto de expressão intermediário e interpretando o contexto de dados que se aplica ao elemento e à sua associação em tempo de execução.  
  
## <a name="binding-expression-usage"></a>Uso de expressões de associação  
  
```xaml  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>Observações sobre a sintaxe  
 Nessas sintaxes, o `[]` e `*` não são literais. Eles fazem parte de uma notação para indicar que pares de*valores* *de bindProp*`=`zero ou mais podem ser usados, com um `,` separador entre eles e os pares de*valores* *bindProp*`=`anteriores.  
  
 Qualquer uma das propriedades listadas na seção "Propriedades de vinculação que podem ser <xref:System.Windows.Data.Binding> definidas com a extensão de vinculação" poderia ser definida usando atributos de um elemento de objeto. No entanto, esse não é <xref:System.Windows.Data.Binding>realmente o uso de extensão de marcação, é apenas <xref:System.Windows.Data.Binding> o processamento geral XAML de atributos que definem propriedades da classe CLR. Em outras `<Binding` palavras, *bindProp1*`="`*value1* `"[` *bindPropN*`="`*valueN* `"]*/>` é <xref:System.Windows.Data.Binding> uma sintaxe `Binding` equivalente para atributos de uso do elemento objeto em vez de um uso de expressão. Para saber mais sobre o uso do <xref:System.Windows.Data.Binding>atributo XAML de propriedades específicas de <xref:System.Windows.Data.Binding> , consulte a seção "Uso de atributo XAML" da propriedade relevante da Biblioteca de Classe Framework .NET.  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|O nome <xref:System.Windows.Data.Binding> da <xref:System.Windows.Data.BindingBase> propriedade ou a definir. Nem <xref:System.Windows.Data.Binding> todas as propriedades `Binding` podem ser definidas com a `Binding` extensão, e algumas propriedades são configuradas dentro de uma expressão apenas usando extensões de marcação aninhadas adicionais. Consulte a seção "Associando propriedades que podem ser definidas com a extensão de associação".|  
|`value1, valueN`|O valor para o qual definir a propriedade. O manuseio do valor do atributo é, em última <xref:System.Windows.Data.Binding> análise, específico para o tipo e a lógica da propriedade específica que está sendo definida.|  
|`path`|A seqüência de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> caminho que define a propriedade implícita. Consulte também [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>{Binding} não qualificada  
 O `{Binding}` uso mostrado em "Uso <xref:System.Windows.Data.Binding> de expressão de vinculação" <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> cria `null`um objeto com valores padrão, que inclui uma inicial de . Isso ainda é útil em muitos <xref:System.Windows.Data.Binding> cenários, porque o criado pode <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> estar confiando em propriedades de vinculação de dados importantes, como e sendo definido satisfaz o contexto de dados em tempo de execução. Para obter mais informações sobre o conceito de contexto de dados, consulte [Vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
## <a name="implicit-path"></a>Caminho implícito  
 A `Binding` extensão <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> de marcação usa como `Path=` uma "propriedade padrão" conceitual, onde não precisa aparecer na expressão. Se você `Binding` especificar uma expressão com um caminho implícito, o caminho `bindProp` = `value` implícito <xref:System.Windows.Data.Binding> deve aparecer primeiro na expressão, antes de quaisquer outros pares onde a propriedade é especificada pelo nome. Por `{Binding PathString}`exemplo: `PathString` , onde está uma string que <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> é <xref:System.Windows.Data.Binding> avaliada como sendo o valor do criado pelo uso da extensão de marcação. Você pode acrescentar um caminho implícito com outras propriedades nomeadas após o separador de vírgula, por exemplo, `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Associando propriedades que podem ser definidas com a extensão de associação  
 A sintaxe mostrada neste `bindProp` = `value` tópico usa a aproximação genérica, pois <xref:System.Windows.Data.BindingBase> existem muitas propriedades de leitura/gravação ou <xref:System.Windows.Data.Binding> que podem ser definidas através da extensão de `Binding` marcação/sintaxe de expressão. Eles podem ser definidos em qualquer ordem, com exceção de um implícito. <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> (Você tem a opção de especificar explicitamente `Path=` e nesse caso, ela poderá ser definida em qualquer ordem). Basicamente, você pode definir zero ou mais das propriedades na lista abaixo, usando pares `bindProp`=`value` separados por vírgulas.  
  
 Vários desses valores de propriedade exigem tipos de objeto que não dão suporte a uma conversão de tipo nativo de uma sintaxe de texto em XAML e, portanto, requerem extensões de marcação para serem definidos como um valor de atributo. Consulte a seção Uso do atributo XAML na biblioteca de classes .NET Framework para cada propriedade para obter mais informações. A cadeia de caracteres que você usa para a sintaxe de atributo XAML, com ou sem o uso adicional de extensão de marcação, é basicamente a mesma que o valor que você especifica em uma expressão `Binding`, com a exceção de que você não coloca aspas ao redor de cada `bindProp`=`value` na expressão `Binding`.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: uma seqüência que identifica um possível grupo de ligação. Este é um conceito de ligação relativamente avançado; ver página <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>de referência para .  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, pode `true` `false`ser ou . O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: pode ser `bindProp` = `value` definido como uma string na expressão, mas para isso requer uma referência de objeto para o valor, como uma [extensão de marcação staticResource](staticresource-markup-extension.md). Nesse caso, o valor é uma instância de uma classe de conversor personalizado.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: definido na expressão como identificador baseado em padrões; ver o tópico <xref:System.Windows.Data.Binding.ConverterCulture%2A>de referência para .  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: pode ser `bindProp` = `value` definido como uma string na expressão, mas isso depende do tipo de parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, esse uso exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: mutuamente <xref:System.Windows.Data.Binding.RelativeSource%2A> exclusivo <xref:System.Windows.Data.Binding.Source%2A>versus e; cada uma dessas propriedades vinculantes representa uma metodologia de vinculação específica. Consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: pode ser `bindProp` = `value` definido como uma string na expressão, mas isso depende do tipo de valor que está sendo passado. Se estiver passando um tipo de referência, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, pode `true` `false`ser ou . O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *valor* é um <xref:System.Windows.Data.BindingMode> nome constante da enumeração. Por exemplo, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, pode `true` `false`ser ou . O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, pode `true` `false`ser ou . O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, pode `true` `false`ser ou . O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: uma string que descreve um caminho em um objeto de dados ou um modelo de objeto geral. O formato fornece várias convenções diferentes para percorrer um modelo de objeto que não pode ser descrito adequadamente neste tópico. Consulte [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: mutuamente exclusivo <xref:System.Windows.Data.Binding.ElementName%2A> <xref:System.Windows.Data.Binding.Source%2A>versus com e; cada uma dessas propriedades vinculantes representa uma metodologia de vinculação específica. Consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md). Exige o uso de uma [MarkupExtension RelativeSource](relativesource-markupextension.md) aninhada para especificar o valor.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: mutuamente <xref:System.Windows.Data.Binding.RelativeSource%2A> exclusivo <xref:System.Windows.Data.Binding.ElementName%2A>versus e; cada uma dessas propriedades vinculantes representa uma metodologia de vinculação específica. Consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md). Exige o uso de uma extensão aninhada, normalmente uma [extensão de marcação StaticResource](staticresource-markup-extension.md), que faz referência a um objeto de fonte de dados de um dicionário de recursos com chave.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: uma string que descreve uma convenção de formato de string para os dados vinculados. Este é um conceito de ligação relativamente avançado; ver página <xref:System.Windows.Data.BindingBase.StringFormat%2A>de referência para .  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: pode ser `bindProp` = `value` definido como uma string na expressão, mas isso depende do tipo de parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *valor* é um <xref:System.Windows.Data.UpdateSourceTrigger> nome constante da enumeração. Por exemplo, `{Binding UpdateSourceTrigger=LostFocus}`. Controles específicos têm, potencialmente, valores padrão diferentes para essa propriedade de associação. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, pode `true` `false`ser ou . O padrão é `false`. Consulte Observações.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, pode `true` `false`ser ou . O padrão é `false`. Consulte Observações.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: uma seqüência que descreve um caminho para o XMLDOM de uma fonte de dados XML. Consulte [Associar a dados XML usando um XMLDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 As seguintes <xref:System.Windows.Data.Binding> propriedades não podem `Binding` ser definidas`{Binding}` usando a forma de extensão/expressão de marcação.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: esta propriedade espera uma referência a uma implementação de retorno de chamada. Retornos de chamada/métodos diferentes de manipuladores de eventos não podem ser referenciados em sintaxe XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: a propriedade leva <xref:System.Windows.Controls.ValidationRule> uma coleção genérica de objetos. Isso pode ser expresso como <xref:System.Windows.Data.Binding> um elemento de propriedade em um elemento objeto, mas `Binding` não tem técnica prontamente disponível de análise de atributos para uso em uma expressão. Consulte o <xref:System.Windows.Data.Binding.ValidationRules%2A>tópico de referência para .  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
> Em termos de precedência de propriedade de dependência, uma expressão `Binding` é equivalente a um valor definido localmente. Se um valor local for definido para uma propriedade que tinha uma expressão `Binding` anteriormente, a `Binding` será totalmente removida. Para obter mais detalhes, consulte [Precedência do valor da propriedade da dependência](dependency-property-value-precedence.md).  
  
 Não é abordada a descrição da vinculação de dados em um nível básico neste tópico. Consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>e <xref:System.Windows.Data.PriorityBinding> não suportam uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe de extensão. Em vez disso, você deveria usar elementos de propriedade. Consulte tópicos <xref:System.Windows.Data.MultiBinding> <xref:System.Windows.Data.PriorityBinding>de referência para e .  
  
 Os valores boolianos para XAML não diferenciam maiúsculas de minúsculas. Por exemplo você pode especificar um `{Binding NotifyOnValidationError=true}` ou `{Binding NotifyOnValidationError=True}`.  
  
 As vinculações que envolvem validação de dados `Binding` são tipicamente `{Binding ...}` especificadas <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> por <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> um elemento explícito e não como uma expressão, e a configuração ou em uma expressão é incomum. Isso porque a <xref:System.Windows.Data.Binding.ValidationRules%2A> propriedade do companheiro não pode ser prontamente definida na forma de expressão. Para obter mais informações, consulte [Implementar validação de associação](../data/how-to-implement-binding-validation.md).  
  
 `Binding` é uma extensão da marcação. As extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores e o requisito é mais global do que conversores de tipo atribuídos em certos tipos ou propriedades. Todas as extensões de marcação no XAML usam os caracteres `{` e `}` na sintaxe de atributo, que é a convenção pela qual o processador XAML reconhece que uma extensão de marcação precisa processar o conteúdo da cadeia de caracteres. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`é uma extensão de marcação atípica na medida em que a <xref:System.Windows.Data.Binding> classe que implementa a funcionalidade de extensão para a implementação XAML do WPF também implementa vários outros métodos e propriedades que não estão relacionados ao XAML. Os outros membros têm <xref:System.Windows.Data.Binding> a intenção de fazer uma classe mais versátil e independente que pode abordar muitos cenários de vinculação de dados, além de funcionar como uma extensão de marcação XAML.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Data.Binding>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md)
