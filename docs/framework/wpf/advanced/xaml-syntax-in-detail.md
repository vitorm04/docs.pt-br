---
title: Sintaxe XAML em detalhes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88e66210fd8066e82a11d07ea0cfeb83808d646c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-syntax-in-detail"></a>Sintaxe XAML em detalhes
Este tópico define os termos que são usados para descrever os elementos da sintaxe XAML. Esses termos são usados com frequência durante o restante desta documentação, tanto especificamente para a documentação do WPF quanto para as outras estruturas que usam XAML ou os conceitos básicos do XAML habilitados pelo suporte à linguagem XAML no nível de System.Xaml. Este tópico trata mais a fundo da terminologia básica introduzida no tópico [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>Especificação da Linguagem XAML  
 A terminologia de sintaxe XAML definida aqui também é definida ou referenciada dentro da especificação da linguagem XAML. XAML é uma linguagem baseada em XML e segue ou expande regras estruturais do XML. Parte da terminologia é compartilhada com ou se baseia na terminologia usada com frequência ao descrever a linguagem XML ou o modelo de objeto do documento XML.  
  
 Para obter mais informações sobre a especificação da linguagem XAML, baixe [\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525) do Centro de Download da Microsoft.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML e CLR  
 XAML é uma linguagem de marcação. O [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], como o nome diz, permite a execução em tempo de execução. XAML por si só não é uma das linguagens comuns diretamente consumidas pelo tempo de execução de CLR. Em vez disso, você pode pensar em XAML como dando suporte a seu próprio sistema de tipos. O sistema de análise de XAML específico que é usado pelo WPF se baseia no CLR e o sistema de tipos do CLR. Tipos XAML são mapeados para tipos do CLR para instanciar uma representação de tempo de execução quando o XAML para WPF é analisado. Por esse motivo, o restante da discussão de sintaxe neste documento incluirá referências ao sistema de tipos do CLR, embora as discussões de sintaxe equivalentes na especificação da linguagem XAML não o façam. (Segundo o nível de especificação da linguagem XAML, tipos de XAML podem ser mapeados para qualquer outro sistema de tipos, o que significa que esse sistema não precisa ser o CLR; no entanto, isso exigiria a criação e uso de um analisador XAML diferente.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Membros de tipos e herança de classe  
 Propriedades e eventos, tal como aparecem como membros XAML de um tipo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], muitas vezes são herdados de tipos base. Considere este exemplo: `<Button Background="Blue" .../>`. O <xref:System.Windows.Controls.Control.Background%2A> propriedade não é uma propriedade imediatamente declarada no <xref:System.Windows.Controls.Button> de classe, se você observar a definição de classe, resultados de reflexo ou a documentação. Em vez disso, <xref:System.Windows.Controls.Control.Background%2A> é herdado da base de <xref:System.Windows.Controls.Control> classe.  
  
 O comportamento de herança de classe de elementos XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é uma mudança significativa de uma interpretação de marcação XML imposta pelo esquema. A herança de classe pode se tornar complexa, especialmente quando classes base intermediárias são abstratas ou interfaces estão envolvidas. Esse é um motivo pelo qual é difícil representar precisamente e completamente o conjunto de elementos XAML e seus atributos permitidos usando os tipos de esquema que são normalmente usados para programação [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], tais como os formatos DTD ou XSD. Outro motivo é que os recursos de extensibilidade e mapeamento de tipo da própria linguagem XAML impedem a integridade de qualquer representação fixa dos tipos e membros permitidos.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Sintaxe de elemento de objeto  
 *Sintaxe de elemento de objeto* é a sintaxe de marcação XAML que instancia uma estrutura ou classe CLR pela declaração de um elemento XML. Essa sintaxe é semelhante à sintaxe de outras linguagens de marcação como HTML. A sintaxe de elemento de objeto começa com um colchete angular esquerdo (\<), seguido imediatamente do nome do tipo da classe ou estrutura sendo instanciada. Zero ou mais espaços podem seguir o nome do tipo e zero ou mais atributos podem também ser declarados no elemento de objeto, com um ou mais espaços separando o par nome="valor" de cada atributo. Por fim, uma das seguintes condições deve ser verdadeira:  
  
-   O elemento e a marca devem ser fechadas por uma barra (/) seguida imediatamente de um colchete angular direito (>).  
  
-   A marca de abertura deve ser concluída por um colchete angular direito (>). Outros elementos de objeto, elementos de propriedade ou texto interno podem vir após a marca de abertura. Exatamente que conteúdo pode estar contido aqui é normalmente restrito pelo modelo de objeto do elemento. A marca de fechamento equivalente para o elemento de objeto também deve existir, com aninhamento e equilíbrio adequados em relação a outros pares de marca de abertura e fechamento.  
  
 XAML, conforme implementado pelo .NET, tem um conjunto de regras que mapeiam elementos de objeto para tipos, atributos para propriedades ou eventos e, por fim namespaces XAML para namespaces CLR mais assembly. Para o WPF e o .NET Framework, elementos de objeto XAML são mapeados para tipos do [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] conforme definido em assemblies referenciados, enquanto os atributos são mapeados para membros desses tipos. Quando você referencia um tipo CLR em XAML, você tem acesso também aos membros herdados desse tipo.  
  
 Por exemplo, o exemplo a seguir é a sintaxe de elemento de objeto que cria uma nova instância do <xref:System.Windows.Controls.Button> de classe e também especifica um <xref:System.Windows.FrameworkElement.Name%2A> atributo e um valor para o atributo:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 O exemplo a seguir é uma sintaxe de elemento de objeto que também inclui a sintaxe de propriedade de conteúdo XAML. O texto interno será usado para definir o <xref:System.Windows.Controls.TextBox> propriedade de conteúdo XAML, <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modelos de conteúdo  
 Uma classe pode dar suporte a um uso como um elemento de objeto XAML em termos da sintaxe, mas esse elemento só funcionará corretamente em um aplicativo ou página quando ele for colocado em uma posição esperada de uma árvore de elementos ou modelo de conteúdo geral. Por exemplo, um <xref:System.Windows.Controls.MenuItem> deve normalmente ser colocado apenas como um filho de um <xref:System.Windows.Controls.Primitives.MenuBase> classe derivada como <xref:System.Windows.Controls.Menu>. Modelos de conteúdo para elementos específicos são documentados como parte dos comentários nas páginas de classe para controles e outras classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que podem ser usadas como elementos XAML.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Propriedades de elementos de objeto  
 Propriedades em XAML são definidas por uma variedade de sintaxes possíveis. Qual sintaxe pode ser usada para uma determinada propriedade é algo que varia com base nas características do sistema de tipos subjacente da propriedade que você está configurando.  
  
 configurando valores de propriedades, você adiciona recursos ou características a objetos que existem no grafo de objeto em tempo de execução. O estado inicial do objeto criado de um elemento de objeto baseia-se no comportamento do construtor padrão. Normalmente, seu aplicativo usará algo diferente de uma instância completamente padronizada de um determinado objeto.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Sintaxe de atributo (Propriedades)  
 Sintaxe de atributo é a sintaxe de marcação XAML que define um valor para uma propriedade, declarando um atributo em um elemento de objeto existente. O nome do atributo deve corresponder ao nome do membro CLR da propriedade da classe dá suporte ao elemento de objeto relevante. O nome do atributo é seguido por um operador de atribuição (=). O valor do atributo deve ser uma cadeia de caracteres entre aspas.  
  
> [!NOTE]
>  Você pode usar aspas alternadas para colocar aspas literais dentro de um atributo. Por exemplo, você pode usar aspas simples como meio para declarar uma cadeia de caracteres que contém um caractere de aspas duplas. Independentemente de você usar aspas simples ou duplas, você deve usar um par correspondente para abrir e fechar a cadeia de caracteres de valor de atributo. Também há sequências de escape ou outras técnicas disponíveis para contornar as restrições de caracteres impostas por qualquer sintaxe XAML específica. Consulte [Entidades de caractere XML e XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 Para ser configurada via sintaxe de atributo, uma propriedade deve ser pública e deve ser gravável. O valor da propriedade no sistema de tipos de suporte deve ser um tipo de valor ou deve ser um tipo de referência que possa ser instanciado ou referenciado por um processador XAML ao acessar o tipo de suporte relevante.  
  
 Para eventos de XAML WPF, o evento que é referenciado como o nome do atributo deve ser público e ter um delegado público.  
  
 A propriedade ou evento deve ser um membro da classe ou estrutura que é instanciada pelo elemento de objeto recipiente.  
  
### <a name="processing-of-attribute-values"></a>Processamento de valores de atributo  
 O valor de cadeia de caracteres dentro das aspas de abertura e fechamento é processado por um processador XAML. Para propriedades, o comportamento padrão de processamento é determinado pelo tipo da propriedade CLR subjacente.  
  
 O valor do atributo é preenchido por um dos seguintes, usando esta ordem de processamento:  
  
1.  Se o processador XAML encontrar uma chave ou um elemento de objeto que é derivada de <xref:System.Windows.Markup.MarkupExtension>, em seguida, a extensão de marcação referenciada é avaliada primeiro, em vez de processar o valor como uma cadeia de caracteres e o objeto retornado pela extensão de marcação é usado como o valor. Em muitos casos, o objeto retornado por uma extensão de marcação será uma referência a um objeto existente ou então uma expressão que adia a avaliação até o tempo de execução, mas não será um objeto recém-instanciado.  
  
2.  Se a propriedade é declarada com um atributo <xref:System.ComponentModel.TypeConverter>, ou o tipo de valor dessa propriedade é declarado com um atributo <xref:System.ComponentModel.TypeConverter>, o valor de cadeia de caracteres do atributo é enviado para o conversor de tipo como uma entrada de conversão e o conversor retornará um nova instância de objeto.  
  
3.  Se não houver nenhum <xref:System.ComponentModel.TypeConverter>, será tentada uma conversão direta para o tipo de propriedade. Esse nível final é uma conversão direta do valor nativo do analisador entre tipos primitivos de linguagem XAML ou então uma verificação de nomes de constantes nomeadas em uma enumeração (o analisador então acessa os valores correspondentes).  
  
#### <a name="enumeration-attribute-values"></a>Valores de atributo de enumeração  
 Enumerações em XAML são processadas intrinsecamente pelos analisadores XAML e os membros de uma enumeração devem ser definidos especificando-se o nome da cadeia de caracteres de uma das constantes nomeadas da enumeração.  
  
 Para valores de enumeração não sinalizadores, o comportamento nativo é processar a cadeia de caracteres de um valor de atributo e resolvê-lo para um dos valores de enumeração. Você não especifica a enumeração no formato *Enumeração*.*Valor*, do modo como você faz no código. Em vez disso, você especifica somente *Valor*, enquanto *Enumeração* é inferido pelo tipo da propriedade você está configurando. Se você especificar um atributo no formato *Enumeração*.*Valor*, ele não será resolvido corretamente.  
  
 Para enumerações flagwise, o comportamento se baseia o <xref:System.Enum.Parse%2A?displayProperty=nameWithType> método. Você pode especificar vários valores para uma enumeração sinalizadora, separando cada valor com uma vírgula. No entanto, não é possível combinar valores de enumeração que não reconhecem sinalizadores. Por exemplo, você não pode usar a sintaxe de vírgulas para tentar criar um <xref:System.Windows.Trigger> que atua em várias condições de uma enumeração nonflag:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Enumerações sinalizadoras que dão suporte a atributos que são configuráveis no XAML são raras no WPF. No entanto, é uma enumeração <xref:System.Windows.Media.StyleSimulations>. Por exemplo, você poderia usar a sintaxe de atributo flagwise delimitado por vírgulas para modificar o exemplo fornecido nos comentários para a <xref:System.Windows.Documents.Glyphs> classe; `StyleSimulations = "BoldSimulation"` pode se tornar `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>é outra propriedade onde mais de um valor de enumeração pode ser especificado. No entanto, essa propriedade é um caso especial, porque o <xref:System.Windows.Input.ModifierKeys> enumeração dá suporte a seu próprio conversor de tipo. O conversor de tipo para modificadores usa um sinal de adição (+) como um delimitador em vez de uma vírgula (,). Essa conversão dá suporte à sintaxe mais tradicional para representar combinações de teclas na programação do Microsoft Windows, como "Ctrl + Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Propriedades e referências de nome de membro de evento  
 Ao especificar um atributo, você pode referenciar qualquer propriedade ou evento existente como um membro do tipo CLR que você instanciou para o elemento de objeto que o contém.  
  
 Ou você pode fazer referência a uma propriedade anexada ou evento anexado, independente do elemento de objeto que o contém. (Propriedades anexadas são discutidas em uma seção posterior).  
  
 Você também pode nomear qualquer evento de qualquer objeto que possa ser acessado através do namespace padrão usando um nome parcialmente qualificado *typeName*.*evento*; essa sintaxe dá suporte à anexação de manipuladores para eventos roteados em que o manipulador destina-se a manipular o roteamento de eventos de elementos filho, mas o elemento pai também não tem esse evento em sua tabela de membros. Essa sintaxe é semelhante a uma sintaxe de evento anexado, mas o evento aqui não é um evento anexado verdadeiro. Em vez disso, você está referenciando um evento com um nome qualificado. Para obter mais informações, consulte [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Em alguns cenários, os nomes de propriedade às vezes são fornecidos como o valor de um atributo, em vez do nome do atributo. Esse nome de propriedade também pode incluir qualificadores como a propriedade especificada no formato *ownerType*.*dependencyPropertyName*. Esse cenário é comum ao escrever estilos ou modelos em XAML. As regras de processamento para nomes de propriedade fornecidos como um valor de atributo são diferentes e são regidas pelo tipo da propriedade sendo definida ou os comportamentos de subsistemas do WPF específicos. Para obter detalhes, consulte [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Outro uso para nomes de propriedade é quando um valor de atributo descreve uma relação propriedade-propriedade. Esse recurso é usado para associação de dados e para destinos storyboard e é habilitado pela <xref:System.Windows.PropertyPath> classe e o conversor de tipos. Para obter uma descrição mais completa da semântica de pesquisa, consulte [Sintaxe XAML PropertyPath](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Sintaxe de elemento de propriedade  
 *Sintaxe de elemento de propriedade* é uma sintaxe que diverge um pouco das regras de sintaxe XML básicas para elementos. Em XML, o valor de um atributo é uma cadeia de caracteres de fato, com a única variação possível sendo qual formato de codificação de cadeia de caracteres está sendo usado. Em XAML, você pode atribuir outros elementos de objeto para serem o valor de uma propriedade. Essa funcionalidade é habilitada pela sintaxe de elemento de propriedade. Em vez de a propriedade ser especificada como um atributo na marca de elemento, a propriedade é especificada usando uma marca de elemento de abertura na forma *elementTypeName*.*propertyName*, o valor da propriedade é especificado ali e então o elemento de propriedade é fechado.  
  
 Especificamente, a sintaxe começa com um colchete angular esquerdo (\<), seguido imediatamente do nome do tipo da classe ou estrutura dentro da qual a sintaxe de elemento de propriedade está contida. Isso é seguido imediatamente por um único ponto (.), depois pelo nome de uma propriedade e, em seguida, por um sinal de maior (>). Assim como acontece com a sintaxe de atributo, essa propriedade deve existir nos membros públicos declarados do tipo especificado. O valor a ser atribuído à propriedade está contido dentro do elemento de propriedade. Normalmente, o valor é fornecido como um ou mais elementos de objeto, porque a especificação de objetos como valores é o cenário que essa sintaxe de elemento de propriedade destina-se a solucionar. Por fim, uma marca de fechamento equivalente especificando a mesma combinação *elementTypeName*.*propertyName* deve ser fornecida, com aninhamento e equilíbrio adequados em relação a outras marcas de elemento.  
  
 Por exemplo, esta é a sintaxe de elemento de propriedade para o <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriedade de um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 O valor em um elemento de propriedade pode também ser fornecido como texto interno, em casos onde o tipo de propriedade especificado é um tipo de valor primitivo, como <xref:System.String>, ou uma enumeração na qual um nome é especificado. Esses dois usos são um pouco incomuns, pois cada um desses casos também pode usar uma sintaxe de atributo mais simples. Um cenário para preencher um elemento de propriedade com uma cadeia de caracteres é para propriedades que não são a propriedade de conteúdo XAML, mas ainda assim são usadas para representação de texto da interface do usuário, sendo que é obrigatório que elementos de espaço em branco específicos como avanços de linha apareçam nesse texto da interface do usuário. A sintaxe de atributo não é capaz de preservar avanços de linha, mas a sintaxe de elemento de propriedade pode fazê-lo desde que a preservação de espaço em branco significativo esteja ativa (para obter detalhes, consulte [Processamento de espaço em branco em XAML](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)). Outro cenário é aquele no qual a [Política x:Uid](../../../../docs/framework/xaml-services/x-uid-directive.md) pode ser aplicada ao elemento de propriedade e, portanto, marca o valor dentro dele como um valor que deve ser localizado BAML de saída do no WPF ou por outras técnicas.  
  
 Um elemento de propriedade não é representado na árvore lógica do WPF. Um elemento de propriedade é apenas uma sintaxe específica para definir uma propriedade e não é um elemento que disponha do suporte de uma instância ou objeto. (Para obter detalhes sobre o conceito de árvore lógica, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).)  
  
 Para propriedades nas quais ambas a sintaxe de elemento de propriedade e a sintaxe de atributo têm suporte, essas duas sintaxes geralmente têm o mesmo resultado, embora sutilezas como a manipulação de espaço em branco possam variar ligeiramente entre elas.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Sintaxe de coleção  
 A especificação da linguagem XAML requer implementações de processador XAML para identificar propriedades nas quais o tipo de valor é uma coleção. A implementação geral de processador XAML no .NET é baseada em código gerenciado e no CLR e identifica os tipos de coleção por meio de um dos seguintes:  
  
-   Digite implementa <xref:System.Collections.IList>.  
  
-   Digite implementa <xref:System.Collections.IDictionary>.  
  
-   Tipo deriva de <xref:System.Array> (para obter mais informações sobre matrizes em XAML, consulte [extensão de marcação X:array](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
 Se o tipo de uma propriedade é uma coleção, o tipo da coleção inferido não precisa ser especificado na marcação como um elemento de objeto. Em vez disso, os elementos a se tornarem itens na coleção são especificados como um ou mais elementos filho do elemento de propriedade. Cada um desses itens é avaliado para um objeto durante o carregamento e adicionado à coleção chamando o método `Add` da coleção implícita. Por exemplo, o <xref:System.Windows.Style.Triggers%2A> propriedade <xref:System.Windows.Style> usa o tipo de coleção especializada <xref:System.Windows.TriggerCollection>, que implementa <xref:System.Collections.IList>. Não é necessário criar uma instância de um <xref:System.Windows.TriggerCollection> elemento do objeto na marcação. Em vez disso, você especificar um ou mais <xref:System.Windows.Trigger> itens como elementos dentro de `Style.Triggers` elemento de propriedade, onde <xref:System.Windows.Trigger> (ou uma classe derivada) é o tipo esperado como o tipo de item para o implícita e fortemente tipada <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Uma propriedade pode ser tanto um tipo de coleção quanto a propriedade de conteúdo XAML para esse tipo e tipos derivados, o que é abordado na próxima seção deste tópico.  
  
 Um elemento de coleção implícita cria um membro na representação de árvore lógica, mesmo que ele não apareça na marcação como um elemento. Geralmente o construtor do tipo pai faz a instanciação para a coleção que é uma de suas propriedades e a coleção inicialmente vazia torna-se parte da árvore de objetos.  
  
> [!NOTE]
>  Interfaces genéricas de lista e dicionário (<xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IDictionary%602>) não são suportadas para detecção de coleção. No entanto, você pode usar o <xref:System.Collections.Generic.List%601> classe como uma classe base, pois ela implementa <xref:System.Collections.IList> diretamente, ou <xref:System.Collections.Generic.Dictionary%602> como uma classe base, pois ela implementa <xref:System.Collections.IDictionary> diretamente.  
  
 Nas páginas de referência do .NET para tipos de coleção, essa sintaxe com a omissão deliberada do elemento de objeto para uma coleção é ocasionalmente mencionada nas seções de sintaxe XAML como sintaxe de coleção implícita.  
  
 Com exceção do elemento raiz, cada elemento de objeto em um arquivo XAML que está aninhado como um elemento filho de outro elemento é na realidade um elemento que se enquadra em um ou ambos os casos a seguir: um membro de uma propriedade de coleção implícita do seu elemento pai ou então um elemento que especifica o valor da propriedade de conteúdo XAML para o elemento pai (propriedades de conteúdo XAML serão discutidas em uma seção posterior). Em outras palavras, a relação dos elementos pai e filho em uma página de marcação é na verdade um único objeto na raiz, sendo que todo elemento de objeto abaixo da raiz é uma instância única que fornece um valor da propriedade do pai ou então é um dos itens dentro de uma coleção que é também um valor da propriedade de tipo de coleção do pai. Esse conceito de raiz única é comum com XML e frequentemente é reforçado no comportamento de APIs que carregar XAML, como <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 O exemplo a seguir é uma sintaxe com o elemento de objeto para uma coleção (<xref:System.Windows.Media.GradientStopCollection>) especificado explicitamente.  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 Observe que nem sempre é possível declarar explicitamente a coleção. Por exemplo, tentando declarar <xref:System.Windows.TriggerCollection> explicitamente em mostradas anteriormente <xref:System.Windows.Style.Triggers%2A> exemplo falhará. Declarar explicitamente a coleção requer que a classe de coleção deve oferecer suporte a um construtor padrão, e <xref:System.Windows.TriggerCollection> não tem um construtor padrão.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>Propriedades de conteúdo XAML  
 Sintaxe de conteúdo XAML é uma sintaxe que está habilitada somente nas classes que especificam o <xref:System.Windows.Markup.ContentPropertyAttribute> como parte de sua declaração de classe. O <xref:System.Windows.Markup.ContentPropertyAttribute> faz referência ao nome de propriedade que é a propriedade de conteúdo para esse tipo de elemento (incluindo as classes derivadas). Quando processados por um processador XAML, quaisquer elementos filho ou texto interno que sejam encontrados entre as marcas de abertura e fechamento do elemento de objeto serão atribuídos como sendo o valor da propriedade de conteúdo XAML para esse objeto. Você tem permissão para especificar elementos de propriedade explícitos para a propriedade de conteúdo, mas esse uso geralmente não é mostrado nas seções de sintaxe XAML na referência do .NET. A técnica explícita/detalhada tem valor ocasional para fins de esclarecimento de marcação ou como uma questão de estilo de marcação, mas a intenção de uma propriedade de conteúdo costuma ser simplificar a marcação para que os elementos relacionados intuitivamente como pai/filho possam ser diretamente aninhados. Marcas de elemento de propriedade para outras propriedades em um elemento não são atribuídas como "conteúdo" segundo uma definição estrita de linguagem XAML; eles são processados anteriormente na ordem de processamento do analisador XAML e não são considerados "conteúdo".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Valores de propriedade de conteúdo XAML devem ser contíguos  
 O valor de uma propriedade de conteúdo XAML deve ser fornecido inteiramente antes ou inteiramente depois de todos os outros elementos de propriedade nesse elemento de objeto. Isso é verdadeiro se o valor de uma propriedade de conteúdo XAML é especificado como uma cadeia de caracteres ou como um ou mais objetos. Por exemplo, a marcação a seguir não analisa:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Isso é ilegal essencialmente porque se essa sintaxe tivesse sido tornada explícita usando sintaxe de elemento de propriedade para a propriedade de conteúdo, a propriedade de conteúdo seria definida duas vezes:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Um exemplo similarmente ilegal é no caso de a propriedade de conteúdo ser uma coleção e elementos filho serem intercalados com elementos de propriedade:  
  
```xml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>Propriedades de conteúdo e sintaxe de coleção combinados  
 Para aceitar mais de um único elemento de objeto como conteúdo, o tipo da propriedade de conteúdo deve ser especificamente um tipo de coleção. Semelhante à sintaxe de elemento de propriedade para tipos de coleção, um processador XAML deve identificar tipos que são tipos de coleção. Se um elemento tem uma propriedade de conteúdo XAML e o tipo da propriedade de conteúdo XAML é uma coleção, o tipo de coleção sugerido não precisa ser especificado na marcação como um elemento de objeto e a propriedade de conteúdo XAML não precisa ser especificada como um elemento de propriedade. Portanto, o modelo de conteúdo aparente na marcação agora pode ter mais de um elemento filho atribuído como o conteúdo. A seguir está a sintaxe de conteúdo para um <xref:System.Windows.Controls.Panel> classe derivada. Todos os <xref:System.Windows.Controls.Panel> classes derivadas estabelecer a propriedade de conteúdo XAML para ser <xref:System.Windows.Controls.Panel.Children%2A>, que requer um valor do tipo <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Observe que nem o elemento de propriedade <xref:System.Windows.Controls.Panel.Children%2A> nem o elemento para o <xref:System.Windows.Controls.UIElementCollection> é necessária na marcação. Esse é um recurso de design do XAML para que elementos recursivamente contidos que definem um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sejam representados mais intuitivamente como uma árvore de elementos aninhados com relações pai/filho imediatas, sem objetos de coleção ou marcas entrepostas. Na verdade, <xref:System.Windows.Controls.UIElementCollection> não pode ser especificado explicitamente na marcação como um elemento de objeto, por design. Como seu único uso pretendido é como uma coleção implícita, <xref:System.Windows.Controls.UIElementCollection> não expõe um construtor público padrão e, portanto, não pode ser instanciado como um elemento de objeto.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Combinação de elementos de propriedade e elementos de objeto em um objeto com uma propriedade de conteúdo  
 A especificação da linguagem XAML declara que um processador XAML pode impor que elementos de objeto que são usados para preencher a propriedade de conteúdo XAML dentro de um elemento de objeto precisem ser contíguos e não possam ser misturados. Essa restrição contra misturar elementos de propriedade e conteúdo é imposta pelos processadores XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Você pode ter um elemento de objeto filho como a primeira marcação imediata dentro de um elemento de objeto. Em seguida, você pode introduzir elementos de propriedade. Ou ainda, você pode especificar um ou mais elementos de propriedade, então conteúdo e depois mais elementos de propriedade. Mas uma vez que um elemento de propriedade segue o conteúdo, você não pode introduzir nenhum conteúdo adicional, você só pode adicionar elementos de propriedade.  
  
 Este requisito de ordem de elementos de propriedade/conteúdo não se aplica ao texto interno usado como conteúdo. No entanto, esse ainda é um bom estilo de marcação para manter o texto interno contíguo, porque o espaço em branco significativo será difícil de detectar visualmente na marcação se elementos de propriedade forem intercalados com texto interno.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>Namespaces XAML  
 Nenhum dos exemplos de sintaxe anteriores especificaram um namespace XAML diferente do namespace XAML padrão. Em aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] típicos, o namespace XAML padrão é especificado como sendo o namespace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Você pode especificar namespaces XAML diferentes do namespace XAML padrão e ainda assim usar uma sintaxe semelhante. Mas nesse casso, em qualquer lugar em que for nomeada uma classe não acessível dentro do namespace XAML padrão, esse nome de classe deverá ser precedido do prefixo do namespace XAML conforme mapeado para o namespace CLR correspondente. Por exemplo, `<custom:Example/>` é a sintaxe de elemento de objeto para criar uma instância da classe `Example`, em que o namespace CLR que contém essa classe (e possivelmente as informações de assembly externo que contêm tipos de suporte) foi anteriormente mapeado para o prefixo `custom`.  
  
 Para obter mais informações sobre namespaces XAML, consulte [Namespaces XAML e mapeamento de namespace para XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Extensões de marcação  
 O XAML define uma entidade de programação de extensão de marcação que habilita um escape da manipulação normal de valores de atributo de cadeia de caracteres ou elementos de objeto pelo processador XAML e adia o processamento para uma classe de suporte. O caractere que identifica um extensão de marcação para um processador XAML ao usar a sintaxe de atributo é a chave de abertura ({), seguida por qualquer caractere que não seja uma chave de fechamento (}). A primeira cadeia de caracteres após a chave de abertura deve fazer referência à classe que oferece o comportamento de extensão específico, em que a referência pode omitir a subcadeia de caracteres "Extension" se essa subcadeia faz parte do verdadeiro nome de classe. Depois disso, pode aparecer um único espaço e, em seguida, cada caractere subsequente é usado como entrada pela implementação de extensão até que a chave de fechamento é encontrada.  
  
 A implementação de XAML .NET usa o <xref:System.Windows.Markup.MarkupExtension> classe abstrata como base para todas as extensões de marcação com suporte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , bem como outras estruturas ou tecnologias. As extensões de marcação que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementa especificamente geralmente se destinam a fornecer um meio para fazer referência a outros objetos existentes ou fazer referências adiadas a objetos que serão avaliados em tempo de execução. Por exemplo, uma vinculação de dados simples do WPF é feita especificando a extensão de marcação `{Binding}` no lugar do valor que uma propriedade específica normalmente aceitaria. Muitas das extensões de marcação do WPF permitem uma sintaxe de atributo para propriedades em que a sintaxe de atributo não seria possível de outra maneira. Por exemplo, um <xref:System.Windows.Style> objeto é um tipo relativamente complexo que contém uma série aninhada de objetos e propriedades. Estilos no WPF geralmente são definidos como um recurso em um <xref:System.Windows.ResourceDictionary>e depois referenciado por meio de uma das duas extensões de marcação WPF que solicitam um recurso. A extensão de marcação adia a avaliação do valor de propriedade para um recurso de pesquisa e permite fornecer o valor da <xref:System.Windows.FrameworkElement.Style%2A> propriedade, levando tipo <xref:System.Windows.Style>, no atributo sintaxe como no exemplo a seguir:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Aqui, `StaticResource` identifica o <xref:System.Windows.StaticResourceExtension> classe fornecendo a implementação de extensão de marcação. A próxima cadeia `MyStyle` é usado como entrada para o não-padrão <xref:System.Windows.StaticResourceExtension> construtor, onde o parâmetro como extraído da cadeia de caracteres de extensão declara o pedido <xref:System.Windows.ResourceKey>. `MyStyle`deve ser o [X:Key](../../../../docs/framework/xaml-services/x-key-directive.md) valor de um <xref:System.Windows.Style> definido como um recurso. O [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) uso solicita que o recurso seja usado para fornecer o <xref:System.Windows.Style> valor de propriedade por meio de lógica de busca de recurso estático no tempo de carregamento.  
  
 Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação e XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md). Para obter uma referência de extensões de marcação e outros recursos de programação em XAML habilitados na implementação geral do XAML no .NET, consulte [Recursos de linguagem (x:) do namespace XAML](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). Para extensões de marcação específicas de WPF, consulte [Extensões XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Propriedades anexadas  
 Propriedades anexadas são um conceito de programação introduzido no XAML no qual propriedades podem pertencer a um determinado tipo ou ser definidas por ele, mas definidas como atributos ou elementos de propriedade em qualquer elemento. O cenário principal para o qual propriedades anexadas se destinam é habilitar elementos filho em uma estrutura de marcação para relatar informações a um elemento pai sem exigir um modelo de objeto amplamente compartilhado entre todos os elementos. Por outro lado, propriedades anexadas podem ser usadas pelos elementos pai para relatar informações para elementos filhos. Para obter mais informações sobre o objetivo de propriedades anexadas e como criar suas próprias propriedades anexadas, consulte [Visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Propriedades anexadas utilizam uma sintaxe que superficialmente se assemelha à sintaxe de elemento de propriedade, em que você também especifica uma combinação *typeName*.*propertyName*. Há duas diferenças importantes:  
  
-   Você pode usar a combinação *typeName*.*propertyName* mesmo ao definir uma propriedade anexada por meio da sintaxe de atributo. Propriedades anexadas são o único caso em que a qualificação do nome da propriedade é um requisito em uma sintaxe de atributo.  
  
-   Você também pode usar a sintaxe de elemento de propriedade para propriedades anexadas. No entanto, para a sintaxe de elemento de propriedade típica, o *typeName* que você especifica é o elemento de objeto que contém o elemento de propriedade. Se você estiver fazendo referência a uma propriedade anexada, o *typeName* será a classe que define a propriedade anexada, não o elemento de objeto que a contém.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Eventos anexados  
 Eventos anexados são outro conceito de programação introduzido em XAML em que os eventos podem ser definidos por um tipo específico, mas manipuladores podem ser anexados a qualquer elemento de objeto. Na implementação WOF, geralmente o tipo que define um evento anexado é um tipo estático que define um serviço e, às vezes, esses eventos anexados são expostos por um alias de evento roteado em tipos que expõem o serviço. Manipuladores para eventos anexados são especificados pela sintaxe de atributo. Assim como ocorre com eventos anexados, a sintaxe de atributo é expandida para eventos anexados para permitir um uso de *typeName*.*eventName*, em que *typeName* é a classe que fornece os acessadores de manipuladores de eventos `Add` e `Remove` para a infraestrutura de evento anexado e *eventName* é o nome do evento.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomia de um elemento raiz XAML  
 A tabela a seguir mostra um típico elemento raiz XAML, mostrando os atributos específicos de um elemento raiz:  
  
|||  
|-|-|  
|`<Page`|Elemento de objeto de abertura do elemento raiz|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|O namespace XAML padrão ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)])|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Namespace XAML de linguagem XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|A declaração de classe parcial que conecta a marcação a qualquer code-behind definido para a classe parcial|  
|`>`|Final do elemento de objeto para a raiz. Objeto ainda não foi fechado porque o elemento contém elementos filho|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>Usos de XAML opcionais e não recomendados  
 As seções a seguir descrevem os usos de XAML que tem tecnicamente suporte em processadores XAML, mas que produzem detalhamento ou outros problemas estéticos que interferem com arquivos XAML, permanecendo legíveis quando você desenvolve aplicativos que contêm códigos-fonte XAML.  
  
### <a name="optional-property-element-usages"></a>Usos de elemento de propriedade opcional  
 Usos de elemento de propriedade opcional incluem escrever explicitamente propriedades de conteúdo de elemento que o processador XAML considera implícitas. Por exemplo, quando você declara o conteúdo de um <xref:System.Windows.Controls.Menu>, você poderia escolher declarar explicitamente o <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção do <xref:System.Windows.Controls.Menu> como um `<Menu.Items>` marca de elemento de propriedade e colocar cada <xref:System.Windows.Controls.MenuItem> dentro de `<Menu.Items>`, em vez disso que usar o comportamento de processador implícita do XAML que todos os elementos filho de um <xref:System.Windows.Controls.Menu> deve ser um <xref:System.Windows.Controls.MenuItem> e são colocados no <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção. Às vezes os usos opcionais podem ajudar a esclarecer visualmente a estrutura do objeto conforme representada na marcação. Ou, às vezes, um uso de elemento de propriedade explícito pode evitar uma marcação que é tecnicamente funcional, mas visualmente confusa, assim como extensões de marcação aninhadas dentro de um valor de atributo.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Atributos qualificados typeName.memberName completos  
 A forma *typeName*.*memberName* para um atributo realmente funciona mais universalmente do que apenas para o caso de evento roteado. Em outras situações, no entanto, essa forma é supérflua e você deve evitá-la, mesmo que apenas por motivos de estilo de marcação e legibilidade. No exemplo a seguir, cada uma das três referências para o <xref:System.Windows.Controls.Control.Background%2A> atributo são totalmente equivalentes:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`funciona porque a pesquisa qualificada para essa propriedade em <xref:System.Windows.Controls.Button> for bem-sucedida (<xref:System.Windows.Controls.Control.Background%2A> foi herdada de Control) e <xref:System.Windows.Controls.Button> é a classe do elemento de objeto ou uma classe base. `Control.Background`funciona porque o <xref:System.Windows.Controls.Control> realmente define uma classe <xref:System.Windows.Controls.Control.Background%2A> e <xref:System.Windows.Controls.Control> é um <xref:System.Windows.Controls.Button> classe base.  
  
 No entanto, exemplo de formato de *typeName*.*memberName* a seguir não funciona e, portanto, é mostrado comentado:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>é outra classe derivada de <xref:System.Windows.Controls.Control>, e se você tiver especificado `Label.Background` dentro de um <xref:System.Windows.Controls.Label> elemento de objeto, este uso teria funcionado. No entanto, como <xref:System.Windows.Controls.Label> não é a classe ou classe base de <xref:System.Windows.Controls.Button>, o comportamento especificado do processador XAML é processar `Label.Background` como uma propriedade anexada. `Label.Background` não é uma propriedade anexada disponível e esse uso falha.  
  
### <a name="basetypenamemembername-property-elements"></a>Elementos de propriedade baseTypeName.memberName  
 De maneira semelhante ao modo como o formulário *typeName*.*memberName* funciona para a sintaxe de atributo, uma sintaxe *baseTypeName*.*memberName* funciona para a sintaxe de elemento de propriedade. Por exemplo, a sintaxe a seguir funciona:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Aqui o elemento de propriedade foi fornecido como `Control.Background`, embora o elemento de propriedade estivesse contido em `Button`.  
  
 Mas assim como o formato *typeName*.*memberName* para atributos, *baseTypeName*.*memberName* é um estilo ruim de marcação e você deve evitá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Recursos da linguagem (x:) do namespace de XAML](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Extensões XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [TypeConverters e XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)  
 [XAML e classes personalizadas para WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
