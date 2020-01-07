---
title: Namescopes XAML WPF
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: 97889b302aac06e118c93f2d000b0eeeed8b71bb
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559931"
---
# <a name="wpf-xaml-namescopes"></a>Namescopes XAML WPF
Os namescopes de XAML são um conceito que identifica objetos que são definidos em XAML. Os nomes em um namescope de XAML podem ser usados para estabelecer relações entre os nomes de objetos definidos por XAML e seus equivalentes de instância em uma árvore de objetos. Normalmente, os namescopes de XAML no código gerenciado do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são criados ao carregar as raízes da página XAML individual de um aplicativo XAML. Os namescopes XAML como o objeto de programação são definidos pela interface <xref:System.Windows.Markup.INameScope> e também são implementados pela classe prática <xref:System.Windows.NameScope>.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Namescopes em aplicativos de XAML carregados  
 Em um contexto mais amplo de programação ou de ciência da computação, os conceitos de programação geralmente incluem o princípio de um identificador exclusivo ou de um nome que pode ser usado para acessar um objeto. Para sistemas que usam identificadores ou nomes, o namescope define os limites dentro dos quais um processo ou uma técnica pesquisará, se um objeto com esse nome for solicitado ou os limites em que a exclusividade de nomes de identificação é imposta. Esses princípios gerais são verdadeiros para namescopes XAML. No WPF, os namescopes de XAML são criados no elemento raiz de uma página XAML quando a página é carregada. Cada nome especificado na página XAML, começando na raiz da página, é adicionado a um namescopes de XAML pertinente.  
  
 No WPF XAML, os elementos que são elementos raiz comuns (como <xref:System.Windows.Controls.Page>e <xref:System.Windows.Window>) sempre controlam um namescope XAML. Se um elemento como <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> for o elemento raiz da página na marcação, um processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adicionará um <xref:System.Windows.Controls.Page> raiz implicitamente para que o <xref:System.Windows.Controls.Page> possa fornecer um namescope de trabalho em funcionamento.  
  
> [!NOTE]
> As ações de build do WPF criam um namescope de XAML para uma produção de XAML mesmo se os atributos `Name` ou `x:Name` não estiverem definidos em nenhum elemento na marcação de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Se você tentar usar o mesmo nome duas vezes em qualquer namescope de XAML, uma exceção será gerada. Para o XAML do WPF que tem code-behind e faz parte de um aplicativo compilado, a exceção é gerada em tempo de compilação por ações de compilação do WPF, ao criar a classe gerada para a página durante a compilação de marcação inicial. Para o XAML que não é compilado por marcação por qualquer ação de build, as exceções relacionadas a problemas de namescopes de XAML podem ser geradas quando o XAML é carregado. Os designers de XAML também podem prever problemas de namescope de XAML em tempo de design.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Adicionando objetos a árvores de objetos de runtime  
 O momento em que o XAML é analisado representa o momento em que um namescope de XAML do WPF é criado e definido. Se você adicionar um objeto a uma árvore de objetos em um ponto no tempo após o momento em que o XAML que produziu a árvore foi analisado, um valor `Name` ou `x:Name` no novo objeto não atualizará automaticamente as informações em um namescope de XAML. Para adicionar um nome para um objeto em um namescope XAML do WPF depois que o XAML é carregado, você deve chamar a implementação apropriada do <xref:System.Windows.Markup.INameScope.RegisterName%2A> no objeto que define o namescope do XAML, que normalmente é a raiz da página XAML. Se o nome não estiver registrado, o objeto adicionado não poderá ser referenciado pelo nome por meio de métodos como <xref:System.Windows.FrameworkElement.FindName%2A>, e você não poderá usar esse nome para o direcionamento de animação.  
  
 O cenário mais comum para desenvolvedores de aplicativos é que você usará <xref:System.Windows.FrameworkElement.RegisterName%2A> para registrar nomes no namescope XAML na raiz atual da página. <xref:System.Windows.FrameworkElement.RegisterName%2A> faz parte de um cenário importante para storyboards que direcionam objetos para animações. Para obter mais informações, consulte [Visão geral de storyboards](../graphics-multimedia/storyboards-overview.md).  
  
 Se você chamar <xref:System.Windows.FrameworkElement.RegisterName%2A> em um objeto que não seja o objeto que define o namescope XAML, o nome ainda será registrado no namescope XAML em que o objeto de chamada é mantido, como se você tivesse chamado <xref:System.Windows.FrameworkElement.RegisterName%2A> no namescope XAML que define o objeto.  
  
### <a name="xaml-namescopes-in-code"></a>Namescopes de XAML no código  
 Você pode criar e usar namescopes de XAML no código. As APIs e os conceitos envolvidos na criação de namescopes de XAML são os mesmos, mesmo para um uso de código puro, porque o processador de XAML para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa essas APIs e conceitos quando processa o próprio XAML. Os conceitos e a API existem principalmente para que seja possível encontrar objetos por nome em uma árvore de objeto que é normalmente definida, parcialmente ou totalmente, em XAML.  
  
 Para aplicativos que são criados programaticamente, e não do XAML carregado, o objeto que define um namescope XAML deve implementar <xref:System.Windows.Markup.INameScope>, ou ser uma <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> classe derivada, a fim de dar suporte à criação de um namescope XAML em suas instâncias.  
  
 Além disso, para qualquer elemento que não é carregado e processado por um processador de XAML, o namescope de XAML do objeto não é criado ou inicializado por padrão. Você deve criar explicitamente um novo namescope de XAML para qualquer objeto no qual você pretende registrar nomes posteriormente. Para criar um namescope XAML, você chama o método de <xref:System.Windows.NameScope.SetNameScope%2A> estático. Especifique o objeto que o terá como o parâmetro `dependencyObject` e uma nova chamada de Construtor <xref:System.Windows.NameScope.%23ctor%2A> como o parâmetro `value`.  
  
 Se o objeto fornecido como `dependencyObject` para <xref:System.Windows.NameScope.SetNameScope%2A> não for uma implementação de <xref:System.Windows.Markup.INameScope>, <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, chamar <xref:System.Windows.FrameworkElement.RegisterName%2A> em qualquer elemento filho não terá nenhum efeito. Se você não conseguir criar o novo namescope de XAML explicitamente, as chamadas para <xref:System.Windows.FrameworkElement.RegisterName%2A> gerarão uma exceção.  
  
 Para obter um exemplo de uso de APIs de namescope de XAML no código, consulte [Definir um escopo de nome](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Namescopes de XAML em estilos e modelos  
 Os estilos e modelos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornecem a capacidade para reutilizar e reaplicar conteúdo de uma maneira simples. No entanto, os estilos e modelos também podem incluir elementos com nomes XAML definidos no nível do modelo. Esse mesmo modelo pode ser usado várias vezes em uma página. Por esse motivo, os estilos e modelos definem seus próprios namescopes de XAML, independente do local, em uma árvore de objetos, em que o estilo ou o modelo é aplicado.  
  
 Considere o exemplo a seguir:  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Aqui, o mesmo modelo é aplicado a dois botões diferentes. Se os modelos não tivessem namescopes de XAML distintos, o nome `TheBorder` usado no modelo causaria uma colisão de nomes no namescope de XAML. Cada instanciação do modelo tem seu próprio namescope de XAML, portanto, neste exemplo, cada namescope de XAML de modelo instanciado conteria exatamente um nome.  
  
 Os estilos também definem seus próprios namescopes de XAML, principalmente para que as partes de storyboards possam ter nomes específicos atribuídos. Esses nomes habilitam comportamentos específicos de controle que se destinarão a elementos desse nome, mesmo que o modelo tenha sido redefinido como parte da personalização do controle.  
  
 Devido aos namescopes de XAML separados, encontrar elementos nomeados em um modelo é mais desafiador que localizar um elemento nomeado que não faz parte do modelo em uma página. Primeiro, você precisa determinar o modelo aplicado, obtendo o valor da propriedade <xref:System.Windows.Controls.Control.Template%2A> do controle em que o modelo é aplicado. Em seguida, você chama a versão de modelo do <xref:System.Windows.FrameworkTemplate.FindName%2A>, passando o controle onde o modelo foi aplicado como o segundo parâmetro.  
  
 Se você for um autor de controle e estiver gerando uma convenção em que um determinado elemento nomeado em um modelo aplicado é o destino para um comportamento que é definido pelo próprio controle, você pode usar o método <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> do seu código de implementação de controle. O método <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> é protegido, portanto, somente o autor do controle tem acesso a ele.  
  
 Se você estiver trabalhando de dentro de um modelo e precisar chegar ao namescope do XAML onde o modelo é aplicado, obtenha o valor de <xref:System.Windows.FrameworkElement.TemplatedParent%2A>e, em seguida, chame <xref:System.Windows.FrameworkElement.FindName%2A> lá. Um exemplo de trabalho dentro do modelo seria se você estivesse escrevendo a implementação do manipulador de eventos em que o evento será acionado de um elemento em um modelo aplicado.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Namescopes de XAML e APIs relacionadas a nomes  
 <xref:System.Windows.FrameworkElement> tem <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> e métodos <xref:System.Windows.FrameworkElement.UnregisterName%2A>. Se o objeto em que você chama esses métodos é proprietário de um namescope de XAML, os métodos chamam nos métodos do namescope de XAML relevante. Caso contrário, o elemento pai é verificado para ver se ele é proprietário de um namescope de XAML e esse processo continua recursivamente até que seja encontrado um namescope de XAML (devido ao comportamento do processador de XAML, é garantido que haverá um namescope de XAML na raiz). <xref:System.Windows.FrameworkContentElement> tem comportamentos análogos, com exceção de que nenhum <xref:System.Windows.FrameworkContentElement> terá um namescope XAML. Os métodos existem no <xref:System.Windows.FrameworkContentElement> para que as chamadas possam ser encaminhadas eventualmente para um elemento pai de <xref:System.Windows.FrameworkElement>.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> é usado para mapear um novo namescope de XAML para um objeto existente. Você pode chamar <xref:System.Windows.NameScope.SetNameScope%2A> mais de uma vez para redefinir ou limpar o namescope XAML, mas esse não é um uso comum. Além disso, <xref:System.Windows.NameScope.GetNameScope%2A> normalmente não é usado no código.  
  
### <a name="xaml-namescope-implementations"></a>Implementações de namescope de XAML  
 As classes a seguir implementam <xref:System.Windows.Markup.INameScope> diretamente:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> não usa nomes XAML ou namescopes; em vez disso, ele usa chaves, porque é uma implementação de dicionário. O único motivo pelo qual <xref:System.Windows.ResourceDictionary> implementa <xref:System.Windows.Markup.INameScope> é para que ele possa gerar exceções para o código do usuário que ajudam a esclarecer a distinção entre um verdadeiro namescope XAML e como um <xref:System.Windows.ResourceDictionary> manipula as chaves e também para garantir que os namescopes XAML não sejam aplicados a um <xref:System.Windows.ResourceDictionary> por elementos pai.  
  
 <xref:System.Windows.FrameworkTemplate> e <xref:System.Windows.Style> implementar <xref:System.Windows.Markup.INameScope> por meio de definições de interface explícitas. As implementações explícitas permitem que esses namescopes XAML se comportem de forma convencional quando são acessados por meio da interface <xref:System.Windows.Markup.INameScope>, que é como os namescopes XAML são comunicados por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processos internos. Mas as definições de interface explícitas não fazem parte da superfície convencional da API de <xref:System.Windows.FrameworkTemplate> e <xref:System.Windows.Style>, porque raramente é necessário chamar os métodos <xref:System.Windows.Markup.INameScope> em <xref:System.Windows.FrameworkTemplate> e <xref:System.Windows.Style> diretamente e, em vez disso, usaria outra API, como <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 As classes a seguir definem seu próprio namescope XAML, usando a classe auxiliar <xref:System.Windows.NameScope?displayProperty=nameWithType> e conectando-se à sua implementação de namescope do XAML por meio da propriedade <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> anexada:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Veja também

- [Namespaces XAML e mapeamento de namespace para XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [Diretiva x:Name](../../../desktop-wpf/xaml-services/xname-directive.md)
