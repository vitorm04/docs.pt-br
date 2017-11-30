---
title: Arquitetura do WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8580f805e23732f24248a046201c87b0a5a370b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-architecture"></a>Arquitetura do WPF
Este tópico fornece um tour guiado pela hierarquia de classe de [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]. Ele aborda a maioria dos subsistemas principais do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e descreve como eles interagem. Ele também detalha algumas das escolhas feitas pelos arquitetos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
  
<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 O modelo de programação principal do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é exposto por meio de código gerenciado. No início da fase de projeto do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], houve um número de debates sobre qual deveria ser o limite determinado entre os componentes gerenciados e os não gerenciados do sistema. O [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] fornece inúmeros recursos que tornam o desenvolvimento mais produtivo e robusto (incluindo o gerenciamento de memória, tratamento de erro, CTS, etc.), mas eles vêm com um custo.  
  
 Os principais componentes do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] estão ilustrados na figura abaixo. As seções em vermelho do diagrama (PresentationFramework, PresentationCore e milcore) são as principais partes de código do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Dessas, somente uma é um componente não gerenciado – milcore. O milcore é escrito em código não gerenciado para permitir uma forte integração com o [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Toda a exibição no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é feito por meio do mecanismo do [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], permitindo renderização eficiente de hardware e software. O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] também exigiu controle detalhado de memória e execução. O mecanismo de composição no milcore é extremamente sensível ao desempenho e exigiu que se abdicasse de muitas vantagens do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] para obtenção de um melhor desempenho.  
  
 ![A posição do WPF no .NET Framework.](../../../../docs/framework/wpf/advanced/media/wpf-architect1.PNG "wpf_architect1")  
  
 Comunicação entre as partes gerenciadas e não gerenciadas do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é discutida posteriormente neste tópico. O restante do modelo de programação gerenciado é descrito abaixo.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 A maioria dos objetos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] derivam <xref:System.Windows.Threading.DispatcherObject>, que fornece as construções básicas para lidar com simultaneidade e threading. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se baseia em um sistema de mensagens implementado pelo dispatcher. Isso funciona de maneira muito semelhante ao já familiar aumento de mensagens do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]; na verdade, o dispatcher do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usa mensagens User32 para realizar chamadas entre threads.  
  
 Há na verdade dois conceitos principais a serem entendidos ao discutir a simultaneidade no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – o dispatcher e afinidade de thread.  
  
 Durante a fase de design do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a meta era mudar para um único thread de execução, mas um modelo não sujeito à afinidade de thread. A afinidade de thread ocorre quando um componente usa a identidade do thread em execução para armazenar algum tipo de estado. A forma mais comum disso é usar o armazenamento local de thread (TLS) para armazenar o estado. Afinidade de threads requer que cada thread lógica de execução pertença a apenas um thread físico no sistema operacional, que pode passar a fazer uso intensivo de memória. No final, o modelo de threading do WPF foi mantido em sincronização com o modelo de threading User32 existente, de execução em thread único com afinidade de thread. O principal motivo para isso foi interoperabilidade – sistemas como [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], a área de transferência e o Internet Explorer exigem, todos, execução STA (afinidade de thread único).  
  
 Considerando que você tem objetos com threading STA, você precisa de uma maneira para se comunicar entre threads e validar que você está no thread correto. Eis aí a função do dispatcher. O dispatcher é um sistema básico de despacho de mensagens, com várias filas priorizadas. Exemplos de mensagens incluem notificações de entrada bruta (o mouse foi movido), funções de estrutura (layout) ou comandos do usuário (executar este método). Derivando de <xref:System.Windows.Threading.DispatcherObject>, você cria um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] do objeto que tem comportamento STA e receberá um ponteiro para um distribuidor na hora da criação.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Uma das principais filosofias da arquitetura usadas ao compilar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] foi a preferência por propriedades sobre métodos ou eventos. Propriedades são declarativas e permitem que você especifique mais facilmente a intenção em vez de ação. Isso também deu suporte para um sistema controlado por modelo ou por dados para exibição do conteúdo de interface do usuário. Essa filosofia tinha o efeito desejado de criar mais propriedades do que o número ao qual você era capaz de se associar, de modo a controlar melhor o comportamento de um aplicativo.  
  
 Para que mais do sistema fosse controlado por propriedades, era necessário um sistema de propriedades mais sofisticado do que o fornecido pelo [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Um exemplo simples desta sofisticação é encontrado nas notificações de alteração. Para habilitar a associação bidirecional, você precisa que ambos os lados da associação deem suporte à notificação de alteração. Para ter comportamento ligado aos valores de propriedade, você precisa ser notificado quando o valor da propriedade é alterado. O [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] tem uma interface, **INotifyPropertyChange**, que permite que um objeto publique notificações de alteração, mas isso é opcional.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Fornece um sistema de propriedade mais sofisticado, derivado do <xref:System.Windows.DependencyObject> tipo. O sistema de propriedades é realmente um sistema de propriedade de "dependência", que controla as dependências entre expressões de propriedade e revalida automaticamente valores de propriedade quando as dependências são alteradas. Por exemplo, se você tiver uma propriedade herdada (como <xref:System.Windows.Controls.Control.FontSize%2A>), o sistema é atualizado automaticamente se a propriedade é alterada em um pai de um elemento que herda o valor.  
  
 A base do sistema de propriedades do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é o conceito de uma expressão de propriedade. Nesta primeira versão do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], o sistema de expressão de propriedade é fechado e as expressões são fornecidas como parte da estrutura. As expressões são o motivo pelo qual o sistema de propriedades não tem associação de dados, definição de estilo ou herança fixados no código, mas sim fornecidos por camadas posteriores dentro do framework.  
  
 O sistema de propriedades também fornece armazenamento esparso de valores de propriedade. Já que os objetos podem ter dezenas (se não centenas) de propriedades e a maioria dos valores estão em seu estado padrão (herdado, definido por estilos, etc.), nem toda instância de um objeto precisa ter o peso total de todas as propriedades definidas nele.  
  
 O último novo recurso do sistema de propriedades é o conceito de propriedades anexadas. Elementos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] são criados sobre o princípio de composição e reutilização de componente. Ele é geralmente o caso que algumas que contém o elemento (como um <xref:System.Windows.Controls.Grid> elemento layout) precisar de dados adicionais dos elementos filho para controlar seu comportamento (como informações de linha ou coluna). Em vez de associar todas essas propriedades com cada elemento, qualquer objeto tem permissão para fornecer definições de propriedade para qualquer outro objeto. Isso é semelhante aos recursos "expando" do JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Com um sistema definido, a próxima etapa é fazer com que pixels sejam desenhados na tela. O <xref:System.Windows.Media.Visual> classe fornece para criar uma árvore de objetos visuais, cada um opcionalmente contendo instruções de desenho e metadados sobre como renderizar essas instruções (corte, transformação, etc.). <xref:System.Windows.Media.Visual>foi projetado para ser extremamente simples e flexível, portanto, a maioria dos recursos não tem nenhum public [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] exposição e dependem fortemente de funções de retorno de chamada protegido.  
  
 <xref:System.Windows.Media.Visual>é realmente o ponto de entrada para o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sistema de composição. <xref:System.Windows.Media.Visual>é o ponto de conexão entre esses dois subsistemas, gerenciados [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] e milcore não gerenciado.  
  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exibe dados percorrendo as estruturas de dados não gerenciados gerenciadas pelo milcore. Essas estruturas, chamadas nós de composição, representam uma árvore de exibição hierárquica com instruções de renderização em cada nó. Essa árvore, ilustrada no lado direito da figura abaixo, só é acessível por meio de um protocolo de mensagens.  
  
 Ao programar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], criar <xref:System.Windows.Media.Visual> elementos e tipos derivados, que internamente se comunicam com a árvore de composição através deste protocolo de mensagens. Cada <xref:System.Windows.Media.Visual> em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pode criar um, nenhum ou vários nós de composição.  
  
 ![A árvore visual do Windows Presentation Foundation.](../../../../docs/framework/wpf/advanced/media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Há um detalhe arquitetural muito importante a observar aqui – toda a árvore de elementos visuais e instruções de desenho é armazenada em cache. Em termos gráficos, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usa um sistema de renderização retido. Isso permite ao sistema redesenhar com altas taxas de atualização sem o bloqueio do sistema de composição em retornos de chamada para o código do usuário. Isso ajuda a impedir o surgimento de um aplicativo que não responde.  
  
 Outro detalhe importante que não é realmente perceptível no diagrama é o modo como o sistema realmente executa a composição.  
  
 No User32 e [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], o sistema funciona em um sistema de recorte de modo imediato. Quando um componente precisa ser renderizado, o sistema estabelece os limites de recorte fora dos quais o componente não tem permissão para tocar nos pixels e, em seguida, é solicitado ao componente que ele pinte os pixels dentro dessa caixa. Este sistema funciona muito bem em sistemas com restrição de memória porque quando algo é alterado, você só tem que tocar o componente afetado – não há jamais dois componentes que contribuam para a cor de um único pixel.  
  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usa um modelo de pintura de "algoritmo de pincel". Isso significa que, em vez de cortar cada componente, é solicitado a cada componente que renderize da parte de trás da exibição para a parte da frente. Isso permite que cada componente pinte sobre a exibição do componente anterior. A vantagem desse modelo é que você pode ter formas complexas, parcialmente transparentes. Com o hardware gráfico moderno de hoje, esse modelo é relativamente rápido (que não era o caso quando User32/[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] foram criados).  
  
 Conforme mencionado anteriormente, uma filosofia central do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é mover para um modelo de programação mais declarativo, "centrado em propriedades". No sistema visual, isso aparece em alguns locais interessantes.  
  
 Primeiro, se você pensar sobre o sistema gráfico de modo retido, isso estará realmente se movendo de um modelo de tipo DrawLine/DrawLine imperativo para um modelo orientado a dados – new Line()/new Line(). A mudança para a renderização controlada por dados permite que operações complexas nas instruções de desenho sejam expressas usando propriedades. Os tipos derivados de <xref:System.Windows.Media.Drawing> são efetivamente o modelo de objeto para renderização.  
  
 Em segundo lugar, se você avaliar o sistema de animação, verá que ele é quase completamente declarativo. Em vez de exigir que um desenvolvedor calcule o próximo local, ou a próxima cor, você pode expressar animações como um conjunto de propriedades em um objeto de animação. Essas animações podem expressar a intenção do desenvolvedor ou designer (mover esse botão daqui para lá em 5 segundos), e o sistema pode determinar a maneira mais eficiente de fazer isso.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>define subsistemas centrais, incluindo o Layout, entrada e eventos.  
  
 Layout é um conceito central no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Em muitos sistemas, há um conjunto fixo de modelos de layout (o HTML dá suporte a três modelos de layout; fluxo, absoluto e tabelas) ou nenhum modelo de layout (o User32 dá suporte somente a posicionamento absoluto). O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] começou com a suposição de que os desenvolvedores e designers queriam um modelo de layout flexível e extensível, que pudesse ser controlado por valores de propriedade em vez de lógica imperativa. No <xref:System.Windows.UIElement> nível, o contrato básico para layout é apresentado – um duas fases modelo com <xref:System.Windows.UIElement.Measure%2A> e <xref:System.Windows.UIElement.Arrange%2A> passa.  
  
 <xref:System.Windows.UIElement.Measure%2A>permite que um componente determinar o quanto ele gostaria de tamanho. Esta é uma fase separada de <xref:System.Windows.UIElement.Arrange%2A> porque há muitas situações onde um elemento pai pedirá a um filho para medir várias vezes para determinar suas melhores posição e tamanho. O fato de que os elementos pai pedem a elementos filho para se medirem demonstra outra filosofia chave do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – dimensionar para o conteúdo. Todos os controles em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dão suporte à capacidade de dimensionar para o tamanho natural de seu conteúdo. Isso torna a localização muito mais fácil e permite layout dinâmico dos elementos conforme as coisas são redimensionadas. O <xref:System.Windows.UIElement.Arrange%2A> fase permite que um pai posicione e determine o tamanho final de cada filho.  
  
 Muito tempo é geralmente gasto falando sobre o lado da saída do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> e objetos relacionados. No entanto, também há um tremendo montante de inovação no lado de entrada. Provavelmente, a alteração mais fundamental no modelo de entrada para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é o modelo consistente pelo qual os eventos de entrada são roteados através do sistema.  
  
 A entrada se origina como um sinal em um driver de dispositivo de modo kernel e é roteada para o processo e thread corretos por um processo intrincado, que envolve o kernel do Windows e o User32. Depois que a mensagem User32 correspondente à entrada é roteada para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ela será convertida em uma mensagem de entrada bruta do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e enviada para o dispatcher. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite que eventos de entrada brutos sejam convertidos em vários eventos reais, permitindo que recursos como "MouseEnter" sejam implementados em um nível baixo do sistema com entrega garantida.  
  
 Cada evento de entrada é convertido em pelo menos dois eventos – um evento de "visualização" e o evento real. Todos os eventos no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] têm uma noção de roteamento através da árvore de elementos. Dizemos que os eventos são roteados por "propagação" se percorrem a rota de um destino na parte superior da árvore até a raiz, ou então que são roteados por "túnel" se começam na raiz e percorrem a rota até um destino. Eventos de visualização de entrada são roteados por túnel, permitindo que qualquer elemento na árvore tenha uma oportunidade de filtrar ou executar uma ação no evento. Os eventos regulares (não visualização) são então roteados por propagação do destino até a raiz.  
  
 Essa divisão entre as fases de túnel e de propagação torna a implementação de recursos como aceleradores de teclado funcionar de forma consistente em um mundo composto. No User32, você poderia implementar aceleradores de teclado tendo uma única tabela global contendo todos os aceleradores aos quais que você quisesse dar suporte (Ctrl + N mapeando para "New"). No dispatcher para seu aplicativo, você chamaria **TranslateAccelerator**, que rastrearia as mensagens de entrada no User32 e determinaria se havia correspondência entre alguma delas e um acelerador registrado. Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] isso não funcionaria, pois o sistema é totalmente "passível de composição" – qualquer elemento pode manipular e usar qualquer acelerador de teclado. Esse modelo de duas fases para a entrada permite que os componentes implementem seu próprio "TranslateAccelerator".  
  
 Para levar isso um passo além disso, <xref:System.Windows.UIElement> também introduz a noção de CommandBindings. O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sistema de comando permite que os desenvolvedores definam funcionalidade em termos de um ponto de extremidade de comando – algo que implementa <xref:System.Windows.Input.ICommand>. Associações de comando permitem a um elemento definir um mapeamento entre um gesto de entrada (Ctrl + N) e um comando (New). Tanto os gestos de entrada quanto as definições de comando são extensíveis e podem ser ligados juntos durante o tempo de uso. Isso torna trivial, por exemplo, permitir que um usuário final personalize as associações de teclas que deseja usar em um aplicativo.  
  
 Até esse ponto nesse tópico, os recursos "principais" do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – recursos implementados no assembly PresentationCore – têm sido o foco. Ao criar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], uma separação entre as partes fundamentais de limpeza (como o contrato de layout com **medidas** e **organizar**) e partes do framework (como a implementação de um determinado layout como <xref:System.Windows.Controls.Grid>) foi o resultado desejado. A meta era fornecer um ponto de extensibilidade baixo na pilha que permitisse aos desenvolvedores externos criar suas próprias estruturas, se necessário.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>pode ser visto de duas maneiras diferentes. Ele introduz um conjunto de políticas e personalizações dos subsistemas introduzidos nas camadas inferiores do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ele também introduz um conjunto de novos subsistemas.  
  
 A diretiva primária introduzida por <xref:System.Windows.FrameworkElement> ao redor do layout do aplicativo. <xref:System.Windows.FrameworkElement>amplia o contrato de layout básico introduzido por <xref:System.Windows.UIElement> e adiciona a noção de um layout "slot", o que torna mais fácil para autores de layout ter um conjunto consistente de propriedade orientado a semântica de layout. Propriedades como <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, e <xref:System.Windows.FrameworkElement.Margin%2A> (entre outros) oferecem todos os componentes derivados de <xref:System.Windows.FrameworkElement> um comportamento consistente dentro de contêineres de layout.  
  
 <xref:System.Windows.FrameworkElement>também fornece mais fácil [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] exposição a muitos recursos encontrados nas camadas principais de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Por exemplo, <xref:System.Windows.FrameworkElement> fornece acesso direto a animação através de <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> método. A <xref:System.Windows.Media.Animation.Storyboard> fornece uma maneira de várias animações de um conjunto de propriedades de script.  
  
 As duas coisas mais importantes que <xref:System.Windows.FrameworkElement> apresenta são a associação de dados e estilos.  
  
 O subsistema de associação de dados no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] deve ser relativamente familiar para qualquer pessoa que usou o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou o [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] para criar uma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo. Em cada um desses sistemas, há uma maneira simples de expressar se você deseja que uma ou mais propriedades de um determinado elemento seja associada a uma parte dos dados. O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tem suporte completo para associação de propriedades, transformações e associação de listas.  
  
 Um dos recursos mais interessantes de associação de dados no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é a introdução de modelos de dados. Modelos de dados permitem que você especifique declarativamente como uma parte dos dados deve ser visualizada. Em vez de criar uma interface do usuário personalizada que pode ser associada a dados, você pode inverter o problema e permitir que os dados determinem a exibição que será criada.  
  
 Definição de estilo é na verdade uma forma leve de associação de dados. Usando estilização, você pode associar um conjunto de propriedades de uma definição compartilhada a uma ou mais instâncias de um elemento. Estilos são aplicados a um elemento por referência explícita (definindo o <xref:System.Windows.FrameworkElement.Style%2A> propriedade) ou implicitamente ao associar um estilo com o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] tipo do elemento.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 O recurso mais significativo do controle é a modelagem. Se você pensar sobre o sistema de composição do WPF como um sistema de renderização de modo retido, a modelagem permitirá que um controle descreva sua renderização de maneira declarativa e parametrizada. Um <xref:System.Windows.Controls.ControlTemplate> é realmente nada mais que um script para criar um conjunto de filhos elementos, com associações a propriedades oferecidas pelo controle.  
  
 <xref:System.Windows.Controls.Control>Fornece um conjunto de propriedades de estoque, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, entre outros, que os autores de modelo podem usar para personalizar a exibição de um controle. A implementação de um controle oferece um modelo de dados e um modelo de interação. O modelo de interação define um conjunto de comandos (como Close para uma janela) e associações para gestos de entrada (como clicar no X vermelho no canto superior da janela). O modelo de dados fornece um conjunto de propriedades para personalizar o modelo de interação ou então personalizar a exibição (determinado pelo modelo).  
  
 Essa divisão entre o modelo de dados (propriedades), o modelo de interação (comandos e eventos) e o modelo de exibição (modelos) permite a completa personalização da aparência e comportamento de um controle.  
  
 Um aspecto comum do modelo de dados dos controles é o modelo de conteúdo. Se você observar um controle como <xref:System.Windows.Controls.Button>, você verá que ele tem uma propriedade chamada "Content" do tipo <xref:System.Object>. Em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], essa propriedade seria normalmente uma cadeia de caracteres – no entanto, isso limita o tipo de conteúdo que você pode colocar em um botão. O conteúdo de um botão pode ser uma cadeia de caracteres simples, um objeto de dados complexo ou uma árvore de elementos inteira. No caso de um objeto de dados, o modelo de dados é usado para construir uma exibição.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Resumo  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] foi projetado para permitir que você crie sistemas de apresentação dinâmicos, controlados por dados. Cada parte do sistema foi projetada para criar objetos através de conjuntos de propriedades que controlam o comportamento. A associação de dados é uma parte fundamental do sistema e está integrada em todas as camadas.  
  
 Aplicativos tradicionais criam uma exibição e, em seguida, associam a alguns dados. Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], tudo que se relaciona ao controle e todos os aspectos da exibição são gerados por algum tipo de associação de dados. O texto encontrado em um botão é exibido por meio da criação de um controle composto dentro do botão e da associação de sua exibição à propriedade de conteúdo do botão.  
  
 Quando você começar a desenvolver aplicativos com base em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], isso deverá se tornar muito familiar. Você pode definir propriedades, usar objetos e associar dados praticamente da mesma forma que poderia fazer usando [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. Com uma investigação mais profunda da arquitetura do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], você descobrirá que existe a possibilidade de criar aplicativos muito mais sofisticados que, fundamentalmente, tratem os dados como o controlador principal do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Threading.DispatcherObject>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Controls.Control>  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Layout](../../../../docs/framework/wpf/advanced/layout.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
