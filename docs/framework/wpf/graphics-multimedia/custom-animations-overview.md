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
ms.openlocfilehash: 5a9ca51b87f73a24b90d0bd843ee306f8a1b970a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453085"
---
# <a name="custom-animations-overview"></a>Visão geral de animações personalizadas
Este tópico descreve como e quando estender o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de animação criando quadros-chave personalizados, classes de animação ou utilizando callback por quadro para contorná-lo.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de animação fornecidos pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações, consulte Visão geral sobre animações de From/To/By a [visão geral de animações de quadro-chave](key-frame-animations-overview.md)e o [visão geral de animações de caminho](path-animations-overview.md).  
  
 Como as classes de animação herdam da classe <xref:System.Windows.Freezable>, você deve estar familiarizado com <xref:System.Windows.Freezable> objetos e como herdar de <xref:System.Windows.Freezable>. Para obter mais informações, consulte a [visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Estendendo o sistema de animação  
 Há várias maneiras de estender o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dependendo do nível de funcionalidade interna que você deseja usar.  Há três pontos principais de extensibilidade no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de animação:  
  
- Crie um objeto de quadro de chave personalizado herdando de um dos *\<tipo >* classes de quadro-chave, como <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Essa abordagem utiliza a maior parte da funcionalidade interna do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de animação.  
  
- Crie sua própria classe de animação herdando de <xref:System.Windows.Media.Animation.AnimationTimeline> ou de uma das classes *\<tipo >* AnimationBase.  
  
- Use o callback por quadro para gerar animações por quadro. Essa abordagem ignora completamente a animação e o sistema de tempo.  
  
 A tabela a seguir descreve alguns dos cenários para estender o sistema de animação.  
  
|Quando você quiser...|Use essa abordagem|  
|-------------------------|-----------------------|  
|Personalizar a interpolação entre valores de um tipo que tem um correspondente *\<Tipo>* AnimationUsingKeyFrames|Criar um quadro-chave personalizado. Para obter mais informações, consulte a seção [Criar um quadro de chave personalizada](#createacustomkeyframe).|  
|Personalizar mais do que apenas a interpolação entre valores de um tipo que tem um *\<Tipo >* Animação correspondente.|Criar uma classe de animação personalizada que herda da classe *\<Tipo>* AnimationBase que corresponde ao tipo que você deseja animar. Para obter mais informações, consulte a seção [Criar uma classe de animação personalizada](#createacustomanimationtype).|  
|Animar um tipo que não tem animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondente|Use um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> ou crie uma classe que herda de <xref:System.Windows.Media.Animation.AnimationTimeline>. Para obter mais informações, consulte a seção [Criar uma classe de animação personalizada](#createacustomanimationtype).|  
|Animar múltiplos objetos com valores que são computados a cada quadro e baseados no último conjunto de interações de objetos|Retorno de chamada de quadro de animação. Para obter mais informações, consulte a seção [Criar um retorno de chamada do uso por quadro](#useperframecallback).|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Criar um quadro-chave personalizado  
 Criar uma classe de quadro-chave personalizado é a maneira mais simples para estender o sistema de animação. Use essa abordagem para um método de interpolação diferente para uma animação de quadro-chave.  Conforme descrito na [Visão geral de animações de quadro-chave](key-frame-animations-overview.md), uma animação de quadro-chave utiliza objetos de quadro-chave para gerar seus valores de saída. Cada objeto de quadro-chave realiza três funções:  
  
- Especifica um valor de destino usando sua propriedade <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
- Especifica a hora em que esse valor deve ser alcançado usando sua propriedade <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  
  
- Interpola entre o valor do quadro chave anterior e seu próprio valor implementando o método InterpolateValueCore.  
  
 **Instruções de implementação**  
  
 Derivam da classe *\<Tipo>* KeyFrame abstrata e implementa o método InterpolateValueCore. O método InterpolateValueCore retorna o valor atual do quadro-chave. Ele usa dois parâmetros: o valor do quadro chave anterior e um valor de progresso que varia de 0 a 1. Um progresso de 0 indica que o quadro-chave acabou de ser iniciado e um valor de 1 indica que o quadro de chave acabou de ser concluído e deve retornar o valor especificado por sua propriedade <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
 Como o *tipo de\<>* classes de quadro-chave herdam da classe <xref:System.Windows.Freezable>, você também deve substituir <xref:System.Windows.Freezable.CreateInstanceCore%2A> Core para retornar uma nova instância da sua classe. Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md) para obter mais informações.  
  
 Depois de criar sua animação personalizada de *\<Tipo >* KeyFrame, você pode usá-la com o *\<Tipo>* AnimationUsingKeyFrames para aquele tipo.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Criar uma classe de animação personalizada  
 Criando sua própria animação tipo lhe dá que mais controle sobre como um objeto é animado. Há duas maneiras recomendadas de criar seu próprio tipo de animação: você pode derivar da classe <xref:System.Windows.Media.Animation.AnimationTimeline> ou da classe *\<tipo >* AnimationBase. Derivar das classes *\<Tipo >* Animação ou *\<Tipo >* AnimationUsingKeyFrames não é recomendado.  
  
### <a name="derive-from-typeanimationbase"></a>Derivar de \<Tipo>AnimationBase  
 Derivar de uma classe *\<Tipo >* AnimationBase é a maneira mais simples de criar um novo tipo de animação. Use esta abordagem quando você deseja criar uma animação nova para o tipo que já tem uma classe *\<Tipo >* AnimationBase correspondente.  
  
 **Instruções de implementação**  
  
 Derivar de uma classe *\<Tipo>* Animação e implementar o método GetCurrentValueCore. O método GetCurrentValueCore retorna o valor atual da animação. São necessários três parâmetros: um valor inicial sugerido, um valor final sugerido e um <xref:System.Windows.Media.Animation.AnimationClock>, que você usa para determinar o progresso da animação.  
  
 Como o *tipo de\<>* as classes AnimationBase herdam da classe <xref:System.Windows.Freezable>, você também deve substituir <xref:System.Windows.Freezable.CreateInstanceCore%2A> Core para retornar uma nova instância da sua classe. Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md) para obter mais informações.  
  
 Para obter mais informações, consulte a documentação do método GetCurrentValueCore para a classe *\<Tipo>* AnimationBase para o tipo que você deseja animar. Para obter um exemplo, consulte a [Exemplo de animação personalizada](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Abordagens alternativas**  
  
 Se você simplesmente quer mudar como os valores de animação são interpolados, considere derivar de uma classe *\<Tipo>* KeyFrame. O quadro chave que você criar pode ser usado com a classe *\<Tipo >* AnimationUsingKeyFrames correspondente fornecida pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Derivar de AnimationTimeline  
 Derive da classe <xref:System.Windows.Media.Animation.AnimationTimeline> quando desejar criar uma animação para um tipo que ainda não tem uma animação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondente ou que você deseja criar uma animação que não tenha rigidez de tipos.  
  
 **Instruções de implementação**  
  
 Derive da classe <xref:System.Windows.Media.Animation.AnimationTimeline> e substitua os seguintes membros:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A> – se sua nova classe for concreta, você deverá substituir <xref:System.Windows.Freezable.CreateInstanceCore%2A> para retornar uma nova instância da sua classe.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – Substitua esse método para retornar o valor atual da sua animação. São necessários três parâmetros: um valor de origem padrão, um valor de destino padrão e um <xref:System.Windows.Media.Animation.AnimationClock>. Use a <xref:System.Windows.Media.Animation.AnimationClock> para obter a hora atual ou o andamento da animação. Você pode optar por usar os valores padrão de origem e destino.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – Substitua essa propriedade para indicar se sua animação usa o valor de destino padrão especificado pelo método <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – Substitua essa propriedade para indicar a <xref:System.Type> de saída que sua animação produz.  
  
 Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../advanced/freezable-objects-overview.md) para obter mais informações.  
  
 O paradigma recomendado (usada pelas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animações) é utilizar dois níveis de herança:  
  
1. Crie um *tipo de\<abstrato >* classe AnimationBase que deriva de <xref:System.Windows.Media.Animation.AnimationTimeline>. Essa classe deve substituir o método <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>. Ele também deve introduzir um novo método abstrato, GetCurrentValueCore e substituir <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> para que ele valide os tipos do valor de origem padrão e os parâmetros de valor de destino padrão e, em seguida, chame GetCurrentValueCore.  
  
2. Crie outra classe que herda de sua nova *\<tipo >* AnimationBase e substitui o método <xref:System.Windows.Freezable.CreateInstanceCore%2A>, o método GetCurrentValueCore que você introduziu e a propriedade <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>.  
  
 **Abordagens alternativas**  
  
 Se você quiser animar um tipo que não corresponde à animação de/para/por ou animação de quadro chave, considere usar um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Como ele é de tipo fraco, um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pode animar qualquer tipo de valor. A desvantagem dessa abordagem é que <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> só dá suporte à interpolação discreta.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Utilize Chamada por quadro  
 Use esta abordagem quando você precisar ignorar completamente o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Um cenário para essa abordagem é animações de física, na qual em cada animação etapa que uma nova direção ou posição de objetos animados precisa ser recalculada com base no último conjunto de interações de objetos.  
  
 **Instruções de implementação**  
  
 Diferentemente de outras abordagens descritas nesta visão geral, para utilizar callback por quadro você não precisa criar uma classe de quadro-chave ou animação personalizada.  
  
 Em vez disso, registre-se para o evento <xref:System.Windows.Media.CompositionTarget.Rendering> do objeto que contém os objetos que você deseja animar. Esse método do manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual ao longo da árvore de composição, o método do manipulador de eventos será chamado.  
  
 Em seu manipulador de evento, realize todos cálculos necessários para a animação em vigor e definir as propriedades dos objetos que você deseja animar com esses valores.  
  
 Para obter a hora da apresentação do quadro atual, o <xref:System.EventArgs> associado a esse evento pode ser convertido como <xref:System.Windows.Media.RenderingEventArgs>, que fornece uma propriedade <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> que você pode usar para obter o tempo de renderização do quadro atual.  
  
 Para obter mais informações, consulte a página <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
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
