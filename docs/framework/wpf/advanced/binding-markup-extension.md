---
title: Extensão de marcação de associação
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 616e405e191cb264a002e903bed60cf04559a675
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964896"
---
# <a name="binding-markup-extension"></a>Extensão de marcação de associação
Adia um valor da propriedade para ser um valor de associação de dados, criando um objeto de expressão intermediário e interpretando o contexto de dados que se aplica ao elemento e à sua associação em tempo de execução.  
  
## <a name="binding-expression-usage"></a>Uso de expressões de associação  
  
```  
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
  
 Qualquer uma das propriedades listadas na seção "Propriedades de associação que podem ser definidas com a extensão de associação" poderia ser definida usando atributos de <xref:System.Windows.Data.Binding> um elemento Object. No entanto, isso não é verdadeiramente o uso da <xref:System.Windows.Data.Binding>extensão de marcação de, é apenas o processamento geral XAML dos atributos que definem <xref:System.Windows.Data.Binding> as propriedades da classe CLR. Em outras palavras, `<Binding` *bindProp1*`="`*value1* `"[` <xref:System.Windows.Data.Binding> *bindPropN* valuenéumasintaxeequivalenteparaatributosdeusodeelementode`"]*/>`objeto `="` em vez de `Binding` um uso de expressão. Para saber mais sobre o uso do atributo XAML de propriedades <xref:System.Windows.Data.Binding>específicas do, consulte a seção "uso do atributo XAML" da propriedade <xref:System.Windows.Data.Binding> relevante do na biblioteca de classes do .NET Framework.  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|O nome da <xref:System.Windows.Data.Binding> propriedade ou <xref:System.Windows.Data.BindingBase> a ser definida. Nem todas <xref:System.Windows.Data.Binding> as propriedades podem ser definidas com `Binding` a extensão e algumas propriedades são configuráveis dentro de `Binding` uma expressão somente usando extensões de marcação aninhadas adicionais. Consulte a seção "Associando propriedades que podem ser definidas com a extensão de associação".|  
|`value1, valueN`|O valor para o qual definir a propriedade. A manipulação do valor do atributo é, por fim, específica ao tipo e à lógica <xref:System.Windows.Data.Binding> da propriedade específica que está sendo definida.|  
|`path`|A cadeia de caracteres de caminho que <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> define a propriedade implícita. Consulte também [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>{Binding} não qualificada  
 O `{Binding}` uso mostrado em "uso da expressão de associação" <xref:System.Windows.Data.Binding> cria um objeto com valores padrão, que inclui <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> uma `null`inicial de. Isso ainda é útil em muitos cenários, porque o criado <xref:System.Windows.Data.Binding> pode estar de acordo com as propriedades de associação de dados <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> chave <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> , como e que está sendo definido no contexto de dados em tempo de execução. Para obter mais informações sobre o conceito de contexto de dados, consulte [Vinculação de dados](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Caminho implícito  
 A `Binding` extensão de marcação <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> usa como uma "propriedade padrão" conceitual `Path=` , onde não precisa aparecer na expressão. Se você especificar uma `Binding` expressão com um caminho implícito, o caminho implícito deverá aparecer primeiro na expressão, antes de quaisquer outros `value` `bindProp` = pares em que a <xref:System.Windows.Data.Binding> propriedade for especificada por nome. Por exemplo: `{Binding PathString}`, em `PathString` que é uma cadeia de caracteres que é avaliada como <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> <xref:System.Windows.Data.Binding> o valor de no criado pelo uso da extensão de marcação. Você pode acrescentar um caminho implícito com outras propriedades nomeadas após o separador de vírgula, por exemplo, `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Associando propriedades que podem ser definidas com a extensão de associação  
 A sintaxe mostrada neste tópico usa a aproximação `bindProp` genérica <xref:System.Windows.Data.Binding> = `value` , pois há muitas propriedades de leitura/gravação de <xref:System.Windows.Data.BindingBase> ou que podem ser definidas por meio `Binding` da extensão de marcação/ sintaxe de expressão. Eles podem ser definidos em qualquer ordem, com exceção de um implícito <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Você tem a opção de especificar explicitamente `Path=` e nesse caso, ela poderá ser definida em qualquer ordem). Basicamente, você pode definir zero ou mais das propriedades na lista abaixo, usando pares `bindProp`=`value` separados por vírgulas.  
  
 Vários desses valores de propriedade exigem tipos de objeto que não dão suporte a uma conversão de tipo nativo de uma sintaxe de texto em XAML e, portanto, requerem extensões de marcação para serem definidos como um valor de atributo. Consulte a seção Uso do atributo XAML na biblioteca de classes .NET Framework para cada propriedade para obter mais informações. A cadeia de caracteres que você usa para a sintaxe de atributo XAML, com ou sem o uso adicional de extensão de marcação, é basicamente a mesma que o valor que você especifica em uma expressão `Binding`, com a exceção de que você não coloca aspas ao redor de cada `bindProp`=`value` na expressão `Binding`.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: uma cadeia de caracteres que identifica um possível grupo de associação. Esse é um conceito de Associação relativamente avançado; consulte a página de <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>referência para.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Booliano, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: pode ser definido como uma `bindProp` = `value` cadeia de caracteres na expressão, mas isso requer uma referência de objeto para o valor, como uma [extensão de marcação StaticResource](staticresource-markup-extension.md). Nesse caso, o valor é uma instância de uma classe de conversor personalizado.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: configurável na expressão como um identificador baseado em padrões; consulte o tópico de referência <xref:System.Windows.Data.Binding.ConverterCulture%2A>para.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: pode ser definido como uma `bindProp` = `value` cadeia de caracteres na expressão, mas isso depende do tipo do parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, esse uso exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: mutuamente exclusivo versus <xref:System.Windows.Data.Binding.RelativeSource%2A> e <xref:System.Windows.Data.Binding.Source%2A>; cada uma dessas propriedades de associação representa uma metodologia de ligação específica. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: pode ser definido como uma `bindProp` = `value` cadeia de caracteres na expressão, mas isso depende do tipo do valor que está sendo passado. Se estiver passando um tipo de referência, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Booliano, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *Value* é um nome constante da <xref:System.Windows.Data.BindingMode> enumeração. Por exemplo, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Booliano, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Booliano, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Booliano, pode ser `true` ou `false`. O padrão é `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: uma cadeia de caracteres que descreve um caminho em um objeto de dados ou um modelo de objeto geral. O formato fornece várias convenções diferentes para percorrer um modelo de objeto que não pode ser descrito adequadamente neste tópico. Consulte [Sintaxe XAML de PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: mutuamente exclusivo versus com <xref:System.Windows.Data.Binding.ElementName%2A> and <xref:System.Windows.Data.Binding.Source%2A>; cada uma dessas propriedades de associação representa uma metodologia de ligação específica. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md). Exige o uso de uma [MarkupExtension RelativeSource](relativesource-markupextension.md) aninhada para especificar o valor.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: mutuamente exclusivo versus <xref:System.Windows.Data.Binding.RelativeSource%2A> e <xref:System.Windows.Data.Binding.ElementName%2A>; cada uma dessas propriedades de associação representa uma metodologia de ligação específica. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md). Exige o uso de uma extensão aninhada, normalmente uma [extensão de marcação StaticResource](staticresource-markup-extension.md), que faz referência a um objeto de fonte de dados de um dicionário de recursos com chave.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: uma cadeia de caracteres que descreve uma Convenção de formato de cadeia de caracteres para os dados associados. Esse é um conceito de Associação relativamente avançado; consulte a página de <xref:System.Windows.Data.BindingBase.StringFormat%2A>referência para.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: pode ser definido como uma `bindProp` = `value` cadeia de caracteres na expressão, mas isso depende do tipo do parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](staticresource-markup-extension.md) aninhada.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *Value* é um nome constante da <xref:System.Windows.Data.UpdateSourceTrigger> enumeração. Por exemplo, `{Binding UpdateSourceTrigger=LostFocus}`. Controles específicos têm, potencialmente, valores padrão diferentes para essa propriedade de associação. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Booliano, pode ser `true` ou `false`. O padrão é `false`. Consulte Observações.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Booliano, pode ser `true` ou `false`. O padrão é `false`. Consulte Observações.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: uma cadeia de caracteres que descreve um caminho para o XMLDOM de uma fonte de dados XML. Consulte [Associar a dados XML usando um XMLDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Veja a seguir as propriedades <xref:System.Windows.Data.Binding> de que não podem ser definidas `Binding` usando a extensão`{Binding}` de marcação/formulário de expressão.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: essa propriedade espera uma referência a uma implementação de retorno de chamada. Retornos de chamada/métodos diferentes de manipuladores de eventos não podem ser referenciados em sintaxe XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: a propriedade usa uma coleção genérica de <xref:System.Windows.Controls.ValidationRule> objetos. Isso pode ser expresso como um elemento de propriedade em <xref:System.Windows.Data.Binding> um elemento Object, mas não tem uma técnica de análise de atributo prontamente disponível para `Binding` uso em uma expressão. Consulte o tópico de <xref:System.Windows.Data.Binding.ValidationRules%2A>referência para.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
> Em termos de precedência de propriedade de dependência, uma expressão `Binding` é equivalente a um valor definido localmente. Se um valor local for definido para uma propriedade que tinha uma expressão `Binding` anteriormente, a `Binding` será totalmente removida. Para obter mais detalhes, consulte [Precedência do valor da propriedade de dependência](dependency-property-value-precedence.md).  
  
 Não é abordada a descrição da vinculação de dados em um nível básico neste tópico. Consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>e <xref:System.Windows.Data.PriorityBinding> não oferecem suporte a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uma sintaxe de extensão. Em vez disso, você deveria usar elementos de propriedade. Consulte os tópicos de <xref:System.Windows.Data.MultiBinding> referência <xref:System.Windows.Data.PriorityBinding>para e.  
  
 Os valores boolianos para XAML não diferenciam maiúsculas de minúsculas. Por exemplo você pode especificar um `{Binding NotifyOnValidationError=true}` ou `{Binding NotifyOnValidationError=True}`.  
  
 Associações que envolvem validação de dados normalmente são especificadas por um `Binding` elemento explícito em vez de `{Binding ...}` como uma expressão, <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> e <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> a configuração ou em uma expressão não é comum. Isso ocorre porque a propriedade <xref:System.Windows.Data.Binding.ValidationRules%2A> Companion não pode ser prontamente definida no formulário de expressão. Para obter mais informações, consulte [Implementar validação de associação](../data/how-to-implement-binding-validation.md).  
  
 `Binding` é uma extensão da marcação. As extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores e o requisito é mais global do que conversores de tipo atribuídos em certos tipos ou propriedades. Todas as extensões de marcação no XAML usam os caracteres `{` e `}` na sintaxe de atributo, que é a convenção pela qual o processador XAML reconhece que uma extensão de marcação precisa processar o conteúdo da cadeia de caracteres. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`é uma extensão de marcação atípicos no que <xref:System.Windows.Data.Binding> a classe que implementa a funcionalidade de extensão para a implementação XAML do WPF também implementa vários outros métodos e propriedades que não estão relacionados ao XAML. Os outros membros destinam- <xref:System.Windows.Data.Binding> se a tornar uma classe mais versátil e autônoma que pode tratar de vários cenários de ligação de dados, além de funcionar como uma extensão de marcação XAML.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.Binding>
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Visão geral de XAML (WPF)](xaml-overview-wpf.md)
- [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md)
