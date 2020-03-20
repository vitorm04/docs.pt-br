---
title: Arquitetura
ms.date: 03/30/2017
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
ms.openlocfilehash: b16be8470a47f3e8e362feb0b13e10aa901baacb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187129"
---
# <a name="wpf-architecture"></a>Arquitetura do WPF
Este tópico fornece uma visita guiada à hierarquia de classes da Windows Presentation Foundation (WPF). Ele cobre a maioria dos principais subsistemas do WPF, e descreve como eles interagem. Ele também detalha algumas das escolhas feitas pelos arquitetos da WPF.  

<a name="System_Object"></a>
## <a name="systemobject"></a>System.Object  
 O modelo de programação wpf principal é exposto através de código gerenciado. No início da fase de projeto da WPF houve uma série de debates sobre onde a linha deve ser traçada entre os componentes gerenciados do sistema e os não gerenciados. O CLR fornece uma série de recursos que tornam o desenvolvimento mais produtivo e robusto (incluindo gerenciamento de memória, manipulação de erros, sistema de tipo comum, etc.), mas eles têm um custo.  
  
 Os principais componentes do WPF são ilustrados na figura abaixo. As seções vermelhas do diagrama (PresentationFramework, PresentationCore e milcore) são as principais partes de código do WPF. Dessas, somente uma é um componente não gerenciado – milcore. Milcore é escrito em código não gerenciado para permitir uma integração apertada com o DirectX. Toda a exibição no WPF é feita através do motor DirectX, permitindo uma renderização eficiente de hardware e software. O WPF também exigiu um bom controle sobre a memória e a execução. O motor de composição em milcore é extremamente sensível ao desempenho, e exigiu abrir mão de muitas vantagens da CLR para ganhar desempenho.  
  
 ![A posição do WPF dentro do Quadro .NET.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 A comunicação entre as partes gerenciadas e não gerenciadas do WPF é discutida posteriormente neste tópico. O restante do modelo de programação gerenciado é descrito abaixo.  
  
<a name="System_Threading_DispatcherObject"></a>
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 A maioria dos objetos no WPF deriva, <xref:System.Windows.Threading.DispatcherObject>que fornece os construtos básicos para lidar com a concorrência e o threading. O WPF é baseado em um sistema de mensagens implementado pelo despachante. Isso funciona muito parecido com a bomba de mensagens Win32 familiar; na verdade, o despachante do WPF usa mensagens User32 para realizar chamadas de thread cruzado.  
  
 Existem realmente dois conceitos fundamentais para entender ao discutir a concorrência no WPF – o despachante e a afinidade de segmentos.  
  
 Durante a fase de design do WPF, o objetivo era passar para um único segmento de execução, mas um modelo não-thread "afetivo". A afinidade de thread ocorre quando um componente usa a identidade do thread em execução para armazenar algum tipo de estado. A forma mais comum disso é usar o armazenamento local de thread (TLS) para armazenar o estado. Afinidade de threads requer que cada thread lógica de execução pertença a apenas um thread físico no sistema operacional, que pode passar a fazer uso intensivo de memória. No final, o modelo de threading do WPF foi mantido em sincronização com o modelo de threading User32 existente, de execução em thread único com afinidade de thread. A principal razão para isso foi a interoperabilidade – sistemas como o OLE 2.0, a área de transferência e o Internet Explorer exigem a execução de uma única afinidade de rosca (STA).  
  
 Considerando que você tem objetos com threading STA, você precisa de uma maneira para se comunicar entre threads e validar que você está no thread correto. Eis aí a função do dispatcher. O dispatcher é um sistema básico de despacho de mensagens, com várias filas priorizadas. Exemplos de mensagens incluem notificações de entrada bruta (o mouse foi movido), funções de estrutura (layout) ou comandos do usuário (executar este método). Ao derivar <xref:System.Windows.Threading.DispatcherObject>de , você cria um objeto CLR que tem comportamento STA, e será dado um ponteiro para um despachante no momento da criação.  
  
<a name="System_Windows_DependencyObject"></a>
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Uma das principais filosofias arquitetônicas utilizadas na construção do WPF era a preferência por propriedades sobre métodos ou eventos. Propriedades são declarativas e permitem que você especifique mais facilmente a intenção em vez de ação. Isso também deu suporte para um sistema controlado por modelo ou por dados para exibição do conteúdo de interface do usuário. Essa filosofia tinha o efeito desejado de criar mais propriedades do que o número ao qual você era capaz de se associar, de modo a controlar melhor o comportamento de um aplicativo.  
  
 Para ter mais do sistema conduzido por propriedades, era necessário um sistema de propriedade mais rico do que o que a CLR fornece. Um exemplo simples desta sofisticação é encontrado nas notificações de alteração. Para habilitar a associação bidirecional, você precisa que ambos os lados da associação deem suporte à notificação de alteração. Para ter comportamento ligado aos valores de propriedade, você precisa ser notificado quando o valor da propriedade é alterado. O Microsoft .NET Framework tem uma interface, **INotifyPropertyChange**, que permite que um objeto publique notificações de alteração, porém é opcional.  
  
 O WPF fornece um sistema de <xref:System.Windows.DependencyObject> propriedade mais rico, derivado do tipo. O sistema de propriedades é realmente um sistema de propriedade de "dependência", que controla as dependências entre expressões de propriedade e revalida automaticamente valores de propriedade quando as dependências são alteradas. Por exemplo, se você tiver uma <xref:System.Windows.Controls.Control.FontSize%2A>propriedade que herda (como), o sistema é automaticamente atualizado se a propriedade mudar em um pai de um elemento que herda o valor.  
  
 A base do sistema de propriedade wpf é o conceito de uma expressão de propriedade. Nesta primeira versão do WPF, o sistema de expressão de propriedade é fechado, e as expressões são todas fornecidas como parte do quadro. As expressões são o motivo pelo qual o sistema de propriedades não tem associação de dados, definição de estilo ou herança fixados no código, mas sim fornecidos por camadas posteriores dentro do framework.  
  
 O sistema de propriedades também fornece armazenamento esparso de valores de propriedade. Já que os objetos podem ter dezenas (se não centenas) de propriedades e a maioria dos valores estão em seu estado padrão (herdado, definido por estilos, etc.), nem toda instância de um objeto precisa ter o peso total de todas as propriedades definidas nele.  
  
 O último novo recurso do sistema de propriedades é o conceito de propriedades anexadas. Os elementos WPF são construídos sobre o princípio da composição e reutilização dos componentes. É frequentemente o caso de que algum <xref:System.Windows.Controls.Grid> elemento contendo (como um elemento de layout) precisa de dados adicionais sobre elementos infantis para controlar seu comportamento (como as informações de Linha/Coluna). Em vez de associar todas essas propriedades com cada elemento, qualquer objeto tem permissão para fornecer definições de propriedade para qualquer outro objeto. Isso é semelhante aos recursos "expando" do JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Com um sistema definido, a próxima etapa é fazer com que pixels sejam desenhados na tela. A <xref:System.Windows.Media.Visual> classe prevê a construção de uma árvore de objetos visuais, cada uma contendo opcionalmente instruções de desenho e metadados sobre como renderizar essas instruções (recorte, transformação, etc.). <xref:System.Windows.Media.Visual>é projetado para ser extremamente leve e flexível, de modo que a maioria dos recursos não têm exposição de API pública e dependem fortemente de funções de retorno de chamada protegidas.  
  
 <xref:System.Windows.Media.Visual>é realmente o ponto de entrada para o sistema de composição WPF. <xref:System.Windows.Media.Visual>é o ponto de conexão entre esses dois subsistemas, a API gerenciada e o milcore não gerenciado.  
  
 O WPF exibe dados atravessando as estruturas de dados não gerenciadas gerenciadas pelo milcore. Essas estruturas, chamadas nós de composição, representam uma árvore de exibição hierárquica com instruções de renderização em cada nó. Essa árvore, ilustrada no lado direito da figura abaixo, só é acessível por meio de um protocolo de mensagens.  
  
 Ao programar o WPF, você cria <xref:System.Windows.Media.Visual> elementos e tipos derivados, que se comunicam internamente com a árvore de composição através deste protocolo de mensagens. Cada <xref:System.Windows.Media.Visual> um no WPF pode criar um, nenhum ou vários nós de composição.  
  
 ![A árvore visual da Fundação Windows Presentation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Há um detalhe arquitetural muito importante a observar aqui – toda a árvore de elementos visuais e instruções de desenho é armazenada em cache. Em termos gráficos, o WPF usa um sistema de renderização retido. Isso permite ao sistema redesenhar com altas taxas de atualização sem o bloqueio do sistema de composição em retornos de chamada para o código do usuário. Isso ajuda a impedir o surgimento de um aplicativo que não responde.  
  
 Outro detalhe importante que não é realmente perceptível no diagrama é o modo como o sistema realmente executa a composição.  
  
 No User32 e GDI, o sistema funciona em um sistema de recorte de modo imediato. Quando um componente precisa ser renderizado, o sistema estabelece os limites de recorte fora dos quais o componente não tem permissão para tocar nos pixels e, em seguida, é solicitado ao componente que ele pinte os pixels dentro dessa caixa. Este sistema funciona muito bem em sistemas com restrição de memória porque quando algo é alterado, você só tem que tocar o componente afetado – não há jamais dois componentes que contribuam para a cor de um único pixel.  
  
 WPF usa um modelo de pintura "algoritmo do pintor". Isso significa que, em vez de cortar cada componente, é solicitado a cada componente que renderize da parte de trás da exibição para a parte da frente. Isso permite que cada componente pinte sobre a exibição do componente anterior. A vantagem desse modelo é que você pode ter formas complexas, parcialmente transparentes. Com o hardware gráfico moderno de hoje, este modelo é relativamente rápido (o que não foi o caso quando o User32/ GDI foi criado).  
  
 Como mencionado anteriormente, uma filosofia central da WPF é passar para um modelo mais declarativo, "centrado na propriedade" de programação. No sistema visual, isso aparece em alguns locais interessantes.  
  
 Primeiro, se você pensar sobre o sistema gráfico de modo retido, isso estará realmente se movendo de um modelo de tipo DrawLine/DrawLine imperativo para um modelo orientado a dados – new Line()/new Line(). A mudança para a renderização controlada por dados permite que operações complexas nas instruções de desenho sejam expressas usando propriedades. Os tipos derivados <xref:System.Windows.Media.Drawing> são efetivamente o modelo de renderização.  
  
 Em segundo lugar, se você avaliar o sistema de animação, verá que ele é quase completamente declarativo. Em vez de exigir que um desenvolvedor calcule o próximo local, ou a próxima cor, você pode expressar animações como um conjunto de propriedades em um objeto de animação. Essas animações podem expressar a intenção do desenvolvedor ou designer (mover esse botão daqui para lá em 5 segundos), e o sistema pode determinar a maneira mais eficiente de fazer isso.  
  
<a name="System_Windows_UIElement"></a>
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>define subsistemas principais, incluindo Layout, Entrada e Eventos.  
  
 Layout é um conceito central no WPF. Em muitos sistemas, há um conjunto fixo de modelos de layout (o HTML dá suporte a três modelos de layout; fluxo, absoluto e tabelas) ou nenhum modelo de layout (o User32 dá suporte somente a posicionamento absoluto). O WPF começou com a suposição de que desenvolvedores e designers queriam um modelo de layout flexível e extensível, que poderia ser impulsionado por valores de propriedade em vez de lógica imperativa. Ao <xref:System.Windows.UIElement> nível, o contrato básico para layout é <xref:System.Windows.UIElement.Measure%2A> introduzido <xref:System.Windows.UIElement.Arrange%2A> – um modelo de duas fases com e passa.  
  
 <xref:System.Windows.UIElement.Measure%2A>permite que um componente determine quanto tamanho ele gostaria de ter. Esta é uma <xref:System.Windows.UIElement.Arrange%2A> fase separada porque há muitas situações em que um elemento pai pedirá a uma criança para medir várias vezes para determinar sua posição e tamanho ideal. O fato de os elementos parentais pedirem elementos da criança para medir demonstra outra filosofia fundamental do WPF – tamanho ao conteúdo. Todos os controles no WPF suportam a capacidade de dimensionar até o tamanho natural de seu conteúdo. Isso torna a localização muito mais fácil e permite layout dinâmico dos elementos conforme as coisas são redimensionadas. A <xref:System.Windows.UIElement.Arrange%2A> fase permite que um pai se posicione e determine o tamanho final de cada filho.  
  
 Muito tempo é gasto muitas vezes falando sobre <xref:System.Windows.Media.Visual> o lado de saída do WPF – e objetos relacionados. No entanto, também há um tremendo montante de inovação no lado de entrada. Provavelmente a mudança mais fundamental no modelo de entrada para WPF é o modelo consistente pelo qual os eventos de entrada são roteados através do sistema.  
  
 A entrada se origina como um sinal em um driver de dispositivo de modo kernel e é roteada para o processo e thread corretos por um processo intrincado, que envolve o kernel do Windows e o User32. Uma vez que a mensagem User32 correspondente à entrada é roteada para WPF, ela é convertida em uma mensagem de entrada bruta WPF e enviada ao despachante. O WPF permite que eventos de entrada bruta sejam convertidos em vários eventos reais, permitindo que recursos como "MouseEnter" sejam implementados em um nível baixo do sistema com entrega garantida.  
  
 Cada evento de entrada é convertido em pelo menos dois eventos – um evento de "visualização" e o evento real. Todos os eventos no WPF têm uma noção de roteamento através da árvore de elementos. Os eventos são ditos para "bolha" se eles atravessam de um alvo até a árvore até a raiz, e são ditos para "túnel" se eles começam na raiz e atravessam até um alvo. Eventos de visualização de entrada são roteados por túnel, permitindo que qualquer elemento na árvore tenha uma oportunidade de filtrar ou executar uma ação no evento. Os eventos regulares (não visualização) são então roteados por propagação do destino até a raiz.  
  
 Essa divisão entre as fases de túnel e de propagação torna a implementação de recursos como aceleradores de teclado funcionar de forma consistente em um mundo composto. No User32, você poderia implementar aceleradores de teclado tendo uma única tabela global contendo todos os aceleradores aos quais que você quisesse dar suporte (Ctrl + N mapeando para "New"). No dispatcher para seu aplicativo, você chamaria **TranslateAccelerator**, que rastrearia as mensagens de entrada no User32 e determinaria se havia correspondência entre alguma delas e um acelerador registrado. No WPF isso não funcionaria porque o sistema é totalmente "composável" – qualquer elemento pode lidar e usar qualquer acelerador de teclado. Esse modelo de duas fases para a entrada permite que os componentes implementem seu próprio "TranslateAccelerator".  
  
 Para dar um passo <xref:System.Windows.UIElement> adiante, também introduz a noção de Vinculações de Comando. O sistema de comando WPF permite que os desenvolvedores definam a <xref:System.Windows.Input.ICommand>funcionalidade em termos de um ponto final de comando – algo que implementa . Associações de comando permitem a um elemento definir um mapeamento entre um gesto de entrada (Ctrl + N) e um comando (New). Tanto os gestos de entrada quanto as definições de comando são extensíveis e podem ser ligados juntos durante o tempo de uso. Isso torna trivial, por exemplo, permitir que um usuário final personalize as associações de teclas que deseja usar em um aplicativo.  
  
 Até agora no tópico, os recursos "core" do WPF – recursos implementados no conjunto PresentationCore, têm sido o foco. Ao construir o WPF, uma separação limpa entre peças fundamentais (como o contrato de layout <xref:System.Windows.Controls.Grid>com **Medida** e **Arranjo**) e peças de estrutura (como a implementação de um layout específico como ) foi o resultado desejado. A meta era fornecer um ponto de extensibilidade baixo na pilha que permitisse aos desenvolvedores externos criar suas próprias estruturas, se necessário.  
  
<a name="System_Windows_FrameworkElement"></a>
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>pode ser olhado de duas maneiras diferentes. Ele introduz um conjunto de políticas e personalizações nos subsistemas introduzidos em camadas inferiores de WPF. Ele também introduz um conjunto de novos subsistemas.  
  
 A política primária <xref:System.Windows.FrameworkElement> introduzida por é em torno do layout do aplicativo. <xref:System.Windows.FrameworkElement>baseia-se no contrato básico <xref:System.Windows.UIElement> de layout introduzido e adiciona a noção de um "slot" de layout que torna mais fácil para os autores de layout ter um conjunto consistente de semântica de layout orientada por propriedades. Propriedades <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>como <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> , e (para citar alguns) <xref:System.Windows.FrameworkElement> dão a todos os componentes derivados de um comportamento consistente dentro de recipientes de layout.  
  
 <xref:System.Windows.FrameworkElement>também fornece uma exposição mais fácil da API a muitos recursos encontrados nas camadas principais do WPF. Por exemplo, <xref:System.Windows.FrameworkElement> fornece acesso direto <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> à animação através do método. A <xref:System.Windows.Media.Animation.Storyboard> fornece uma maneira de roteirizar várias animações contra um conjunto de propriedades.  
  
 As duas coisas <xref:System.Windows.FrameworkElement> mais críticas que introduz são a vinculação de dados e estilos.  
  
 O subsistema de vinculação de dados no WPF deve ser relativamente [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]familiar para qualquer um que tenha usado o Windows Forms ou ASP.NET para criar um aplicativo . Em cada um desses sistemas, há uma maneira simples de expressar se você deseja que uma ou mais propriedades de um determinado elemento seja associada a uma parte dos dados. O WPF tem suporte total para vinculação de propriedades, transformação e vinculação de listas.  
  
 Uma das características mais interessantes da vinculação de dados no WPF é a introdução de modelos de dados. Modelos de dados permitem que você especifique declarativamente como uma parte dos dados deve ser visualizada. Em vez de criar uma interface do usuário personalizada que pode ser associada a dados, você pode inverter o problema e permitir que os dados determinem a exibição que será criada.  
  
 Definição de estilo é na verdade uma forma leve de associação de dados. Usando estilização, você pode associar um conjunto de propriedades de uma definição compartilhada a uma ou mais instâncias de um elemento. Os estilos são aplicados a um elemento <xref:System.Windows.FrameworkElement.Style%2A> por referência explícita (definindo a propriedade) ou implicitamente associando um estilo com o tipo CLR do elemento.  
  
<a name="System_Windows_Controls_Control"></a>
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 O recurso mais significativo do controle é a modelagem. Se você pensar sobre o sistema de composição do WPF como um sistema de renderização de modo retido, a modelagem permitirá que um controle descreva sua renderização de maneira declarativa e parametrizada. A <xref:System.Windows.Controls.ControlTemplate> não é nada mais do que um script para criar um conjunto de elementos infantis, com vinculações às propriedades oferecidas pelo controle.  
  
 <xref:System.Windows.Controls.Control>fornece um conjunto de <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.Background%2A>propriedades <xref:System.Windows.Controls.Control.Padding%2A>de estoque, para citar alguns, que os autores de modelos podem usar para personalizar a exibição de um controle. A implementação de um controle oferece um modelo de dados e um modelo de interação. O modelo de interação define um conjunto de comandos (como Close para uma janela) e associações para gestos de entrada (como clicar no X vermelho no canto superior da janela). O modelo de dados fornece um conjunto de propriedades para personalizar o modelo de interação ou então personalizar a exibição (determinado pelo modelo).  
  
 Essa divisão entre o modelo de dados (propriedades), o modelo de interação (comandos e eventos) e o modelo de exibição (modelos) permite a completa personalização da aparência e comportamento de um controle.  
  
 Um aspecto comum do modelo de dados dos controles é o modelo de conteúdo. Se você olhar para <xref:System.Windows.Controls.Button>um controle como, você verá que ele <xref:System.Object>tem uma propriedade chamada "Conteúdo" do tipo . No Windows Forms e ASP.NET, essa propriedade normalmente seria uma string – no entanto, isso limita o tipo de conteúdo que você pode colocar em um botão. O conteúdo de um botão pode ser uma cadeia de caracteres simples, um objeto de dados complexo ou uma árvore de elementos inteira. No caso de um objeto de dados, o modelo de dados é usado para construir uma exibição.  
  
<a name="Summary"></a>
## <a name="summary"></a>Resumo  
 O WPF foi projetado para permitir que você crie sistemas de apresentação dinâmicos e baseados em dados. Cada parte do sistema foi projetada para criar objetos através de conjuntos de propriedades que controlam o comportamento. A associação de dados é uma parte fundamental do sistema e está integrada em todas as camadas.  
  
 Aplicativos tradicionais criam uma exibição e, em seguida, associam a alguns dados. No WPF, tudo sobre o controle, cada aspecto do display, é gerado por algum tipo de vinculação de dados. O texto encontrado em um botão é exibido por meio da criação de um controle composto dentro do botão e da associação de sua exibição à propriedade de conteúdo do botão.  
  
 Quando você começa a desenvolver aplicações baseadas em WPF, deve se sentir muito familiar. Você pode definir propriedades, usar objetos e dados se ligam da mesma forma que você pode usar formulários do Windows ou ASP.NET. Com uma investigação mais profunda sobre a arquitetura do WPF, você verá que existe a possibilidade de criar aplicativos muito mais ricos que tratam fundamentalmente os dados como o principal driver do aplicativo.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Layout](layout.md)
- [Visão geral da animação](../graphics-multimedia/animation-overview.md)
