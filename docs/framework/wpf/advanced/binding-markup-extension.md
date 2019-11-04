---
title: Extensão de marcação de associação
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: d0a437e756da16db978d8074c4355fd83d211b67
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453604"
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
 Nessas sintaxes, o `[]` e `*` não são literais. Eles fazem parte de uma notação para indicar que zero ou mais pares *bindProp*`=`*value* podem ser usados, com um separador `,` entre eles, precedendo pares *bindProp*`=`*value*.  
  
 Qualquer uma das propriedades listadas na seção "Propriedades de associação que podem ser definidas com a extensão de associação" poderia ser definida usando atributos de um elemento de objeto <xref:System.Windows.Data.Binding>. No entanto, isso não é verdadeiramente o uso da extensão de marcação de <xref:System.Windows.Data.Binding>, é apenas o processamento geral XAML dos atributos que definem as propriedades da classe CLR <xref:System.Windows.Data.Binding>. Em outras palavras, `<Binding` *bindProp1*`="`*value1*`"[` *bindPropN*`="`*valor*`"]*/>` é uma sintaxe equivalente para atributos de <xref:System.Windows.Data.Binding> uso de elemento de objeto em vez de um uso de expressão de `Binding`. Para saber mais sobre o uso do atributo XAML de propriedades específicas do <xref:System.Windows.Data.Binding>, consulte a seção "uso do atributo XAML" da propriedade relevante de <xref:System.Windows.Data.Binding> na biblioteca de classes do .NET Framework.  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|O nome da propriedade <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.BindingBase> a ser definida. Nem todas as propriedades de <xref:System.Windows.Data.Binding> podem ser definidas com a extensão `Binding` e algumas propriedades são configuráveis dentro de uma expressão `Binding` apenas usando extensões de marcação aninhadas adicionais. Consulte a seção "Associando propriedades que podem ser definidas com a extensão de associação".|  
|`value1, valueN`|O valor para o qual definir a propriedade. A manipulação do valor do atributo é, por fim, específica ao tipo e à lógica da propriedade <xref:System.Windows.Data.Binding> específica que está sendo definida.|  
|`path`|A cadeia de caracteres de caminho que define a propriedade de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> implícita. Consulte também [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>{Binding} não qualificada  
 O uso de `{Binding}` mostrado em "uso da expressão de associação" cria um objeto <xref:System.Windows.Data.Binding> com valores padrão, que inclui uma <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> inicial de `null`. Isso ainda é útil em muitos cenários, porque o <xref:System.Windows.Data.Binding> criado pode estar contando com as propriedades de associação de dados de chave, como <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> e <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> sendo definidas no contexto de dados em tempo de execução. Para obter mais informações sobre o conceito de contexto de dados, consulte [Vinculação de dados](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Caminho implícito  
 A extensão de marcação de `Binding` usa <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> como uma "propriedade padrão" conceitual, em que `Path=` não precisa aparecer na expressão. Se você especificar uma expressão de `Binding` com um caminho implícito, o caminho implícito deverá aparecer primeiro na expressão, antes de qualquer outra `bindProp`=pares de `value` em que a propriedade <xref:System.Windows.Data.Binding> for especificada por nome. Por exemplo: `{Binding PathString}`, em que `PathString` é uma cadeia de caracteres que é avaliada como o valor de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> no <xref:System.Windows.Data.Binding> criado pelo uso da extensão de marcação. Você pode acrescentar um caminho implícito com outras propriedades nomeadas após o separador de vírgula, por exemplo, `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Associando propriedades que podem ser definidas com a extensão de associação  
 A sintaxe mostrada neste tópico usa o `bindProp`genérico =aproximação de `value`, pois há muitas propriedades de leitura/gravação de <xref:System.Windows.Data.BindingBase> ou <xref:System.Windows.Data.Binding> que podem ser definidas por meio da sintaxe de expressão/extensão de marcação `Binding`. Eles podem ser definidos em qualquer ordem, com exceção de um <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>implícito. (Você tem a opção de especificar explicitamente `Path=` e nesse caso, ela poderá ser definida em qualquer ordem). Basicamente, você pode definir zero ou mais das propriedades na lista abaixo, usando pares `bindProp`=`value` separados por vírgulas.  
  
 Vários desses valores de propriedade exigem tipos de objeto que não dão suporte a uma conversão de tipo nativo de uma sintaxe de texto em XAML e, portanto, requerem extensões de marcação para serem definidos como um valor de atributo. Consulte a seção Uso do atributo XAML na biblioteca de classes .NET Framework para cada propriedade para obter mais informações. A cadeia de caracteres que você usa para a sintaxe de atributo XAML, com ou sem o uso adicional de extensão de marcação, é basicamente a mesma que o valor que você especifica em uma expressão `Binding`, com a exceção de que você não coloca aspas ao redor de cada `bindProp`=`value` na expressão `Binding`.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: uma cadeia de caracteres que identifica um possível grupo de associação. Esse é um conceito de Associação relativamente avançado; consulte a página de referência para <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: pode ser definido como um `bindProp`=cadeia de caracteres `value` na expressão, mas isso requer uma referência de objeto para o valor, como uma [extensão de marcação StaticResource](staticresource-markup-extension.md). Nesse caso, o valor é uma instância de uma classe de conversor personalizado.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: configurável na expressão como um identificador baseado em padrões; consulte o tópico de referência para <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: pode ser definido como um `bindProp`=cadeia de caracteres `value` na expressão, mas isso depende do tipo do parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, esse uso exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: mutuamente exclusivo versus <xref:System.Windows.Data.Binding.RelativeSource%2A> e <xref:System.Windows.Data.Binding.Source%2A>; cada uma dessas propriedades de associação representa uma metodologia de ligação específica. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: pode ser definido como um `bindProp`=cadeia de caracteres `value` na expressão, mas isso depende do tipo do valor que está sendo passado. Se estiver passando um tipo de referência, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *Value* é um nome constante da enumeração <xref:System.Windows.Data.BindingMode>. Por exemplo, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: uma cadeia de caracteres que descreve um caminho em um objeto de dados ou um modelo de objeto geral. O formato fornece várias convenções diferentes para percorrer um modelo de objeto que não pode ser descrito adequadamente neste tópico. Consulte [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: mutuamente exclusivo versus com <xref:System.Windows.Data.Binding.ElementName%2A> e <xref:System.Windows.Data.Binding.Source%2A>; cada uma dessas propriedades de associação representa uma metodologia de ligação específica. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md). Exige o uso de uma [MarkupExtension RelativeSource](relativesource-markupextension.md) aninhada para especificar o valor.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: mutuamente exclusivo versus <xref:System.Windows.Data.Binding.RelativeSource%2A> e <xref:System.Windows.Data.Binding.ElementName%2A>; cada uma dessas propriedades de associação representa uma metodologia de ligação específica. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md). Exige o uso de uma extensão aninhada, normalmente uma [extensão de marcação StaticResource](staticresource-markup-extension.md), que faz referência a um objeto de fonte de dados de um dicionário de recursos com chave.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: uma cadeia de caracteres que descreve uma Convenção de formato de cadeia de caracteres para os dados associados. Esse é um conceito de Associação relativamente avançado; consulte a página de referência para <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: pode ser definido como um `bindProp`=cadeia de caracteres `value` na expressão, mas isso depende do tipo do parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *Value* é um nome constante da enumeração <xref:System.Windows.Data.UpdateSourceTrigger>. Por exemplo, `{Binding UpdateSourceTrigger=LostFocus}`. Controles específicos têm, potencialmente, valores padrão diferentes para essa propriedade de associação. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`. Consulte Observações.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`. Consulte Observações.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: uma cadeia de caracteres que descreve um caminho para o XMLDOM de uma fonte de dados XML. Consulte [Associar a dados XML usando um XMLDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Veja a seguir as propriedades de <xref:System.Windows.Data.Binding> que não podem ser definidas usando o formulário expressão de`{Binding}`/extensão de marcação de `Binding`.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: essa propriedade espera uma referência a uma implementação de retorno de chamada. Retornos de chamada/métodos diferentes de manipuladores de eventos não podem ser referenciados em sintaxe XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: a propriedade usa uma coleção genérica de objetos <xref:System.Windows.Controls.ValidationRule>. Isso pode ser expresso como um elemento de propriedade em um elemento de objeto <xref:System.Windows.Data.Binding>, mas não tem uma técnica de análise de atributo prontamente disponível para uso em uma expressão `Binding`. Consulte o tópico de referência para <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
> Em termos de precedência de propriedade de dependência, uma expressão `Binding` é equivalente a um valor definido localmente. Se um valor local for definido para uma propriedade que tinha uma expressão `Binding` anteriormente, a `Binding` será totalmente removida. Para obter mais detalhes, consulte [Precedência do valor da propriedade da dependência](dependency-property-value-precedence.md).  
  
 Não é abordada a descrição da vinculação de dados em um nível básico neste tópico. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding> e <xref:System.Windows.Data.PriorityBinding> não dão suporte a uma sintaxe de extensão [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Em vez disso, você deveria usar elementos de propriedade. Consulte os tópicos de referência para <xref:System.Windows.Data.MultiBinding> e <xref:System.Windows.Data.PriorityBinding>.  
  
 Os valores boolianos para XAML não diferenciam maiúsculas de minúsculas. Por exemplo você pode especificar um `{Binding NotifyOnValidationError=true}` ou `{Binding NotifyOnValidationError=True}`.  
  
 Associações que envolvem validação de dados geralmente são especificadas por um elemento `Binding` explícito em vez de como uma expressão `{Binding ...}`, e a configuração <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ou <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> em uma expressão não é comum. Isso ocorre porque a propriedade Companion <xref:System.Windows.Data.Binding.ValidationRules%2A> não pode ser prontamente definida no formulário de expressão. Para obter mais informações, consulte [Implementar validação de associação](../data/how-to-implement-binding-validation.md).  
  
 `Binding` é uma extensão da marcação. As extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores e o requisito é mais global do que conversores de tipo atribuídos em certos tipos ou propriedades. Todas as extensões de marcação no XAML usam os caracteres `{` e `}` na sintaxe de atributo, que é a convenção pela qual o processador XAML reconhece que uma extensão de marcação precisa processar o conteúdo da cadeia de caracteres. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding` é uma extensão de marcação atípicos no que a classe <xref:System.Windows.Data.Binding> que implementa a funcionalidade de extensão para a implementação XAML do WPF também implementa vários outros métodos e propriedades que não estão relacionados ao XAML. Os outros membros destinam-se a fazer <xref:System.Windows.Data.Binding> uma classe mais versátil e independente que pode resolver muitos cenários de ligação de dados, além de funcionar como uma extensão de marcação XAML.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.Binding>
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md)
