---
title: Extensão de marcação ComponentResourceKey
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243356"
---
# <a name="componentresourcekey-markup-extension"></a>Extensão de marcação ComponentResourceKey
Define e referencia chaves para recursos carregados de assemblies externos. Isso permite que um recurso de pesquisa especifique um tipo de destino em um assembly, em vez de um dicionário de recurso explícito em um assembly ou em uma classe.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Uso do atributo XAML (configuração de chave, compacta)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Uso do atributo XAML (configuração de chave, detalhada)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Uso do atributo XAML (solicitação de recurso, compacta)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Uso do atributo XAML (solicitação de recurso, detalhada)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`targetTypeName`|O nome do tipo de tempo de execução de linguagem comum pública (CLR) que é definido na montagem de recursos.|  
|`targetID`|A chave para o recurso. Quando recursos forem pesquisados, `targetID` será análogo à [Diretiva X:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) do recurso.|  
  
## <a name="remarks"></a>Comentários  
 Como visto nos usos acima, um uso de extensão de marcação {`ComponentResourceKey`} é encontrado em dois locais:  
  
- A definição de uma chave em um dicionário de recursos de tema, conforme fornecido por um autor de controle.  
  
- Acessando um recurso de tema do assembly, quando você está remodelando o controle, mas deseja usar valores de propriedade que vêm dos recursos fornecidos pelos temas do controle.  
  
 Para fazer referência a recursos de componente que vêm de temas, geralmente é recomendável usar `{DynamicResource}`, em vez de `{StaticResource}`. Isso é mostrado em usos. `{DynamicResource}` é recomendado porque o tema em si pode ser alterado pelo usuário. Se você desejar que o recurso do componente que mais se aproxima da intenção do autor do controle para dar suporte a um tema, habilite a referência de recurso do componente para que seja dinâmica também.  
  
 O <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifica um tipo que existe no conjunto de destino onde o recurso é realmente definido. A `ComponentResourceKey` pode ser definido e usado independentemente de saber exatamente onde o <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> é definido, mas eventualmente deve resolver o tipo através de assembléias referenciadas.  
  
 Um uso <xref:System.Windows.ComponentResourceKey> comum para é definir chaves que são então expostas como membros de uma classe. Para este uso, <xref:System.Windows.ComponentResourceKey> você usa o construtor de classe, não a extensão de marcação. Para obter mais <xref:System.Windows.ComponentResourceKey>informações, consulte ou a seção "Definindo e Referenciando chaves para recursos temáticos" da visão geral da [autora do](../controls/control-authoring-overview.md)tópico Controle .  
  
 Para estabelecer chaves e referenciar recursos de chave, sintaxe do atributo normalmente é usada para a extensão de marcação `ComponentResourceKey`.  
  
 A sintaxe compacta <xref:System.Windows.ComponentResourceKey.%23ctor%2A> mostrada baseia-se na assinatura do construtor e no uso do parâmetro posicional de uma extensão de marcação. A ordem na qual o `targetTypeName` e o `targetID` são apresentados é importante. A sintaxe verbose <xref:System.Windows.ComponentResourceKey.%23ctor%2A> se baseia no construtor sem parâmetros, e então define o <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> e <xref:System.Windows.ComponentResourceKey.ResourceId%2A> de uma forma análoga a uma verdadeira sintaxe de atributo em um elemento objeto. Na sintaxe detalhada, a ordem na qual as propriedades são definidas não é importante. O relacionamento e os mecanismos dessas duas alternativas (compacta e detalhada) é descrito em mais detalhes no tópico [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Tecnicamente, o valor de `targetID` pode ser qualquer objeto, não precisa ser uma cadeia de caracteres. No entanto, o uso mais comum no WPF é alinhar o valor `targetID` com formulários que são cadeias de caracteres e o ponto em que tais cadeias são válidas na [Gramática XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md).  
  
 O `ComponentResourceKey` pode ser usado na sintaxe de elemento de objeto. Neste caso, especificar o valor <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> <xref:System.Windows.ComponentResourceKey.ResourceId%2A> das propriedades e das propriedades é necessário para inicializar adequadamente a extensão.  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação do leitor, o manuseio para esta <xref:System.Windows.ComponentResourceKey> extensão de marcação é definido pela classe.  
  
 `ComponentResourceKey` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Visão geral da criação de controle](../controls/control-authoring-overview.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md)
