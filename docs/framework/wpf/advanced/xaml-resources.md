---
title: Recursos XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: f5d6ae2d21058e7e6dd9fa9736800237082766d1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364743"
---
# <a name="xaml-resources"></a>Recursos XAML
Um recurso é um objeto que pode ser reutilizado em locais diferentes do aplicativo. Exemplos de recursos incluem pincéis e estilos. Esta visão geral descreve como usar recursos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Você também pode criar e acessar recursos por meio de código ou de forma intercambiável entre o código e [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Para obter mais informações, consulte [recursos e código](resources-and-code.md).  
  
> [!NOTE]
>  Os arquivos de recurso descritos neste tópico são diferentes do que os arquivos de recurso descrito em [recurso de aplicativo do WPF, conteúdo e arquivos de dados](../app-development/wpf-application-resource-content-and-data-files.md) e diferentes dos recursos inseridos ou vinculados descritos [gerenciar Recursos de aplicativo (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Usando recursos no XAML  
 O exemplo a seguir define uma <xref:System.Windows.Media.SolidColorBrush> como um recurso no elemento raiz de uma página. O exemplo, em seguida, faz referência ao recurso e o usa para definir as propriedades de vários elementos filho, incluindo uma <xref:System.Windows.Shapes.Ellipse>, um <xref:System.Windows.Controls.TextBlock>e um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Cada elemento de nível de estrutura (<xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>) tem um <xref:System.Windows.FrameworkElement.Resources%2A> propriedade, que é a propriedade que contém os recursos (como um <xref:System.Windows.ResourceDictionary>) que define um recurso. Você pode definir recursos em qualquer elemento. No entanto, os recursos com mais frequência são definidos no elemento raiz, que é <xref:System.Windows.Controls.Page> no exemplo.  
  
 Cada recurso em um dicionário de recursos deve ter uma chave exclusiva. Quando você define recursos em marcação, atribua a chave exclusiva por meio de [X:Key](../../xaml-services/x-key-directive.md). Normalmente, a chave é uma cadeia de caracteres; no entanto, você pode também a definir com outros tipos de objeto usando as extensões de marcação apropriadas. Chaves não cadeia de caracteres para recursos que são usadas por determinadas áreas de recurso no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especialmente em estilos, recursos de componente e estilos de dados.  
  
 Depois de definir um recurso, é possível referenciá-lo para ser usado em um valor da propriedade usando uma sintaxe de extensão de marcação de recursos que especifica o nome da chave, por exemplo:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 No exemplo anterior, quando o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] carregador processa o valor `{StaticResource MyBrush}` para o <xref:System.Windows.Controls.Control.Background%2A> propriedade <xref:System.Windows.Controls.Button>, a lógica de pesquisa de recursos primeiro verifica o dicionário de recursos para o <xref:System.Windows.Controls.Button> elemento. Se <xref:System.Windows.Controls.Button> não tem uma definição da chave de recurso `MyBrush` (isso não acontecer; sua coleção de recursos está vazia), a pesquisa então verificará o elemento pai do <xref:System.Windows.Controls.Button>, que é <xref:System.Windows.Controls.Page>. Assim, quando você define um recurso nas <xref:System.Windows.Controls.Page> elemento raiz, todos os elementos na árvore lógica do <xref:System.Windows.Controls.Page> possa acessá-lo, e você pode reutilizar o mesmo recurso para definir o valor de qualquer propriedade que aceita o <xref:System.Type> que o recurso representa. No exemplo anterior, o mesmo `MyBrush` recurso define duas propriedades diferentes: o <xref:System.Windows.Controls.Control.Background%2A> de uma <xref:System.Windows.Controls.Button>e o <xref:System.Windows.Shapes.Shape.Fill%2A> de um <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Recursos estáticos e dinâmicos  
 Um recurso pode ser referenciado como um recurso estático ou dinâmico. Isso é feito usando o [extensão de marcação StaticResource](staticresource-markup-extension.md) ou o [extensão de marcação DynamicResource](dynamicresource-markup-extension.md). Uma extensão de marcação é um recurso do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] por meio da qual você pode especificar uma referência de objeto fazendo com que a extensão de marcação processe a cadeia de caracteres de atributo e retorne o objeto a ser um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] carregador. Para obter mais informações sobre o comportamento de extensão de marcação, consulte [extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Ao usar uma extensão de marcação, normalmente, você fornece um ou mais parâmetros no formato de cadeia de caracteres que são processados por uma extensão de marcação específica, em vez de serem avaliados no contexto da propriedade que está sendo definida. O [extensão de marcação StaticResource](staticresource-markup-extension.md) processa uma chave pesquisando o valor para essa chave em todos os dicionários de recursos disponíveis. Isso ocorre durante o carregamento, o que é o ponto no tempo quando o processo de carregamento precisa atribuir o valor da propriedade que usa a referência de recursos estáticos. O [extensão de marcação DynamicResource](dynamicresource-markup-extension.md) em vez disso, os processos de uma chave com a criação de uma expressão e essa expressão permanece não avaliada até que o aplicativo é executado, na verdade, momento em que a expressão é avaliada e fornece um valor.  
  
 Quando você referencia um recurso, as seguintes considerações podem influenciar se uma referência de recurso estático ou dinâmico será usada:  
  
-   O design geral de como criar os recursos para seu aplicativo (por página, no aplicativo, soltos no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], em um assembly somente de recurso).  
  
-   A funcionalidade do aplicativo: a atualização de recursos em tempo real faz parte dos requisitos do aplicativo?  
  
-   O respectivo comportamento de pesquisa desse tipo de referência de recurso.  
  
-   A propriedade ou o tipo de recurso específico e o comportamento nativo desses tipos.  
  
### <a name="static-resources"></a>Recursos estáticos  
 As referências de recursos estáticos funcionam melhor nas seguintes circunstâncias:  
  
-   O design do aplicativo concentra a maior parte de seus recursos em dicionários de recursos em nível de página ou de aplicativo. As referências de recursos estáticos não são reavaliadas de acordo com os comportamentos em tempo de execução, como o recarregamento de uma página e, portanto, pode haver alguma vantagem de desempenho em evitar um grande número de referências de recursos dinâmicos quando elas não são necessárias, conforme o design do aplicativo e dos recursos.  
  
-   Você está definindo o valor de uma propriedade que não está em um <xref:System.Windows.DependencyObject> ou um <xref:System.Windows.Freezable>.  
  
-   Você está criando um dicionário de recursos que será compilado em uma DLL e empacotado como parte do aplicativo ou compartilhado entre aplicativos.  
  
-   Você está criando um tema para um controle personalizado e está definindo recursos que são usados nos temas. Nesse caso, normalmente, você não deseja ter o comportamento de pesquisa da referência de recursos dinâmicos; em vez disso, você deseja ter o comportamento da referência de recursos estáticos, de forma que a pesquisa seja previsível e independente para o tema. Com uma referência de recursos dinâmicos, até mesmo uma referência em um tema é deixada como não avaliada até o tempo de execução, e há a possibilidade de que quando o tema for aplicado, algum elemento local redefina uma chave que o tema está tentando referenciar e o elemento local falhe antes do próprio tema na pesquisa. Se isso acontecer, o tema não se comportará da maneira esperada.  
  
-   Você está usando recursos para definir uma grande quantidade de propriedades de dependência. As propriedades de dependência têm um cache de valor efetivo habilitado pelo sistema de propriedades e, portanto, se você fornecer um valor para uma propriedade de dependência que pode ser avaliado em tempo de carregamento, a propriedade de dependência não precisará verificar uma expressão reavaliada e poderá retornar o último valor efetivo. Essa técnica pode ser uma vantagem de desempenho.  
  
-   Para alterar o recurso subjacente para todos os consumidores ou deseja manter instâncias graváveis separadas para cada consumidor usando o [x: atributo X:Shared](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Comportamento de pesquisa de recursos estáticos  
  
1.  O processo de pesquisa verifica a chave solicitada no dicionário de recursos definido pelo elemento que define a propriedade.  
  
2.  Em seguida, o processo de pesquisa percorre a árvore lógica de forma ascendente, até o elemento pai e seu dicionário de recursos. Isso continua até que o elemento raiz seja alcançado.  
  
3.  Em seguida, os recursos do aplicativo são verificados. Recursos de aplicativo são aqueles recursos dentro do dicionário de recursos definido pelos <xref:System.Windows.Application> do objeto para sua [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.  
  
 As referências de recursos estáticos em um dicionário de recursos devem referenciar um recurso que já foi definido lexicalmente antes da referência ao recurso. As referências de encaminhamento não podem ser resolvidas por uma referência de recursos estáticos. Por esse motivo, se você usar referências de recursos estáticos, deverá projetar a estrutura do dicionário de recursos, de forma que os recursos destinados ao uso por recurso sejam definidos no início ou próximo do início de cada respectivo dicionário de recursos.  
  
 Pesquisa de recursos estáticos pode se estender a temas, ou a recursos do sistema, mas isso é suportado apenas porque o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] carregador adia a solicitação. O adiamento é necessário para que o tema em tempo de execução no momento em que a página é carregada seja aplicado corretamente ao aplicativo. No entanto, referências de recursos estáticos a chaves que são conhecidas somente e existentes em temas ou como recursos do sistema não são recomendadas. Isso ocorre porque essas referências não são reavaliadas se o tema é alterado pelo usuário em tempo real. Uma referência de recurso dinâmico é mais confiável quando você solicita recursos do sistema ou de tema. A exceção é quando um próprio elemento de tema solicita outro recurso. Essas referências devem ser referências de recursos estáticos, pelas razões mencionadas anteriormente.  
  
 O comportamento de exceção se uma referência de recurso estático não é encontrada varia. Se o recurso foi adiado, a exceção ocorre em tempo de execução. Se o recurso não foi adiado, a exceção ocorre em tempo de carregamento.  
  
### <a name="dynamic-resources"></a>Recursos dinâmicos  
 Os recursos dinâmicos funcionam melhor nas seguintes circunstâncias:  
  
-   O valor do recurso depende de condições que só são conhecidas em tempo de execução. Isso inclui recursos do sistema ou recursos que são, de outro modo, configuráveis pelo usuário. Por exemplo, você pode criar valores setter que fazem referência às propriedades do sistema, como expostos por <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, ou <xref:System.Windows.SystemParameters>. Esses valores são realmente dinâmicos, pois, basicamente, são obtidos do ambiente em tempo de execução do usuário e do sistema operacional. Você também pode ter temas em nível do aplicativo que podem ser alterados, em que o acesso aos recursos em nível de página também deve captar a alteração.  
  
-   Você está criando ou referenciando estilos de tema para um controle personalizado.  
  
-   Você pretende ajustar o conteúdo de um <xref:System.Windows.ResourceDictionary> durante um ciclo de vida do aplicativo.  
  
-   Você tem uma estrutura de recursos complicada que tem interdependências, em que uma referência de encaminhamento pode ser necessária. Referências de recursos estáticos não dão suporte a referências de encaminhamento, mas referências a recursos dinâmicos oferecem suporte a isso porque o recurso não precisa ser avaliado até o tempo de execução e referências de encaminhamento, portanto, não são um conceito relevante.  
  
-   Você está referenciando um recurso que é especificamente grande da perspectiva de um conjunto de compilação ou de trabalho, que pode não ser usado imediatamente quando a página é carregada. Referências de recursos estáticos sempre são carregadas do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] quando a página for carregada; no entanto, uma referência de recurso dinâmico não é carregado até que, na verdade, ele é usado.  
  
-   Você está criando um estilo no qual os valores setter podem ser obtidos de outros valores que são influenciados por temas ou por outras configurações do usuário.  
  
-   Você está aplicando recursos a elementos que podem ser reassociados na árvore lógica durante o tempo de vida do aplicativo. Potencialmente, a alteração do pai também altera o escopo de pesquisa de recursos; portanto, se você desejar que o recurso de um elemento reassociado seja reavaliado com base no novo escopo, sempre use uma referência de recursos dinâmicos.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Comportamento de pesquisa de recursos dinâmicos  
 Comportamento de pesquisa para obter uma referência de recurso dinâmico é comparável ao comportamento de pesquisa em seu código se você chamar <xref:System.Windows.FrameworkElement.FindResource%2A> ou <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1.  O processo de pesquisa verifica a chave solicitada no dicionário de recursos definido pelo elemento que define a propriedade.  
  
    -   Se o elemento define uma <xref:System.Windows.FrameworkElement.Style%2A> propriedade, o <xref:System.Windows.Style.Resources%2A> dicionário dentro a <xref:System.Windows.Style> é verificada.  
  
    -   Se o elemento define uma <xref:System.Windows.Controls.Control.Template%2A> propriedade, o <xref:System.Windows.FrameworkTemplate.Resources%2A> dicionário dentro a <xref:System.Windows.FrameworkTemplate> é verificada.  
  
2.  Em seguida, o processo de pesquisa percorre a árvore lógica de forma ascendente, até o elemento pai e seu dicionário de recursos. Isso continua até que o elemento raiz seja alcançado.  
  
3.  Em seguida, os recursos do aplicativo são verificados. Recursos de aplicativo são aqueles recursos dentro do dicionário de recursos definido pelos <xref:System.Windows.Application> do objeto para sua [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.  
  
4.  O dicionário de recursos de tema é verificado quanto ao tema ativo no momento. Se o tema for alterado em tempo de execução, o valor será reavaliado.  
  
5.  Os recursos do sistema são verificados.  
  
 O comportamento de exceção (se houver) varia:  
  
-   Se um recurso foi solicitado por um <xref:System.Windows.FrameworkElement.FindResource%2A> chamar e não foi encontrado, uma exceção será gerada.  
  
-   Se um recurso foi solicitado por um <xref:System.Windows.FrameworkElement.TryFindResource%2A> chamar e não foi encontrado, nenhuma exceção for gerada, mas o valor retornado é `null`. Se a propriedade sendo definida não aceitar `null`, em seguida, ele ainda é possível que uma exceção mais profunda seja gerada (isso depende da propriedade que está sendo definida).  
  
-   Se um recurso foi solicitado por uma referência de recurso dinâmico no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]e não foi encontrado, em seguida, o comportamento depende do sistema de propriedades geral, mas o comportamento geral é como se nenhuma operação de configuração de propriedade ocorreu no nível onde o recurso existe. Por exemplo, se você tentar definir a tela de fundo em um elemento de botão individual usando um recurso que não pôde ser avaliado, nenhum conjunto de valores resultará, mas o valor efetivo ainda poderá ser obtido de outros participantes do sistema de propriedades e da precedência de valor. Por exemplo, o valor de tela de fundo ainda poderá ser obtido de um estilo de botão definido localmente ou do estilo de tema. Para propriedades que não são definidas por estilos de tema, o valor efetivo após uma avaliação de recurso com falha pode ser obtido do valor padrão nos metadados da propriedade.  
  
#### <a name="restrictions"></a>Restrições  
 As referências de recursos dinâmicos têm algumas restrições importantes. Pelo menos, uma das seguintes condições deve ser verdadeira:  
  
-   A propriedade sendo definida deve ser uma propriedade em um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Se a propriedade deve ser suportada por um <xref:System.Windows.DependencyProperty>.  
  
-   A referência é para um valor em uma <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
-   A propriedade sendo definida deve ser uma propriedade em um <xref:System.Windows.Freezable> que é fornecido como um valor de uma <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> propriedade, ou um <xref:System.Windows.Setter> valor.  
  
 Porque a propriedade sendo definida deve ser um <xref:System.Windows.DependencyProperty> ou <xref:System.Windows.Freezable> propriedade, a maioria das alterações de propriedade podem ser propagadas para a interface do usuário porque uma alteração de propriedade (o valor do recurso dinâmico alterado) é reconhecida pelo sistema de propriedade. A maioria dos controles incluem lógica que forçará outro layout de um controle se um <xref:System.Windows.DependencyProperty> alterações e a propriedade puder afetar o layout. No entanto, nem todas as propriedades que têm uma [extensão de marcação DynamicResource](dynamicresource-markup-extension.md) como seu valor são garantidos para fornecer o valor de tal forma que elas sejam atualizadas em tempo real na interface do usuário. Essa funcionalidade ainda pode variar dependendo da propriedade, bem como do tipo que possui a propriedade, ou até mesmo da estrutura lógica do aplicativo.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Estilos, DataTemplates e chaves implícitas  
 Anteriormente, mencionamos que todos os itens em um <xref:System.Windows.ResourceDictionary> deve ter uma chave. No entanto, isso não significa que todos os recursos devem ter uma explícita `x:Key`. Vários tipos de objeto dão suporte a uma chave implícita quando definidos como um recurso, em que o valor da chave é vinculado ao valor de outra propriedade. Isso é conhecido como uma chave implícita, enquanto um `x:Key` atributo é uma chave explícita. Você pode substituir uma chave implícita especificando uma chave explícita.  
  
 Um cenário muito importante para recursos é quando você define uma <xref:System.Windows.Style>. Na verdade, um <xref:System.Windows.Style> quase sempre é definido como uma entrada em um dicionário de recursos, porque os estilos são inerentemente destinados à reutilização. Para obter mais informações sobre estilos, consulte [estilo e modelagem](../controls/styling-and-templating.md).  
  
 Os estilos de controles podem ser criados com uma chave implícita e referenciados com ela. Os estilos de tema que definem a aparência padrão de um controle se baseiam nessa chave implícita. A chave implícita, do ponto de vista de solicitá-la a <xref:System.Type> do próprio controle. A chave implícita, do ponto de vista da definição do recurso é o <xref:System.Windows.Style.TargetType%2A> do estilo. Portanto, se você estiver criando temas para controles personalizados, criando estilos que interagem com estilos de tema existentes, você não precisará especificar uma [X:Key](../../xaml-services/x-key-directive.md) para que <xref:System.Windows.Style>. Além disso, você desejar usar os estilos de tema, não precisará especificar nenhum estilo. Por exemplo, a seguinte definição de estilo funciona, mesmo que o <xref:System.Windows.Style> recurso parece não ter uma chave:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Esse estilo realmente tem uma chave: a chave implícita `typeof(` <xref:System.Windows.Controls.Button> `)`. Na marcação, você pode especificar uma <xref:System.Windows.Style.TargetType%2A> diretamente, como o tipo de nome (ou, opcionalmente, você pode usar [{... x: Type}](../../xaml-services/x-type-markup-extension.md) para retornar um <xref:System.Type>.  
  
 Por meio dos mecanismos de estilo de tema padrão usados pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], esse estilo é aplicado como o estilo de tempo de execução de um <xref:System.Windows.Controls.Button> na página, mesmo que o <xref:System.Windows.Controls.Button> não tente especificar sua <xref:System.Windows.FrameworkElement.Style%2A> propriedade ou um recurso específico fazer referência ao estilo. O estilo definido na página é encontrado anteriormente na sequência de pesquisa que o estilo de dicionário de tema, usando a mesma chave que tem o estilo de dicionário de tema. Você poderá especificar `<Button>Hello</Button>` em qualquer lugar na página e o estilo definido com <xref:System.Windows.Style.TargetType%2A> de `Button` se aplica a esse botão. Se você quiser, você pode ainda explicitamente uma chave para o estilo com o mesmo valor de tipo que <xref:System.Windows.Style.TargetType%2A>, para maior clareza na sua marcação, mas isso é opcional.  
  
 Chaves implícitas para estilos não se aplicam em um controle se <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> está `true` (Observe também que <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> pode ser definido como parte do comportamento nativo para a classe de controle, em vez de explicitamente em uma instância do controle). Além disso, para dar suporte a chaves implícitas para cenários de classes derivadas, o controle deve substituir <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (todos os controles existentes fornecidos como parte do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fazer isso). Para obter mais informações sobre estilos, temas e design de controle, consulte [diretrizes para criação de controles estilizados](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> também tem uma chave implícita. A chave implícita para um <xref:System.Windows.DataTemplate> é o <xref:System.Windows.DataTemplate.DataType%2A> valor da propriedade. <xref:System.Windows.DataTemplate.DataType%2A> também pode ser especificado como o nome do tipo em vez de usar explicitamente [{... x: Type} ](../../xaml-services/x-type-markup-extension.md). Para obter detalhes, consulte [visão geral de modelagem de dados](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.ResourceDictionary>
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Recursos e código](resources-and-code.md)
- [Definir e referenciar um recurso](how-to-define-and-reference-a-resource.md)
- [Visão geral do gerenciamento de aplicativos](../app-development/application-management-overview.md)
- [Extensão de marcação x:Type](../../xaml-services/x-type-markup-extension.md)
- [Extensão de marcação StaticResource](staticresource-markup-extension.md)
- [Extensão de marcação DynamicResource](dynamicresource-markup-extension.md)
