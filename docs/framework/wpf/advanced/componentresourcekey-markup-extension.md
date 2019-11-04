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
ms.openlocfilehash: 85e6862d59284df1b51bf5ea7fbba786fe0492d7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458961"
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
|`targetTypeName`|O nome do tipo de Common Language Runtime público (CLR) que é definido no assembly de recurso.|  
|`targetID`|A chave para o recurso. Quando recursos forem pesquisados, `targetID` será análogo à [Diretiva X:Key](../../xaml-services/x-key-directive.md) do recurso.|  
  
## <a name="remarks"></a>Comentários  
 Como visto nos usos acima, um uso de extensão de marcação {`ComponentResourceKey`} é encontrado em dois locais:  
  
- A definição de uma chave em um dicionário de recursos de tema, conforme fornecido por um autor de controle.  
  
- Acessando um recurso de tema do assembly, quando você está remodelando o controle, mas deseja usar valores de propriedade que vêm dos recursos fornecidos pelos temas do controle.  
  
 Para fazer referência a recursos de componente que vêm de temas, geralmente é recomendável usar `{DynamicResource}`, em vez de `{StaticResource}`. Isso é mostrado em usos. `{DynamicResource}` é recomendado porque o tema em si pode ser alterado pelo usuário. Se você desejar que o recurso do componente que mais se aproxima da intenção do autor do controle para dar suporte a um tema, habilite a referência de recurso do componente para que seja dinâmica também.  
  
 O <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifica um tipo que existe no assembly de destino onde o recurso está realmente definido. Um `ComponentResourceKey` pode ser definido e usado independentemente de saber exatamente onde o <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> está definido, mas eventualmente deve resolver o tipo por meio de assemblies referenciados.  
  
 Um uso comum para <xref:System.Windows.ComponentResourceKey> é definir chaves que são então expostas como membros de uma classe. Para esse uso, você usa o construtor da classe <xref:System.Windows.ComponentResourceKey>, não a extensão de marcação. Para obter mais informações, consulte <xref:System.Windows.ComponentResourceKey>ou a seção "definindo e referenciando chaves para recursos de tema" do tópico [visão geral da criação do controle](../controls/control-authoring-overview.md)de tópicos.  
  
 Para estabelecer chaves e referenciar recursos de chave, sintaxe do atributo normalmente é usada para a extensão de marcação `ComponentResourceKey`.  
  
 A sintaxe do Compact mostrada depende da assinatura do construtor de <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> e do uso do parâmetro posicional de uma extensão de marcação. A ordem na qual o `targetTypeName` e o `targetID` são apresentados é importante. A sintaxe detalhada depende do <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Construtor sem parâmetros e, em seguida, define o <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> e <xref:System.Windows.ComponentResourceKey.ResourceId%2A> de forma que seja análoga a uma sintaxe de atributo verdadeira em um elemento Object. Na sintaxe detalhada, a ordem na qual as propriedades são definidas não é importante. O relacionamento e os mecanismos dessas duas alternativas (compacta e detalhada) é descrito em mais detalhes no tópico [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Tecnicamente, o valor de `targetID` pode ser qualquer objeto, não precisa ser uma cadeia de caracteres. No entanto, o uso mais comum no WPF é alinhar o valor `targetID` com formulários que são cadeias de caracteres e o ponto em que tais cadeias são válidas na [Gramática XamlName](../../xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` pode ser usado na sintaxe de elemento de objeto. Nesse caso, especificar o valor das propriedades <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> e <xref:System.Windows.ComponentResourceKey.ResourceId%2A> é necessário para inicializar corretamente a extensão.  
  
 Na implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Reader, o tratamento para essa extensão de marcação é definido pela classe <xref:System.Windows.ComponentResourceKey>.  
  
 `ComponentResourceKey` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Visão geral da criação de controle](../controls/control-authoring-overview.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md)
