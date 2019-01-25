---
title: Diretiva x:Name
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: 164b0283864cdeb60ef7b8e19c9d457f80ee4eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696458"
---
# <a name="xname-directive"></a>Diretiva x:Name
Identifica os elementos definidos pelo XAML em um namescope XAML. Namescopes XAML e seus modelos de exclusividade podem ser aplicados para objetos instanciados, quando estruturas fornecem APIs ou implementam comportamentos que acesse o gráfico de objeto criado pelo XAML em tempo de execução.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Uma cadeia de caracteres que está em conformidade com as restrições dos [gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## <a name="remarks"></a>Comentários  
 Depois de `x:Name` é aplicado a uma estrutura de suporte do modelo de programação, o nome é equivalente à variável que contém uma referência de objeto ou uma instância, conforme retornado por um construtor.  
  
 O valor de um `x:Name` o uso de diretiva deve ser exclusivo dentro de um namescope XAML. Por padrão quando usado pela API de serviços de XAML do .NET Framework, o namescope XAML primário é definido no elemento raiz XAML de uma única produção de XAML e abrange os elementos que estão contidos na produção XAML. Discretos namescopes XAML adicionais que podem ocorrer dentro de uma única produção de XAML podem ser definidos por estruturas para lidar com cenários específicos. Por exemplo, no WPF, novo namescopes XAML são definidos e criados por qualquer modelo que também esteja definido em produção esse XAML. Para obter mais informações sobre os namescopes XAML (escritos para o WPF, mas relevante para muitos conceitos de namescope XAML), consulte [Namescopes de XAML do WPF](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Em geral, `x:Name` não deve ser aplicada em situações que também usam `x:Key`. Implementações de XAML por estruturas existentes específicas introduziram conceitos de substituição entre `x:Key` e `x:Name`, mas que não é uma prática recomendada. Serviços de XAML do .NET framework não oferece suporte a esses conceitos de substituição ao lidar com informações de nome/chave, como <xref:System.Windows.Markup.INameScope> ou <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Regras para a permissão de `x:Name` , bem como a imposição de exclusividade de nome potencialmente são definidos por estruturas específicas de implementação. No entanto, para ser usado com serviços XAML do .NET Framework, as definições de estrutura de exclusividade de namescope XAML devem ser consistentes com a definição de <xref:System.Windows.Markup.INameScope> informações nesta documentação e deve usar as mesmas regras sobre onde o as informações são aplicadas. Por exemplo, o [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementação divide vários elementos de marcação em separado <xref:System.Windows.NameScope> intervalos como dicionários de recursos, a árvore lógica, o nível de página XAML, modelos e outros adiada conteúda criada e, em seguida, impõe XAML exclusividade do nome dentro de cada uma dessas namescopes XAML.  
  
 Para tipos personalizados que usam os gravadores de objeto XAML de serviços de XAML do .NET Framework, uma propriedade que é mapeado para `x:Name` em um tipo pode ser estabelecido ou alterado. Você define esse comportamento referenciando o nome da propriedade a ser mapeada com o <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> no código de definição de tipo.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> é um atributo de nível de tipo.  
  
 Serviços XAML do Framework Using.NET, a lógica de backup para o suporte de namescope XAML podem ser definidos de maneira neutra framework Implementando o <xref:System.Windows.Markup.INameScope> interface.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Sob a configuração de compilação padrão para um [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplicativo que usa XAML, classes parciais e code-behind, especificado `x:Name` torna-se o nome de um campo que é criado no subjacente código quando [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é processada por uma marcação tarefa de build de compilação e esse campo contém uma referência ao objeto. Por padrão, o campo criado é interno. Você pode alterar o acesso ao campo especificando o [atributo X:FieldModifier](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md). No WPF e Silverlight, a sequência é que a compilação de marcação define e nomes de campo em uma classe parcial, mas o valor é inicialmente vazio. Em seguida, um método gerado chamado `InitializeComponent` é chamado de dentro do construtor de classe. `InitializeComponent` consiste `FindName` chamadas usando cada um do `x:Name` cadeias de caracteres de entrada de valores que existem na parte da classe parcial, conforme definido em XAML. Os valores de retorno são então atribuídos a referência de campo de nome semelhante para preencher os valores de campo com objetos que foram criados de XAML de análise. A execução de `InitializeComponent` possibilitam a referência para o grafo de objeto de tempo de execução usando o `x:Name` / nome do campo diretamente, em vez de precisar chamar `FindName` explicitamente sempre que você precisa de uma referência a um objeto definido pelo XAML.  
  
 Para um WPF, o aplicativo que usa o Microsoft Visual Basic tem como alvo e inclui os arquivos XAML com `Page` ação de compilação, uma propriedade de referência separada é criada durante a compilação que adiciona o `WithEvents` palavra-chave para todos os elementos que têm um `x:Name`, para oferecer suporte `Handles` sintaxe para delegados de manipulador de eventos. Essa propriedade sempre é pública. Para obter mais informações, consulte [Manipulação de eventos WPF e do Visual Basic](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` é usado pelo processador de XAML WPF para registrar um nome em um namescope XAML no tempo de carregamento, mesmo em casos em que a página não é compilado por marcação por ações de build (por exemplo, XAML flexível de um dicionário de recursos). Um motivo para esse comportamento ocorre porque o `x:Name` potencialmente é necessário para <xref:System.Windows.Data.Binding.ElementName%2A> associação. Para obter detalhes, consulte [visão geral de associação de dados](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Conforme mencionado anteriormente, `x:Name` (ou `Name`) não deve ser aplicada em situações que também usam `x:Key`. O [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> tem um comportamento especial de definição em si como um namescope XAML, mas retornando não implementado ou valores nulos para <xref:System.Windows.Markup.INameScope> APIs como uma maneira de aplicar esse comportamento. Se o analisador de XAML WPF encontra `Name` ou `x:Name` em um XAML definido <xref:System.Windows.ResourceDictionary>, o nome não é adicionado a qualquer namescope XAML. Tentativa de encontrar esse nome de qualquer namescope XAML e o `FindName` métodos não retornará resultados válidos.  
  
### <a name="xname-and-name"></a>x: o nome e nome  
 Muitos cenários de aplicativo do WPF podem evitar o uso de qualquer os `x:Name` de atributo, pois o `Name` propriedade de dependência como especificado no padrão namespace XAML para várias das classes base importantes, como <xref:System.Windows.FrameworkElement> e <xref:System.Windows.FrameworkContentElement> atende a essa mesma finalidade. Ainda existem alguns cenários comuns de XAML e WPF em que o acesso a um elemento sem nenhum código `Name` propriedade no nível da estrutura é importante. Por exemplo, determinadas classes de suporte do storyboard e animação não dão suporte a um `Name` propriedade, mas eles geralmente precisam ser referenciados no código para controlar a animação. Você deve especificar `x:Name` como um atributo em cronogramas e transformações que são criadas no XAML, se você pretende referenciá-los no código.  
  
 Se <xref:System.Windows.FrameworkElement.Name%2A> está disponível como uma propriedade na classe, <xref:System.Windows.FrameworkElement.Name%2A> e `x:Name` podem ser usados alternadamente como atributos, mas uma exceção de análise ocorrerá se ambos forem especificados no mesmo elemento. Se o XAML é compilada com marcação, a exceção ocorrerá na compilação de marcação, caso contrário, ela ocorre na carga.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> pode ser definido usando a sintaxe de atributo XAML e no código usando <xref:System.Windows.DependencyObject.SetValue%2A>; no entanto, observe que a configuração de <xref:System.Windows.FrameworkElement.Name%2A> propriedade no código não cria a referência de campo representativa dentro do namescope XAML na maioria das circunstâncias em que o XAML já está carregado. Em vez de tentar definir <xref:System.Windows.FrameworkElement.Name%2A> no código, use <xref:System.Windows.NameScope> métodos de código, em relação ao namescope apropriado.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> também podem ser definidas usando a sintaxe de elemento de propriedade com o texto interno, mas que é incomum. Em contraste, `x:Name` não pode ser definida na sintaxe de elemento de propriedade XAML ou em código usando <xref:System.Windows.DependencyObject.SetValue%2A>; ele só pode ser definido usando a sintaxe de atributo em objetos porque ele é uma diretiva.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight  
 `x:Name` para o Silverlight está documentado separadamente. Para obter mais informações, consulte [Namespace de XAML (x) Recursos de linguagem (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Árvores no WPF](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
