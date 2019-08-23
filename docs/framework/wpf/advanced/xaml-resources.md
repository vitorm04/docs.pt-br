---
title: Recursos XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958814"
---
# <a name="xaml-resources"></a>Recursos XAML
Um recurso é um objeto que pode ser reutilizado em locais diferentes do aplicativo. Exemplos de recursos incluem pincéis e estilos. Esta visão geral descreve como usar recursos no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Você também pode criar e acessar recursos usando código ou de forma intercambiável entre código e [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Para obter mais informações, consulte [recursos e código](resources-and-code.md).  
  
> [!NOTE]
> Os arquivos de recursos descritos neste tópico são diferentes dos arquivos de recursos descritos no [recurso de aplicativo do WPF, conteúdo e arquivos de dados](../app-development/wpf-application-resource-content-and-data-files.md) e diferentes dos recursos incorporados ou vinculados descritos em [gerenciar recursos do aplicativo (.net) ](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Usando recursos no XAML  
 O exemplo a seguir define <xref:System.Windows.Media.SolidColorBrush> um como um recurso no elemento raiz de uma página. O exemplo faz referência ao recurso e o usa para definir as propriedades de vários elementos filho, incluindo <xref:System.Windows.Shapes.Ellipse>um, <xref:System.Windows.Controls.TextBlock>um e um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Cada elemento de nível de estrutura<xref:System.Windows.FrameworkElement> ( <xref:System.Windows.FrameworkContentElement>ou) tem <xref:System.Windows.FrameworkElement.Resources%2A> uma propriedade, que é a propriedade que contém os recursos (como <xref:System.Windows.ResourceDictionary>um) que um recurso define. Você pode definir recursos em qualquer elemento. No entanto, os recursos são definidos com mais frequência no elemento raiz <xref:System.Windows.Controls.Page> , que está no exemplo.  
  
 Cada recurso em um dicionário de recursos deve ter uma chave exclusiva. Ao definir recursos na marcação, você atribui a chave exclusiva por meio da [diretiva x:Key](../../xaml-services/x-key-directive.md). Normalmente, a chave é uma cadeia de caracteres; no entanto, você pode também a definir com outros tipos de objeto usando as extensões de marcação apropriadas. Chaves não cadeias de caracteres para recursos são usadas por determinadas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]áreas de recursos no, especialmente para estilos, recursos de componentes e estilo de dados.  
  
 Depois de definir um recurso, é possível referenciá-lo para ser usado em um valor da propriedade usando uma sintaxe de extensão de marcação de recursos que especifica o nome da chave, por exemplo:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 No exemplo anterior, quando o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] carregador processa o valor `{StaticResource MyBrush}` <xref:System.Windows.Controls.Control.Background%2A> da propriedade em <xref:System.Windows.Controls.Button>, a lógica de pesquisa de recurso primeiro verifica o dicionário de recursos para <xref:System.Windows.Controls.Button> o elemento. Se <xref:System.Windows.Controls.Button> não tiver uma definição da chave `MyBrush` de recurso (ela não; sua coleção de recursos está vazia), a pesquisa em seguida verificará o elemento pai <xref:System.Windows.Controls.Button>de, que <xref:System.Windows.Controls.Page>é. Portanto, quando você define um recurso no <xref:System.Windows.Controls.Page> elemento raiz, todos os elementos na árvore lógica <xref:System.Windows.Controls.Page> do podem acessá-lo e você pode reutilizar o mesmo recurso para definir o valor de qualquer propriedade que aceite o <xref:System.Type> recurso determina. No exemplo anterior, o mesmo `MyBrush` recurso define duas propriedades diferentes: o <xref:System.Windows.Controls.Control.Background%2A> de <xref:System.Windows.Controls.Button>a e o <xref:System.Windows.Shapes.Shape.Fill%2A> de <xref:System.Windows.Shapes.Rectangle>a.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Recursos estáticos e dinâmicos  
 Um recurso pode ser referenciado como um recurso estático ou dinâmico. Isso é feito usando a extensão de [marcação StaticResource](staticresource-markup-extension.md) ou a [extensão de marcação DynamicResource](dynamicresource-markup-extension.md). Uma extensão de marcação é um recurso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do qual você pode especificar uma referência de objeto fazendo com que a extensão de marcação processe a cadeia de caracteres de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributo e retorne o objeto a um carregador. Para obter mais informações sobre o comportamento de extensão de marcação, consulte [Markup Extensions e WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Ao usar uma extensão de marcação, normalmente, você fornece um ou mais parâmetros no formato de cadeia de caracteres que são processados por uma extensão de marcação específica, em vez de serem avaliados no contexto da propriedade que está sendo definida. A [extensão de marcação StaticResource](staticresource-markup-extension.md) processa uma chave procurando o valor dessa chave em todos os dicionários de recursos disponíveis. Isso ocorre durante o carregamento, o que é o ponto no tempo quando o processo de carregamento precisa atribuir o valor da propriedade que usa a referência de recursos estáticos. Em vez disso, a [extensão de marcação DynamicResource](dynamicresource-markup-extension.md) processa uma chave criando uma expressão, e essa expressão permanece não avaliada até que o aplicativo seja realmente executado, quando a expressão é avaliada e fornece um valor.  
  
 Quando você referencia um recurso, as seguintes considerações podem influenciar se uma referência de recurso estático ou dinâmico será usada:  
  
- O design geral de como você cria os recursos para seu aplicativo (por página, no aplicativo, em livre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], em um assembly de recurso somente).  
  
- A funcionalidade do aplicativo: a atualização de recursos em tempo real faz parte dos requisitos do aplicativo?  
  
- O respectivo comportamento de pesquisa desse tipo de referência de recurso.  
  
- A propriedade ou o tipo de recurso específico e o comportamento nativo desses tipos.  
  
### <a name="static-resources"></a>Recursos estáticos  
 As referências de recursos estáticos funcionam melhor nas seguintes circunstâncias:  
  
- O design do aplicativo concentra a maior parte de seus recursos em dicionários de recursos em nível de página ou de aplicativo. As referências de recursos estáticos não são reavaliadas de acordo com os comportamentos em tempo de execução, como o recarregamento de uma página e, portanto, pode haver alguma vantagem de desempenho em evitar um grande número de referências de recursos dinâmicos quando elas não são necessárias, conforme o design do aplicativo e dos recursos.  
  
- Você está definindo o valor de uma propriedade que não está em um <xref:System.Windows.DependencyObject> ou um <xref:System.Windows.Freezable>.  
  
- Você está criando um dicionário de recursos que será compilado em uma DLL e empacotado como parte do aplicativo ou compartilhado entre aplicativos.  
  
- Você está criando um tema para um controle personalizado e está definindo recursos que são usados nos temas. Nesse caso, normalmente, você não deseja ter o comportamento de pesquisa da referência de recursos dinâmicos; em vez disso, você deseja ter o comportamento da referência de recursos estáticos, de forma que a pesquisa seja previsível e independente para o tema. Com uma referência de recursos dinâmicos, até mesmo uma referência em um tema é deixada como não avaliada até o tempo de execução, e há a possibilidade de que quando o tema for aplicado, algum elemento local redefina uma chave que o tema está tentando referenciar e o elemento local falhe antes do próprio tema na pesquisa. Se isso acontecer, o tema não se comportará da maneira esperada.  
  
- Você está usando recursos para definir uma grande quantidade de propriedades de dependência. As propriedades de dependência têm um cache de valor efetivo habilitado pelo sistema de propriedades e, portanto, se você fornecer um valor para uma propriedade de dependência que pode ser avaliado em tempo de carregamento, a propriedade de dependência não precisará verificar uma expressão reavaliada e poderá retornar o último valor efetivo. Essa técnica pode ser uma vantagem de desempenho.  
  
- Você deseja alterar o recurso subjacente para todos os consumidores ou deseja manter instâncias graváveis separadas para cada consumidor usando o [atributo x:Shared](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Comportamento de pesquisa de recursos estáticos  
  
1. O processo de pesquisa verifica a chave solicitada no dicionário de recursos definido pelo elemento que define a propriedade.  
  
2. Em seguida, o processo de pesquisa percorre a árvore lógica de forma ascendente, até o elemento pai e seu dicionário de recursos. Isso continua até que o elemento raiz seja alcançado.  
  
3. Em seguida, os recursos do aplicativo são verificados. Os recursos do aplicativo são aqueles no dicionário de recursos que é definido pelo <xref:System.Windows.Application> objeto para seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.  
  
 As referências de recursos estáticos em um dicionário de recursos devem referenciar um recurso que já foi definido lexicalmente antes da referência ao recurso. As referências de encaminhamento não podem ser resolvidas por uma referência de recursos estáticos. Por esse motivo, se você usar referências de recursos estáticos, deverá projetar a estrutura do dicionário de recursos, de forma que os recursos destinados ao uso por recurso sejam definidos no início ou próximo do início de cada respectivo dicionário de recursos.  
  
 A pesquisa de recursos estáticos pode se estender a temas ou a recursos do sistema, mas só há [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] suporte para isso porque o carregador adia a solicitação. O adiamento é necessário para que o tema em tempo de execução no momento em que a página é carregada seja aplicado corretamente ao aplicativo. No entanto, referências de recursos estáticos a chaves que são conhecidas somente e existentes em temas ou como recursos do sistema não são recomendadas. Isso ocorre porque essas referências não são reavaliadas se o tema é alterado pelo usuário em tempo real. Uma referência de recurso dinâmico é mais confiável quando você solicita recursos do sistema ou de tema. A exceção é quando um próprio elemento de tema solicita outro recurso. Essas referências devem ser referências de recursos estáticos, pelas razões mencionadas anteriormente.  
  
 O comportamento de exceção se uma referência de recurso estático não é encontrada varia. Se o recurso foi adiado, a exceção ocorre em tempo de execução. Se o recurso não foi adiado, a exceção ocorre em tempo de carregamento.  
  
### <a name="dynamic-resources"></a>Recursos dinâmicos  
 Os recursos dinâmicos funcionam melhor nas seguintes circunstâncias:  
  
- O valor do recurso depende de condições que só são conhecidas em tempo de execução. Isso inclui recursos do sistema ou recursos que são, de outro modo, configuráveis pelo usuário. Por exemplo, você pode criar valores setter que se referem às propriedades do sistema, <xref:System.Windows.SystemColors>como <xref:System.Windows.SystemFonts>exposto por <xref:System.Windows.SystemParameters>, ou. Esses valores são realmente dinâmicos, pois, basicamente, são obtidos do ambiente em tempo de execução do usuário e do sistema operacional. Você também pode ter temas em nível do aplicativo que podem ser alterados, em que o acesso aos recursos em nível de página também deve captar a alteração.  
  
- Você está criando ou referenciando estilos de tema para um controle personalizado.  
  
- Você pretende ajustar o conteúdo de um <xref:System.Windows.ResourceDictionary> durante um tempo de vida do aplicativo.  
  
- Você tem uma estrutura de recursos complicada que tem interdependências, em que uma referência de encaminhamento pode ser necessária. As referências de recursos estáticos não dão suporte a referências de encaminhamento, mas as referências de recursos dinâmicos dão suporte a elas porque o recurso não precisa ser avaliado até o tempo de execução e as referências de encaminhamento não são, portanto, um conceito relevante.  
  
- Você está referenciando um recurso que é especificamente grande da perspectiva de um conjunto de compilação ou de trabalho, que pode não ser usado imediatamente quando a página é carregada. As referências de recursos estáticos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sempre são carregadas de quando a página é carregada; no entanto, uma referência de recurso dinâmico não é carregada até que seja realmente usada.  
  
- Você está criando um estilo no qual os valores setter podem ser obtidos de outros valores que são influenciados por temas ou por outras configurações do usuário.  
  
- Você está aplicando recursos a elementos que podem ser reassociados na árvore lógica durante o tempo de vida do aplicativo. Potencialmente, a alteração do pai também altera o escopo de pesquisa de recursos; portanto, se você desejar que o recurso de um elemento reassociado seja reavaliado com base no novo escopo, sempre use uma referência de recursos dinâmicos.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Comportamento de pesquisa de recursos dinâmicos  
 O comportamento de pesquisa de recurso para uma referência de recurso dinâmico paraleliza o comportamento de pesquisa em seu <xref:System.Windows.FrameworkElement.FindResource%2A> código <xref:System.Windows.FrameworkElement.SetResourceReference%2A>se você chamar ou.  
  
1. O processo de pesquisa verifica a chave solicitada no dicionário de recursos definido pelo elemento que define a propriedade.  
  
    - Se o elemento definir uma <xref:System.Windows.FrameworkElement.Style%2A> Propriedade, o <xref:System.Windows.Style.Resources%2A> dicionário dentro do <xref:System.Windows.Style> será verificado.  
  
    - Se o elemento definir uma <xref:System.Windows.Controls.Control.Template%2A> Propriedade, o <xref:System.Windows.FrameworkTemplate.Resources%2A> dicionário dentro do <xref:System.Windows.FrameworkTemplate> será verificado.  
  
2. Em seguida, o processo de pesquisa percorre a árvore lógica de forma ascendente, até o elemento pai e seu dicionário de recursos. Isso continua até que o elemento raiz seja alcançado.  
  
3. Em seguida, os recursos do aplicativo são verificados. Os recursos do aplicativo são aqueles no dicionário de recursos que é definido pelo <xref:System.Windows.Application> objeto para seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.  
  
4. O dicionário de recursos de tema é verificado quanto ao tema ativo no momento. Se o tema for alterado em tempo de execução, o valor será reavaliado.  
  
5. Os recursos do sistema são verificados.  
  
 O comportamento de exceção (se houver) varia:  
  
- Se um recurso foi solicitado por uma <xref:System.Windows.FrameworkElement.FindResource%2A> chamada e não foi encontrado, uma exceção será gerada.  
  
- Se um recurso foi solicitado por uma <xref:System.Windows.FrameworkElement.TryFindResource%2A> chamada e não foi encontrado, nenhuma exceção é gerada, mas o valor retornado é. `null` Se a propriedade que está sendo definida não `null`aceitar, ainda é possível que uma exceção mais profunda seja gerada (isso depende da propriedade individual que está sendo definida).  
  
- Se um recurso foi solicitado por uma referência de recurso dinâmico [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]no e não foi encontrado, o comportamento depende do sistema de propriedades geral, mas o comportamento geral é como se nenhuma operação de configuração de propriedade ocorreu no nível em que o recurso existe. Por exemplo, se você tentar definir a tela de fundo em um elemento de botão individual usando um recurso que não pôde ser avaliado, nenhum conjunto de valores resultará, mas o valor efetivo ainda poderá ser obtido de outros participantes do sistema de propriedades e da precedência de valor. Por exemplo, o valor de tela de fundo ainda poderá ser obtido de um estilo de botão definido localmente ou do estilo de tema. Para propriedades que não são definidas por estilos de tema, o valor efetivo após uma avaliação de recurso com falha pode ser obtido do valor padrão nos metadados da propriedade.  
  
#### <a name="restrictions"></a>Restrições  
 As referências de recursos dinâmicos têm algumas restrições importantes. Pelo menos, uma das seguintes condições deve ser verdadeira:  
  
- A propriedade que está sendo definida deve ser uma propriedade <xref:System.Windows.FrameworkElement> em <xref:System.Windows.FrameworkContentElement>um ou. Essa propriedade deve ser apoiada por um <xref:System.Windows.DependencyProperty>.  
  
- A referência é para um valor dentro de <xref:System.Windows.Style>um <xref:System.Windows.Setter>.  
  
- A propriedade que está sendo definida deve ser uma propriedade <xref:System.Windows.Freezable> em um que é fornecida como um valor de <xref:System.Windows.FrameworkElement> uma <xref:System.Windows.FrameworkContentElement> propriedade ou, ou <xref:System.Windows.Setter> um valor.  
  
 Como a propriedade que está sendo definida deve <xref:System.Windows.DependencyProperty> ser <xref:System.Windows.Freezable> uma propriedade ou, a maioria das alterações de propriedade pode ser propagada para a interface do usuário porque uma alteração de propriedade (o valor de recurso dinâmico alterado) é confirmada pelo sistema de propriedades. A maioria dos controles inclui lógica que forçará outro layout de um controle <xref:System.Windows.DependencyProperty> se uma alteração e essa propriedade puderem afetar o layout. No entanto, nem todas as propriedades que têm uma [extensão de marcação DynamicResource](dynamicresource-markup-extension.md) como seu valor têm garantia de fornecer o valor de tal forma que elas sejam atualizadas em tempo real na interface do usuário. Essa funcionalidade ainda pode variar dependendo da propriedade, bem como do tipo que possui a propriedade, ou até mesmo da estrutura lógica do aplicativo.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Estilos, DataTemplates e chaves implícitas  
 Anteriormente, foi mencionado que todos os itens em um <xref:System.Windows.ResourceDictionary> devem ter uma chave. No entanto, isso não significa que todos os recursos devem ter `x:Key`um explícito. Vários tipos de objeto dão suporte a uma chave implícita quando definidos como um recurso, em que o valor da chave é vinculado ao valor de outra propriedade. Isso é conhecido como uma chave implícita, enquanto que `x:Key` um atributo é uma chave explícita. Você pode substituir uma chave implícita especificando uma chave explícita.  
  
 Um cenário muito importante para os recursos é quando você define <xref:System.Windows.Style>um. Na verdade, um <xref:System.Windows.Style> é quase sempre definido como uma entrada em um dicionário de recursos, porque os estilos são inerentemente destinados à reutilização. Para obter mais informações sobre estilos, consulte [estilização e modelagem](../controls/styling-and-templating.md).  
  
 Os estilos de controles podem ser criados com uma chave implícita e referenciados com ela. Os estilos de tema que definem a aparência padrão de um controle se baseiam nessa chave implícita. A chave implícita do ponto de vista da solicitação é o <xref:System.Type> do próprio controle. A chave implícita do ponto de vista da definição do recurso é <xref:System.Windows.Style.TargetType%2A> o do estilo. Portanto, se você estiver criando temas para controles personalizados, criando estilos que interagem com estilos de tema existentes, não será necessário especificar uma [diretiva x:Key](../../xaml-services/x-key-directive.md) para isso <xref:System.Windows.Style>. Além disso, você desejar usar os estilos de tema, não precisará especificar nenhum estilo. Por exemplo, a definição de estilo a seguir funciona, embora <xref:System.Windows.Style> o recurso não pareça ter uma chave:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Esse estilo realmente tem uma chave: a chave `typeof(` <xref:System.Windows.Controls.Button> `)`implícita. Na marcação, você pode especificar um <xref:System.Windows.Style.TargetType%2A> diretamente como o nome do tipo (ou opcionalmente, você pode usar [{x:Type...}](../../xaml-services/x-type-markup-extension.md) para retornar um <xref:System.Type>.  
  
 Por meio [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dos mecanismos de estilo <xref:System.Windows.Controls.Button> de tema padrão usados pelo, esse estilo é aplicado como o estilo de tempo de execução de a na <xref:System.Windows.Controls.Button> página, mesmo que a si não <xref:System.Windows.FrameworkElement.Style%2A> tente especificar sua propriedade ou um recurso específico referência ao estilo. Seu estilo definido na página é encontrado anteriormente na sequência de pesquisa do que o estilo de dicionário do tema, usando a mesma chave que o estilo do dicionário do tema. Você poderia apenas especificar `<Button>Hello</Button>` qualquer lugar na página, e o estilo que você <xref:System.Windows.Style.TargetType%2A> definiu `Button` a ser aplicado a esse botão. Se desejar, você ainda pode explicitamente chavear o estilo com o mesmo valor de tipo <xref:System.Windows.Style.TargetType%2A>que, para maior clareza na sua marcação, mas isso é opcional.  
  
 As chaves implícitas para estilos não se aplicam a <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> um `true` controle se for ( <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> Observe também que pode ser definida como parte do comportamento nativo da classe Control, em vez de explicitamente em uma instância do controle). Além disso, para dar suporte a chaves implícitas para cenários de classe derivada, o <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> controle deve substituir (todos os controles existentes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornecidos como parte de fazer isso). Para obter mais informações sobre estilos, temas e design de controle, consulte [diretrizes para criar controles stylable](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate>também tem uma chave implícita. A chave implícita para um <xref:System.Windows.DataTemplate> é o <xref:System.Windows.DataTemplate.DataType%2A> valor da propriedade. <xref:System.Windows.DataTemplate.DataType%2A>também pode ser especificado como o nome do tipo em vez de explicitamente usar [{x:Type...}](../../xaml-services/x-type-markup-extension.md). Para obter detalhes, consulte [visão geral de modelagem de dados](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.ResourceDictionary>
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Recursos e código](resources-and-code.md)
- [Definir e referenciar um recurso](how-to-define-and-reference-a-resource.md)
- [Visão geral do gerenciamento de aplicativos](../app-development/application-management-overview.md)
- [Extensão de marcação x:Type](../../xaml-services/x-type-markup-extension.md)
- [Extensão de marcação StaticResource](staticresource-markup-extension.md)
- [Extensão de marcação DynamicResource](dynamicresource-markup-extension.md)
