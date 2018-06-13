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
ms.openlocfilehash: 7fcb7fe767e892109e48c5e56db26b5943b6ef13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565844"
---
# <a name="xname-directive"></a>Diretiva x:Name
Identifica os elementos definidos em XAML em um namescope XAML. Namescopes XAML e seus modelos de exclusividade podem ser aplicados a objetos instanciados, quando estruturas fornecem APIs ou implementam comportamentos que acessam o gráfico de objeto criado XAML em tempo de execução.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Uma cadeia de caracteres que está de acordo com as restrições do [gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## <a name="remarks"></a>Comentários  
 Depois de `x:Name` é aplicado a uma estrutura do fazendo o modelo de programação, o nome é equivalente à variável que contém uma referência de objeto ou uma instância como retornado por um construtor.  
  
 O valor de um `x:Name` diretiva uso deve ser exclusivo dentro de um namescope XAML. Por padrão quando usado pela API de serviços de XAML do .NET Framework, o namescope XAML primário é definido no elemento raiz XAML de um único produção XAML e abrange os elementos que estão contidos em produção que XAML. Discreto namescopes XAML adicionais que podem ocorrer dentro de um único XAML de produção podem ser definidos por estruturas para cenários específicos de endereço. Por exemplo, no WPF, novo namescopes XAML são definidos e criados por qualquer modelo que também esteja definido em produção que XAML. Para obter mais informações sobre namescopes XAML (gravado para WPF mas relevante para muitos conceitos de namescope XAML), consulte [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Em geral, `x:Name` não deve ser aplicada em situações que também usam `x:Key`. Implementações de XAML por estruturas existentes específicas introduziram conceitos de substituição entre `x:Key` e `x:Name`, mas que não é uma prática recomendada. Serviços XAML do .NET framework não dá suporte a esses conceitos de substituição ao lidar com informações de chave de nome/como <xref:System.Windows.Markup.INameScope> ou <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Regras para a permissão de `x:Name` , bem como a imposição de exclusividade de nome potencialmente são definidos pela implementação de estruturas específicas. No entanto, para ser usado com serviços XAML do .NET Framework, as definições do framework de exclusividade de namescope XAML devem ser consistentes com a definição de <xref:System.Windows.Markup.INameScope> informações contidas nesta documentação e deve usar as mesmas regras referentes ao local a as informações são aplicadas. Por exemplo, o [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementação divide vários elementos de marcação em separado <xref:System.Windows.NameScope> intervalos, como dicionários de recursos, a árvore lógica, o nível de página XAML, modelos e outros adiada conteúda criada e, em seguida, aplica XAML exclusividade de nome dentro de cada um desses namescopes XAML.  
  
 Para tipos personalizados que usam os gravadores de objeto do .NET Framework XAML serviços XAML, uma propriedade que ela mapeia para `x:Name` em um tipo pode ser estabelecido ou alterado. Definir esse comportamento referenciando o nome da propriedade a ser mapeada com a <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> no código de definição de tipo.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> é um atributo de tipo de nível.  
  
 Serviços XAML do Framework Using.NET, a lógica de backup para suporte de namescope XAML pode ser definidos em uma maneira neutra no framework Implementando o <xref:System.Windows.Markup.INameScope> interface.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Sob a configuração de compilação padrão para um [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplicativo que usa XAML, classes parciais e code-behind, especificado `x:Name` se torna o nome de um campo que é criado na Base de código quando [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é processada por uma marcação tarefa de compilação de compilação e esse campo contém uma referência ao objeto. Por padrão, o campo criado é interno. Você pode alterar o acesso ao campo especificando o [atributo X:FieldModifier](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md). No WPF e no Silverlight, a sequência é que a compilação da marcação define e nomes de campo em uma classe parcial, mas o valor é inicialmente vazio. Em seguida, um método gerado chamado `InitializeComponent` é chamado de dentro do construtor de classe. `InitializeComponent` consiste em `FindName` chama usando todos os `x:Name` cadeias de caracteres de entrada de valores que existem na parte da classe parcial, conforme definido em XAML. Os valores de retorno são atribuídos à referência de campo de nome semelhante para preencher os valores de campo com objetos que foram criados a partir XAML análise. A execução de `InitializeComponent` possibilitam a referência para o gráfico de objeto de tempo de execução usando o `x:Name` / nome do campo diretamente, em vez de precisar chamar `FindName` explicitamente a qualquer momento você precisa de uma referência a um objeto definido em XAML.  
  
 Para um WPF o aplicativo que usa o Microsoft Visual Basic tem como alvo e inclui os arquivos XAML com `Page` ação de compilação, uma propriedade de referência separada é criada durante a compilação que adiciona o `WithEvents` palavra-chave para todos os elementos que têm um `x:Name`, para dar suporte a `Handles` sintaxe para delegados de manipulador de eventos. Esta propriedade é sempre pública. Para obter mais informações, consulte [Manipulação de eventos WPF e do Visual Basic](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` é usado pelo processador de WPF XAML para registrar um nome em um namescope XAML no tempo de carregamento, mesmo em casos em que a página não está compilado marcação pelas ações de compilação (por exemplo, XAML flexível de um dicionário de recursos). Um motivo para esse comportamento ocorre porque o `x:Name` é potencialmente necessário para <xref:System.Windows.Data.Binding.ElementName%2A> associação. Para obter detalhes, consulte [visão geral de associação de dados](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Conforme mencionado anteriormente, `x:Name` (ou `Name`) não deve ser aplicada em situações que também usam `x:Key`. O [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> tem um comportamento especial de definindo-se como um namescope XAML mas retornando não implementado ou valores nulos para <xref:System.Windows.Markup.INameScope> APIs, como uma forma de impor esse comportamento. Se o analisador do WPF XAML encontra `Name` ou `x:Name` em um XAML definido <xref:System.Windows.ResourceDictionary>, o nome não é adicionado a qualquer namescope XAML. A tentativa de encontrar esse nome de qualquer namescope XAML e o `FindName` métodos não retornará resultados válidos.  
  
### <a name="xname-and-name"></a>x: nome e o nome  
 Muitos cenários de aplicativo do WPF podem evitar qualquer uso do `x:Name` de atributo, pois o `Name` DependencyProperty como especificado no padrão do namespace XAML para várias das classes-base importantes como <xref:System.Windows.FrameworkElement> e <xref:System.Windows.FrameworkContentElement> de acordo com esse mesmo propósito. Ainda existem alguns cenários comuns de XAML e WPF código onde o acesso a um elemento sem nenhum `Name` propriedade no nível do framework é importante. Por exemplo, algumas classes de suporte de storyboard e animação não oferecem suporte a um `Name` propriedade, mas eles geralmente precisam ser referenciada no código para controlar a animação. Você deve especificar `x:Name` como um atributo em cronogramas em transformações que são criadas em XAML, se você pretende referenciá-las do código.  
  
 Se <xref:System.Windows.FrameworkElement.Name%2A> está disponível como uma propriedade na classe, <xref:System.Windows.FrameworkElement.Name%2A> e `x:Name` podem ser usados alternadamente como atributos, mas uma exceção de análise ocorrerá se ambas forem especificadas no mesmo elemento. Se o XAML é compilada com marcação, a exceção ocorrerá na compilação de marcação, caso contrário, ocorre na carga.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> pode ser definido usando a sintaxe do atributo XAML e no código usando <xref:System.Windows.DependencyObject.SetValue%2A>; no entanto observe essa configuração o <xref:System.Windows.FrameworkElement.Name%2A> propriedade em código não cria a referência de campo representativa dentro do namescope XAML na maioria das circunstâncias em que o XAML já está carregado. Em vez de uma tentativa de definir <xref:System.Windows.FrameworkElement.Name%2A> no código, use <xref:System.Windows.NameScope> métodos de código, em relação ao namescope apropriado.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> também pode ser definido usando a sintaxe de elemento de propriedade com o texto interno, mas isso é raro. Por outro lado, `x:Name` não pode ser definida na sintaxe de elemento de propriedade XAML, ou em código usando <xref:System.Windows.DependencyObject.SetValue%2A>; ele só pode ser definido usando a sintaxe do atributo nos objetos porque é uma diretiva.  
  
## <a name="silverlight-usage-notes"></a>Observações de uso do Silverlight  
 `x:Name` para o Silverlight é documentado separadamente. Para obter mais informações, consulte [Namespace XAML (x) Recursos de linguagem (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [Árvores no WPF](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
