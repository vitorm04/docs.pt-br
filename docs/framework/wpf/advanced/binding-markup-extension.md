---
title: "Extensão de marcação de associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d2bbca799e1eda1abae3d199dd71e004b17c4c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
  
 Qualquer uma das propriedades listadas na seção "Associação de propriedades que pode ser definida com a extensão de associação" em vez disso, pode ser definida usando os atributos de um <xref:System.Windows.Data.Binding> elemento do objeto. No entanto, que não é realmente o uso da extensão de marcação de <xref:System.Windows.Data.Binding>, ele é apenas o processamento de XAML de geral de atributos que definem propriedades do CLR <xref:System.Windows.Data.Binding> classe. Em outras palavras, `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*valueN* `"]*/>` é uma sintaxe equivalente para atributos de <xref:System.Windows.Data.Binding> objeto utilização do elemento, em vez de um `Binding` uso de expressão. Para saber mais sobre o uso do atributo XAML de propriedades específicas de <xref:System.Windows.Data.Binding>, consulte a seção "Uso do atributo XAML" da propriedade relevante do <xref:System.Windows.Data.Binding> na biblioteca de classes .NET Framework.  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|O nome do <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.BindingBase> propriedade definida. Nem todos os <xref:System.Windows.Data.Binding> propriedades podem ser definidas com o `Binding` extensão e algumas propriedades são configuráveis dentro de um `Binding` expressão somente com o uso mais aninhado extensões de marcação. Consulte a seção "Associando propriedades que podem ser definidas com a extensão de associação".|  
|`value1, valueN`|O valor para o qual definir a propriedade. O tratamento do valor do atributo é basicamente específico para o tipo e a lógica de específico <xref:System.Windows.Data.Binding> propriedade sendo definida.|  
|`path`|A cadeia de caracteres de caminho que define o implícita <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> propriedade. Consulte também [Sintaxe XAML de PropertyPath](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>{Binding} não qualificada  
 O `{Binding}` uso mostrado em "Uso de expressão de associação" cria um <xref:System.Windows.Data.Binding> do objeto com valores padrão, que inclui um inicial <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> de `null`. Isso é útil em muitos cenários, porque o criado <xref:System.Windows.Data.Binding> pode confiar nas propriedades de associação de dados de chave como <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> e <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> sendo definida no contexto de dados de tempo de execução. Para obter mais informações sobre o conceito de contexto de dados, consulte [Vinculação de dados](../../../../docs/framework/wpf/data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Caminho implícito  
 O `Binding` usos de extensão de marcação <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> como um conceitual "propriedade padrão", onde `Path=` não precisa aparecer na expressão. Se você especificar um `Binding` expressão com um caminho implícita, o caminho implícita deve aparecer primeiro na expressão, antes de qualquer outro `bindProp` = `value` pares onde o <xref:System.Windows.Data.Binding> propriedade é especificada por nome. Por exemplo: `{Binding PathString}`, onde `PathString` é uma cadeia de caracteres que é avaliada como o valor de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> no <xref:System.Windows.Data.Binding> criado pelo uso de extensão de marcação. Você pode acrescentar um caminho implícito com outras propriedades nomeadas após o separador de vírgula, por exemplo, `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Associando propriedades que podem ser definidas com a extensão de associação  
 A sintaxe mostrada neste tópico usa genérica `bindProp` = `value` aproximação, porque há muitas propriedades de leitura/gravação do <xref:System.Windows.Data.BindingBase> ou <xref:System.Windows.Data.Binding> que podem ser definidas por meio de `Binding` extensão de marcação / sintaxe de expressão. Eles podem ser definidos em qualquer ordem, com exceção implícita <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Você tem a opção de especificar explicitamente `Path=` e nesse caso, ela poderá ser definida em qualquer ordem). Basicamente, você pode definir zero ou mais das propriedades na lista abaixo, usando pares `bindProp`=`value` separados por vírgulas.  
  
 Vários desses valores de propriedade exigem tipos de objeto que não dão suporte a uma conversão de tipo nativo de uma sintaxe de texto em XAML e, portanto, requerem extensões de marcação para serem definidos como um valor de atributo. Consulte a seção Uso do atributo XAML na biblioteca de classes .NET Framework para cada propriedade para obter mais informações. A cadeia de caracteres que você usa para a sintaxe de atributo XAML, com ou sem o uso adicional de extensão de marcação, é basicamente a mesma que o valor que você especifica em uma expressão `Binding`, com a exceção de que você não coloca aspas ao redor de cada `bindProp`=`value` na expressão `Binding`.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: uma cadeia de caracteres que identifica um grupo de associação possíveis. Este é um conceito de associação avançada relativamente; Consulte a página de referência para <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: pode ser definida como um `bindProp` = `value` cadeia de caracteres na expressão, mas para isso requer uma referência de objeto para o valor, como um [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Nesse caso, o valor é uma instância de uma classe de conversor personalizado.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: configurável na expressão como um identificador com base em padrões; Consulte o tópico de referência para <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: pode ser definida como um `bindProp` = `value` cadeia de caracteres na expressão, mas isso é dependente do tipo do parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, esse uso exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) aninhada.  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: mutuamente versus <xref:System.Windows.Data.Binding.RelativeSource%2A> e <xref:System.Windows.Data.Binding.Source%2A>; cada dessas propriedades de associação representa uma metodologia de vinculação específico. Consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: pode ser definida como um `bindProp` = `value` cadeia de caracteres na expressão, mas isso é dependente do tipo do valor que está sendo passado. Se estiver passando um tipo de referência, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) aninhada.  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *valor* é um nome de constante do <xref:System.Windows.Data.BindingMode> enumeração. Por exemplo, `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`.  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: uma cadeia de caracteres que descreve um caminho em um objeto de dados ou um modelo de objeto geral. O formato fornece várias convenções diferentes para percorrer um modelo de objeto que não pode ser descrito adequadamente neste tópico. Consulte [Sintaxe XAML de PropertyPath](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: mutuamente versus com <xref:System.Windows.Data.Binding.ElementName%2A> e <xref:System.Windows.Data.Binding.Source%2A>; cada dessas propriedades de associação representa uma metodologia de vinculação específico. Consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md). Exige o uso de uma [MarkupExtension RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) aninhada para especificar o valor.  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: mutuamente versus <xref:System.Windows.Data.Binding.RelativeSource%2A> e <xref:System.Windows.Data.Binding.ElementName%2A>; cada dessas propriedades de associação representa uma metodologia de vinculação específico. Consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md). Exige o uso de uma extensão aninhada, normalmente uma [extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md), que faz referência a um objeto de fonte de dados de um dicionário de recursos com chave.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: uma cadeia de caracteres que descreve uma convenção de formato de cadeia de caracteres para os dados associados. Este é um conceito de associação avançada relativamente; Consulte a página de referência para <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: pode ser definida como um `bindProp` = `value` cadeia de caracteres na expressão, mas isso é dependente do tipo do parâmetro que está sendo passado. Se estiver passando um tipo de referência para o valor, exigirá uma referência de objeto, como uma [Extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) aninhada.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *valor* é um nome de constante do <xref:System.Windows.Data.UpdateSourceTrigger> enumeração. Por exemplo, `{Binding UpdateSourceTrigger=LostFocus}`. Controles específicos têm, potencialmente, valores padrão diferentes para essa propriedade de associação. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`. Consulte Observações.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, pode ser `true` ou `false`. O padrão é `false`. Consulte Observações.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: uma cadeia de caracteres que descreve um caminho em XMLDOM de uma fonte de dados XML. Consulte [Associar a dados XML usando um XMLDataProvider e consultas XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 A seguir é propriedades de <xref:System.Windows.Data.Binding> que não podem ser definidas usando o `Binding` extensão de marcação /`{Binding}` forma de expressão.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: essa propriedade espera uma referência a uma implementação de retorno de chamada. Retornos de chamada/métodos diferentes de manipuladores de eventos não podem ser referenciados em sintaxe XAML.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: a propriedade tem uma coleção genérica de <xref:System.Windows.Controls.ValidationRule> objetos. Isso pode ser expresso como um elemento de propriedade em uma <xref:System.Windows.Data.Binding> elemento do objeto, mas não tem nenhuma técnica de análise de atributo prontamente disponível para uso em um `Binding` expressão. Consulte o tópico de referência para <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
>  Em termos de precedência de propriedade de dependência, uma expressão `Binding` é equivalente a um valor definido localmente. Se um valor local for definido para uma propriedade que tinha uma expressão `Binding` anteriormente, a `Binding` será totalmente removida. Para obter mais detalhes, consulte [Precedência do valor da propriedade de dependência](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Não é abordada a descrição da vinculação de dados em um nível básico neste tópico. Consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding>e <xref:System.Windows.Data.PriorityBinding> não oferecem suporte a um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe de extensão. Em vez disso, você deveria usar elementos de propriedade. Consulte os tópicos de referência para <xref:System.Windows.Data.MultiBinding> e <xref:System.Windows.Data.PriorityBinding>.  
  
 Os valores boolianos para XAML não diferenciam maiúsculas de minúsculas. Por exemplo você pode especificar um `{Binding NotifyOnValidationError=true}` ou `{Binding NotifyOnValidationError=True}`.  
  
 Associações que envolvem a validação de dados normalmente são especificadas por uma explícita `Binding` elemento, em vez de como um `{Binding ...}` expressão e configuração <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ou <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> em uma expressão é incomum. Isso ocorre porque a propriedade complementar <xref:System.Windows.Data.Binding.ValidationRules%2A> não é possível definir prontamente na forma de expressão. Para obter mais informações, consulte [Implementar validação de associação](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md).  
  
 `Binding` é uma extensão da marcação. As extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores e o requisito é mais global do que conversores de tipo atribuídos em certos tipos ou propriedades. Todas as extensões de marcação no XAML usam os caracteres `{` e `}` na sintaxe de atributo, que é a convenção pela qual o processador XAML reconhece que uma extensão de marcação precisa processar o conteúdo da cadeia de caracteres. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 `Binding`é uma extensão de marcação atípicos em que o <xref:System.Windows.Data.Binding> classe que implementa a funcionalidade de extensão para a implementação do WPF XAML também implementa vários outros métodos e propriedades que não estão relacionadas a XAML. Os outros membros destinam-se para fazer <xref:System.Windows.Data.Binding> uma classe mais versátil e independente que pode atender muitos cenários de associação de dados, além de funcionar como uma extensão de marcação XAML.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.Binding>  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
