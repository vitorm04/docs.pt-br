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
ms.openlocfilehash: 8a790ea964ffe399136a82ea298e1c7600f48366
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459969"
---
# <a name="xname-directive"></a>Diretiva x:Name
Identifica exclusivamente elementos definidos pelo XAML em um namescope XAML. Os namescopes XAML e seus modelos de exclusividade podem ser aplicados aos objetos instanciados, quando as estruturas fornecem APIs ou implementam comportamentos que acessam o grafo de objeto criado XAML em tempo de execução.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Uma cadeia de caracteres que está de acordo com as restrições da [Gramática XamlName](xamlname-grammar.md).|  
  
## <a name="remarks"></a>Comentários  
 Depois que `x:Name` é aplicado ao modelo de programação de suporte de uma estrutura, o nome é equivalente à variável que mantém uma referência de objeto ou uma instância como retornada por um construtor.  
  
 O valor de um `x:Name` uso da diretiva deve ser exclusivo dentro de um namescope XAML. Por padrão, quando usado por .NET Framework API de serviços XAML, o namescope XAML primário é definido no elemento raiz XAML de uma única produção XAML e abrange os elementos contidos nessa produção XAML. Os namescopes XAML discretos adicionais que podem ocorrer em uma única produção XAML podem ser definidos por estruturas para tratar de cenários específicos. Por exemplo, no WPF, novos namescopes XAML são definidos e criados por qualquer modelo que também esteja definido nessa produção XAML. Para obter mais informações sobre namescopes XAML (escritos para WPF, mas relevantes para muitos conceitos de namescope XAML), consulte [namescopes XAML do WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Em geral, `x:Name` não deve ser aplicado em situações que também usam `x:Key`. As implementações de XAML por estruturas existentes específicas introduziram conceitos de substituição entre `x:Key` e `x:Name`, mas essa não é uma prática recomendada. .NET Framework serviços XAML não oferece suporte a esses conceitos de substituição ao manipular informações de nome/chave, como <xref:System.Windows.Markup.INameScope> ou <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 As regras para a permissão de `x:Name`, bem como a imposição de exclusividade de nome, são potencialmente definidas por estruturas de implementação específicas. No entanto, para ser utilizável com .NET Framework serviços XAML, as definições de estrutura da exclusividade do namescope do XAML devem ser consistentes com a definição de informações de <xref:System.Windows.Markup.INameScope> nesta documentação e devem usar as mesmas regras sobre onde as informações é aplicado. Por exemplo, a implementação de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] divide vários elementos de marcação em intervalos de <xref:System.Windows.NameScope> separados, como dicionários de recursos, a árvore lógica criada pelo XAML no nível da página, modelos e outros conteúdos adiados e, em seguida, impõe o nome XAML exclusividade dentro de cada um dos namescopes XAML.  
  
 Para tipos personalizados que usam .NET Framework gravadores de objeto XAML dos serviços XAML, uma propriedade que é mapeada para `x:Name` em um tipo pode ser estabelecida ou alterada. Você define esse comportamento referenciando o nome da propriedade a ser mapeada com o <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> no código de definição de tipo.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> é um atributo de nível de tipo.  
  
 Os serviços XAML do Using.NET Framework, a lógica de apoio do suporte ao namescope do XAML, pode ser definida de forma neutra com a estrutura implementando a interface <xref:System.Windows.Markup.INameScope>.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Na configuração de Build padrão para um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] que usa XAML, classes parciais e code-behind, o `x:Name` especificado se torna o nome de um campo que é criado no código subjacente quando [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é processado por uma compilação de compilação de marcação e esse campo contém uma referência ao objeto. Por padrão, o campo criado é interno. Você pode alterar o acesso ao campo especificando o [atributo x:FieldModifier](x-fieldmodifier-directive.md). No WPF e no Silverlight, a sequência é que a compilação de marcação define e nomeia o campo em uma classe parcial, mas o valor está inicialmente vazio. Em seguida, um método gerado chamado `InitializeComponent` é chamado de dentro do construtor da classe. `InitializeComponent` consiste em chamadas de `FindName` usando cada um dos valores de `x:Name` que existem na parte do XAML definida da classe parcial como cadeias de caracteres de entrada. Os valores de retorno são então atribuídos à referência de campo com nome semelhante para preencher os valores de campo com objetos que foram criados a partir da análise XAML. A execução de `InitializeComponent` torna possível referenciar o grafo de objeto de tempo de execução usando o nome de `x:Name`/campo diretamente, em vez de precisar chamar `FindName` explicitamente sempre que você precisar de uma referência a um objeto definido por XAML.  
  
 Para um aplicativo WPF que usa o Microsoft Visual Basic targets e inclui arquivos XAML com `Page` ação de Build, uma propriedade de referência separada é criada durante a compilação que adiciona a palavra-chave `WithEvents` a todos os elementos que têm um `x:Name`, para dar suporte a @no sintaxe de __t_3_ para delegados de manipulador de eventos. Essa propriedade é sempre pública. Para obter mais informações, consulte [Manipulação de eventos WPF e do Visual Basic](../wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` é usado pelo processador XAML WPF para registrar um nome em um namescope XAML no tempo de carregamento, mesmo para casos em que a página não é compilada pela marcação por ações de compilação (por exemplo, XAML flexível de um dicionário de recursos). Um motivo para esse comportamento é porque o `x:Name` é potencialmente necessário para <xref:System.Windows.Data.Binding.ElementName%2A> associação. Para obter detalhes, consulte [visão geral da ligação de dados](../../desktop-wpf/data/data-binding-overview.md).  
  
 Conforme mencionado anteriormente, `x:Name` (ou `Name`) não deve ser aplicado em situações que também usam `x:Key`. A [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> tem um comportamento especial de definir a si mesma como um namescope XAML, mas retornando valores não implementados ou nulos para APIs de <xref:System.Windows.Markup.INameScope> como uma maneira de impor esse comportamento. Se o analisador XAML do WPF encontrar `Name` ou `x:Name` em um <xref:System.Windows.ResourceDictionary>definido por XAML, o nome não será adicionado a nenhum namescope XAML. Tentar encontrar esse nome a partir de qualquer namescope XAML e os métodos `FindName` não retornarão resultados válidos.  
  
### <a name="xname-and-name"></a>x:Name e Name  
 Muitos cenários de aplicativos do WPF podem evitar qualquer uso do atributo `x:Name`, porque a propriedade de dependência `Name` conforme especificado no namespace XAML padrão para várias das classes base importantes, como <xref:System.Windows.FrameworkElement> e <xref:System.Windows.FrameworkContentElement>, atende a essa mesma finalidade. Ainda há alguns cenários comuns de XAML e WPF em que o acesso ao código para um elemento sem nenhuma propriedade `Name` no nível da estrutura é importante. Por exemplo, determinadas classes de suporte a animação e Storyboard não dão suporte a uma propriedade `Name`, mas geralmente precisam ser referenciadas no código para controlar a animação. Você deve especificar `x:Name` como um atributo em cronogramas e transformações que são criados em XAML, se você pretende fazer referência a eles a partir do código posteriormente.  
  
 Se <xref:System.Windows.FrameworkElement.Name%2A> estiver disponível como uma propriedade na classe, <xref:System.Windows.FrameworkElement.Name%2A> e `x:Name` poderão ser usados de maneira intercambiável como atributos, mas uma exceção de análise resultará se ambos forem especificados no mesmo elemento. Se o XAML for uma marcação compilada, a exceção ocorrerá na compilação da marcação, caso contrário, ocorrerá na carga.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> pode ser definido usando a sintaxe do atributo XAML e no código usando <xref:System.Windows.DependencyObject.SetValue%2A>; no entanto, observe que definir a propriedade <xref:System.Windows.FrameworkElement.Name%2A> no código não cria a referência de campo representativa dentro do namescope XAML na maioria das circunstâncias em que o XAML já está carregado. Em vez de tentar definir <xref:System.Windows.FrameworkElement.Name%2A> no código, use <xref:System.Windows.NameScope> métodos do código, em relação ao namescope apropriado.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> também pode ser definida usando a sintaxe do elemento de propriedade com texto interno, mas isso não é comum. Por outro lado, `x:Name` não pode ser definida na sintaxe do elemento da propriedade XAML ou no código usando <xref:System.Windows.DependencyObject.SetValue%2A>; Ele só pode ser definido usando a sintaxe de atributo em objetos porque é uma diretiva.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight  
 o `x:Name` para Silverlight é documentado separadamente. Para obter mais informações, consulte [XAML namespace (x:) Recursos de linguagem (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Árvores no WPF](../wpf/advanced/trees-in-wpf.md)
