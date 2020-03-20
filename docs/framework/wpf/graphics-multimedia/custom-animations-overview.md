---
title: Visão geral de animações personalizadas
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
ms.openlocfilehash: c5f315992e8ae37bc79602e6986d90e7af591fb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186545"
---
# <a name="custom-animations-overview"></a>Visão geral de animações personalizadas
Este tópico descreve como e quando estender o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de animação criando quadros-chave personalizados, classes de animação ou utilizando callback por quadro para contorná-lo.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de animação fornecidos pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações, consulte Visão geral sobre animações de From/To/By a [visão geral de animações de quadro-chave](key-frame-animations-overview.md)e o [visão geral de animações de caminho](path-animations-overview.md).  
  
 Como as classes de <xref:System.Windows.Freezable> animação herdam <xref:System.Windows.Freezable> da classe, você <xref:System.Windows.Freezable>deve estar familiarizado com objetos e como herdar . Para obter mais informações, consulte a [visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>
## <a name="extending-the-animation-system"></a>Estendendo o sistema de animação  
 Há várias maneiras de estender o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dependendo do nível de funcionalidade interna que você deseja usar.  Há três pontos principais de extensibilidade no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de animação:  
  
- Crie um objeto de quadro-chave personalizado * \< *herdando de uma <xref:System.Windows.Media.Animation.DoubleKeyFrame>das classes Type>KeyFrame, tais como . Essa abordagem utiliza a maior parte da funcionalidade interna do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de animação.  
  
- Crie sua própria classe de <xref:System.Windows.Media.Animation.AnimationTimeline> animação herdando ou uma das * \< *classes Type>AnimationBase.  
  
- Use o callback por quadro para gerar animações por quadro. Essa abordagem ignora completamente a animação e o sistema de tempo.  
  
 A tabela a seguir descreve alguns dos cenários para estender o sistema de animação.  
  
|Quando você quiser...|Use essa abordagem|  
|-------------------------|-----------------------|  
|Personalize a interpolação entre valores de um tipo que tenha um * \<tipo *correspondente>AnimaçãoUsingKeyFrames|Criar um quadro-chave personalizado. Para obter mais informações, consulte a seção [Criar um quadro de chave personalizada](#createacustomkeyframe).|  
|Personalize mais do que apenas a interpolação entre valores de um tipo que tenha um * \<Tipo correspondente>* Animação.|Crie uma classe de animação * \< *personalizada que herda da classe Type>AnimationBase que corresponde ao tipo que você deseja animar. Para obter mais informações, consulte a seção [Criar uma classe de animação personalizada](#createacustomanimationtype).|  
|Animar um tipo que não tem animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondente|Use <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> um ou crie uma <xref:System.Windows.Media.Animation.AnimationTimeline>classe que herde de . Para obter mais informações, consulte a seção [Criar uma classe de animação personalizada](#createacustomanimationtype).|  
|Animar múltiplos objetos com valores que são computados a cada quadro e baseados no último conjunto de interações de objetos|Retorno de chamada de quadro de animação. Para obter mais informações, consulte a seção [Criar um retorno de chamada do uso por quadro](#useperframecallback).|  
  
<a name="createacustomkeyframe"></a>
## <a name="create-a-custom-key-frame"></a>Criar um quadro-chave personalizado  
 Criar uma classe de quadro-chave personalizado é a maneira mais simples para estender o sistema de animação. Use essa abordagem para um método de interpolação diferente para uma animação de quadro-chave.  Conforme descrito na [Visão geral de animações de quadro-chave](key-frame-animations-overview.md), uma animação de quadro-chave utiliza objetos de quadro-chave para gerar seus valores de saída. Cada objeto de quadro-chave realiza três funções:  
  
- Especifica um valor de <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> destino usando sua propriedade.  
  
- Especifica o tempo em que esse valor <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> deve ser atingido usando sua propriedade.  
  
- Interpola entre o valor do quadro chave anterior e seu próprio valor implementando o método InterpolateValueCore.  
  
 **Instruções de implementação**  
  
 Derivar * \< *da classe abstrata Type>KeyFrame e implementar o método InterpolateValueCore. O método InterpolateValueCore retorna o valor atual do quadro-chave. Ele usa dois parâmetros: o valor do quadro chave anterior e um valor de progresso que varia de 0 a 1. Um progresso de 0 indica que o quadro-chave acabou de ser iniciado, e um valor de <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 1 indica que o quadro-chave acabou de ser concluído e deve devolver o valor especificado por sua propriedade.  
  
 Como * \< *as classes Type><xref:System.Windows.Freezable> KeyFrame herdam <xref:System.Windows.Freezable.CreateInstanceCore%2A> da classe, você também deve substituir o núcleo para retornar uma nova instância da sua classe. Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md) para obter mais informações.  
  
 Depois de criar sua animação * \<de Tipo>* KeyFrame personalizada, você pode usá-lo com o * \<Tipo>* AnimaçãoUsandoFrames para esse tipo.  
  
<a name="createacustomanimationtype"></a>
## <a name="create-a-custom-animation-class"></a>Criar uma classe de animação personalizada  
 Criando sua própria animação tipo lhe dá que mais controle sobre como um objeto é animado. Existem duas maneiras recomendadas de criar seu próprio <xref:System.Windows.Media.Animation.AnimationTimeline> tipo de animação: você pode derivar da classe ou da * \< *classe Type>AnimationBase. Não é recomendado o * \<uso *das classes Tipo>Animação ou * \<>de TipoUsingKeyFrames. *  
  
### <a name="derive-from-typeanimationbase"></a>Derivar de \<Tipo>AnimationBase  
 Derivada de * \< *uma classe Type>AnimationBase é a maneira mais simples de criar um novo tipo de animação. Use essa abordagem quando quiser criar uma nova animação para o tipo que já tenha uma classe * \<De tipo>* AnimationBase correspondente.  
  
 **Instruções de implementação**  
  
 Derivar * \< *de uma classe de animação de>tipo e implementar o método GetCurrentValueCore. O método GetCurrentValueCore retorna o valor atual da animação. Ele leva três parâmetros: um valor inicial sugerido, <xref:System.Windows.Media.Animation.AnimationClock>um valor final sugerido e um , que você usa para determinar o progresso da animação.  
  
 Como * \< *as classes Type><xref:System.Windows.Freezable> AnimationBase herdam <xref:System.Windows.Freezable.CreateInstanceCore%2A> da classe, você também deve substituir o núcleo para retornar uma nova instância da sua classe. Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md) para obter mais informações.  
  
 Para obter mais informações, consulte a documentação do método GetCurrentValueCore para a * \< *classe Type>AnimationBase para o tipo que você deseja animar. Para obter um exemplo, consulte a [Exemplo de animação personalizada](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Abordagens Alternativas**  
  
 Se você simplesmente quiser alterar a forma como os valores * \< *de animação são interpolados, considerando a deriva de uma das classes Type>KeyFrame. O quadro-chave criado pode ser usado com o * \<tipo *correspondente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]>animaçãoUsingKeyFrames fornecidos por .  
  
### <a name="derive-from-animationtimeline"></a>Derivar de AnimationTimeline  
 Obtenha da <xref:System.Windows.Media.Animation.AnimationTimeline> classe quando você quiser criar uma animação para um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tipo que ainda não tenha uma animação correspondente, ou você deseja criar uma animação que não seja fortemente digitada.  
  
 **Instruções de implementação**  
  
 Derivar <xref:System.Windows.Media.Animation.AnimationTimeline> da classe e substituir os seguintes membros:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A>– Se sua nova classe for <xref:System.Windows.Freezable.CreateInstanceCore%2A> concreta, você deve substituir para retornar uma nova instância de sua classe.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>– Anular este método para retornar o valor atual da sua animação. Ele leva três parâmetros: um valor de origem <xref:System.Windows.Media.Animation.AnimationClock>padrão, um valor de destino padrão e um . Use <xref:System.Windows.Media.Animation.AnimationClock> o para obter o tempo ou progresso atual para a animação. Você pode optar por usar os valores padrão de origem e destino.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>– Anular essa propriedade para indicar se sua animação usa <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> o valor de destino padrão especificado pelo método.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>– Anular esta propriedade <xref:System.Type> para indicar a saída que sua animação produz.  
  
 Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md) para obter mais informações.  
  
 O paradigma recomendado (usada pelas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animações) é utilizar dois níveis de herança:  
  
1. Crie uma classe * \<de tipo>* <xref:System.Windows.Media.Animation.AnimationTimeline>animação de tipo abstrato que deriva de . Esta classe deve <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> substituir o método. Ele também deve introduzir um novo método abstrato, GetCurrentValueCore e substituir para <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> que ele valide os tipos do valor de origem padrão e parâmetros de valor de destino padrão e, em seguida, chama GetCurrentValueCore.  
  
2. Crie outra classe que herda da nova classe * \<Type>* AnimationBase e substitui o <xref:System.Windows.Freezable.CreateInstanceCore%2A> método, <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> o método GetCurrentValueCore que você introduziu e a propriedade.  
  
 **Abordagens Alternativas**  
  
 Se você quiser animar um tipo que não tenha animação de/para/por/por <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>animação ou quadro-chave, considere usar um . Por ser mal digitado, pode <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> animar qualquer tipo de valor. A desvantagem dessa <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> abordagem é que só suporta interpolação discreta.  
  
<a name="useperframecallback"></a>
## <a name="use-per-frame-callback"></a>Utilize Chamada por quadro  
 Use esta abordagem quando você precisar ignorar completamente o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Um cenário para essa abordagem é animações de física, na qual em cada animação etapa que uma nova direção ou posição de objetos animados precisa ser recalculada com base no último conjunto de interações de objetos.  
  
 **Instruções de implementação**  
  
 Diferentemente de outras abordagens descritas nesta visão geral, para utilizar callback por quadro você não precisa criar uma classe de quadro-chave ou animação personalizada.  
  
 Em vez disso, <xref:System.Windows.Media.CompositionTarget.Rendering> você se registra para o evento do objeto que contém os objetos que você deseja animar. Esse método do manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual para o gráfico de cena de composição, o método de manipulador de eventos será chamado.  
  
 Em seu manipulador de evento, realize todos cálculos necessários para a animação em vigor e definir as propriedades dos objetos que você deseja animar com esses valores.  
  
 Para obter o tempo de apresentação <xref:System.EventArgs> do quadro atual, <xref:System.Windows.Media.RenderingEventArgs>o associado <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> a este evento pode ser moldado como , que fornece uma propriedade que você pode usar para obter o tempo de renderização do quadro atual.  
  
 Para saber mais, veja a página <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md)
- [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Visão geral de animações de caminho](path-animations-overview.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md)
- [Exemplo de animação personalizada](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
