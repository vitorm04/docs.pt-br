---
title: "Visão geral de animações personalizadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb8dcce1d72991a803d8a068f29cd0fe3430fdfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-animations-overview"></a>Visão geral de animações personalizadas
Este tópico descreve como e quando estender o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de animação criando quadros-chave personalizados, classes de animação ou utilizando callback por quadro para contorná-lo.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com os diferentes tipos de animação fornecidos pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações, consulte Visão geral sobre animações de From/To/By a [visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)e o [visão geral de animações de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Porque as classes de animação herdam o <xref:System.Windows.Freezable> classe, você deve estar familiarizado com <xref:System.Windows.Freezable> objetos e como herdar de <xref:System.Windows.Freezable>. Para obter mais informações, consulte a [visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Estendendo o sistema de animação  
 Há várias maneiras de estender o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dependendo do nível de funcionalidade interna que você deseja usar.  Há três pontos principais de extensibilidade no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de animação:  
  
-   Criar um objeto de quadro-chave personalizado herdando de uma da  *\<tipo >*classes de quadro-chave, como <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Essa abordagem utiliza a maior parte da funcionalidade interna do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de animação.  
  
-   Criar sua própria classe de animação herdando de <xref:System.Windows.Media.Animation.AnimationTimeline> ou uma da  *\<tipo >*classes AnimationBase.  
  
-   Use o callback por quadro para gerar animações por quadro. Essa abordagem ignora completamente a animação e o sistema de tempo.  
  
 A tabela a seguir descreve alguns dos cenários para estender o sistema de animação.  
  
|Quando você quiser...|Use essa abordagem|  
|-------------------------|-----------------------|  
|Personalizar a interpolação entre valores de um tipo que tem um correspondente  *\<Tipo>*AnimationUsingKeyFrames|Criar um quadro-chave personalizado. Para obter mais informações, consulte a seção [Criar um quadro de chave personalizada](#createacustomkeyframe).|  
|Personalizar mais do que apenas a interpolação entre valores de um tipo que tem um  *\<Tipo >*Animação correspondente.|Criar uma classe de animação personalizada que herda da classe *\<Tipo>*AnimationBase que corresponde ao tipo que você deseja animar. Para obter mais informações, consulte a seção [Criar uma classe de animação personalizada](#createacustomanimationtype).|  
|Animar um tipo que não tem animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondente|Use um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> ou crie uma classe que herda de <xref:System.Windows.Media.Animation.AnimationTimeline>. Para obter mais informações, consulte a seção [Criar uma classe de animação personalizada](#createacustomanimationtype).|  
|Animar múltiplos objetos com valores que são computados a cada quadro e baseados no último conjunto de interações de objetos|Retorno de chamada de quadro de animação. Para obter mais informações, consulte a seção [Criar um retorno de chamada do uso por quadro](#useperframecallback).|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Criar um quadro-chave personalizado  
 Criar uma classe de quadro-chave personalizado é a maneira mais simples para estender o sistema de animação. Use essa abordagem para um método de interpolação diferente para uma animação de quadro-chave.  Conforme descrito na [Visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), uma animação de quadro-chave utiliza objetos de quadro-chave para gerar seus valores de saída. Cada objeto de quadro-chave realiza três funções:  
  
-   Especifica um valor de destino usando seu <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriedade.  
  
-   Especifica a hora em que esse valor deve ser alcançado usando seu <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriedade.  
  
-   Interpola entre o valor do quadro chave anterior e seu próprio valor implementando o método InterpolateValueCore.  
  
 **Instruções de implementação**  
  
 Derivam da classe *\<Tipo>*KeyFrame abstrata e implementa o método InterpolateValueCore. O método InterpolateValueCore retorna o valor atual do quadro-chave. Ele usa dois parâmetros: o valor do quadro chave anterior e um valor de progresso que varia de 0 a 1. Um progresso de 0 indica o quadro chave começou e um valor de 1 indica que o quadro chave completou e deve retornar o valor especificado pelo seu <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriedade.  
  
 Porque o  *\<tipo >*herdam a classes de quadro-chave de <xref:System.Windows.Freezable> classe, também deverá substituir <xref:System.Windows.Freezable.CreateInstanceCore%2A> para retornar uma nova instância da classe. Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) para obter mais informações.  
  
 Depois de criar sua animação personalizada de *\<Tipo >*KeyFrame, você pode usá-la com o  *\<Tipo>*AnimationUsingKeyFrames para aquele tipo.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Criar uma classe de animação personalizada  
 Criando sua própria animação tipo lhe dá que mais controle sobre como um objeto é animado. Há duas maneiras recomendadas para criar seu próprio tipo de animação: você pode derivar o <xref:System.Windows.Media.Animation.AnimationTimeline> classe ou o  *\<tipo >*classe AnimationBase. Derivar das classes *\<Tipo >*Animação ou *\<Tipo >*AnimationUsingKeyFrames não é recomendado.  
  
### <a name="derive-from-typeanimationbase"></a>Derivar de \<Tipo>AnimationBase  
 Derivar de uma classe *\<Tipo >*AnimationBase é a maneira mais simples de criar um novo tipo de animação. Use esta abordagem quando você deseja criar uma animação nova para o tipo que já tem uma classe *\<Tipo >*AnimationBase correspondente.  
  
 **Instruções de implementação**  
  
 Derivar de uma classe *\<Tipo>*Animação e implementar o método GetCurrentValueCore. O método GetCurrentValueCore retorna o valor atual da animação. Ele usa três parâmetros: um valor inicial sugerido, um valor final sugerido e um <xref:System.Windows.Media.Animation.AnimationClock>, que você pode usar para determinar o progresso da animação.  
  
 Porque o  *\<tipo >*AnimationBase classes herdadas do <xref:System.Windows.Freezable> classe, também deverá substituir <xref:System.Windows.Freezable.CreateInstanceCore%2A> para retornar uma nova instância da classe. Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) para obter mais informações.  
  
 Para obter mais informações, consulte a documentação do método GetCurrentValueCore para a classe *\<Tipo>*AnimationBase para o tipo que você deseja animar. Para obter um exemplo, consulte a [Exemplo de animação personalizada](http://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Abordagens alternativas**  
  
 Se você simplesmente quer mudar como os valores de animação são interpolados, considere derivar de uma classe *\<Tipo>*KeyFrame. O quadro chave que você criar pode ser usado com a classe *\<Tipo >*AnimationUsingKeyFrames correspondente fornecida pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Derivar de AnimationTimeline  
 Derivam o <xref:System.Windows.Media.Animation.AnimationTimeline> classe quando você deseja criar uma animação para um tipo que ainda não tiver uma correspondência [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animação, ou você deseja criar uma animação que não seja fortemente tipada.  
  
 **Instruções de implementação**  
  
 Derivam de <xref:System.Windows.Media.Animation.AnimationTimeline> classe e substituir os seguintes membros:  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A>– Se sua nova classe é concreta, você deve substituir <xref:System.Windows.Freezable.CreateInstanceCore%2A> para retornar uma nova instância da classe.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>– Substitua este método para retornar o valor atual da sua animação. Ele usa três parâmetros: um valor de origem padrão, um valor padrão de destino e um <xref:System.Windows.Media.Animation.AnimationClock>. Use o <xref:System.Windows.Media.Animation.AnimationClock> para obter a hora atual ou o progresso da animação. Você pode optar por usar os valores padrão de origem e destino.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>– Ignorar esta propriedade para indicar se sua animação utiliza o valor de destino padrão especificado pelo <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> método.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>– Substituir essa propriedade para indicar o <xref:System.Type> da saída da sua animação produz.  
  
 Se a classe não usar propriedades de dependência para armazenar seus dados ou requer inicialização extra após a criação, talvez seja necessário substituir métodos adicionais; Consulte a [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) para obter mais informações.  
  
 O paradigma recomendado (usada pelas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animações) é utilizar dois níveis de herança:  
  
1.  Criar um resumo  *\<tipo >*AnimationBase classe que deriva de <xref:System.Windows.Media.Animation.AnimationTimeline>. Essa classe deve substituir o <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> método. Ele também deve introduzir um novo método abstrato, GetCurrentValueCore e substituir <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> para que ele valida os tipos do valor de origem padrão e parâmetros de valor de destino padrão, em seguida, chama GetCurrentValueCore.  
  
2.  Criar outra classe que herda de seu novo  *\<tipo >*classe AnimationBase e substitui o <xref:System.Windows.Freezable.CreateInstanceCore%2A> método, o método GetCurrentValueCore que você introduziu, e o <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> propriedade.  
  
 **Abordagens alternativas**  
  
 Se você quiser animar um tipo que não tem animação correspondente de/para/por ou animação de quadro-chave, considere usar um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Porque é fracamente tipado, um <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pode animar qualquer tipo de valor. A desvantagem dessa abordagem é que <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> oferece suporte apenas a interpolação discreta.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Utilize Chamada por quadro  
 Use esta abordagem quando você precisar ignorar completamente o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Um cenário para essa abordagem é animações de física, na qual em cada animação etapa que uma nova direção ou posição de objetos animados precisa ser recalculada com base no último conjunto de interações de objetos.  
  
 **Instruções de implementação**  
  
 Diferentemente de outras abordagens descritas nesta visão geral, para utilizar callback por quadro você não precisa criar uma classe de quadro-chave ou animação personalizada.  
  
 Em vez disso, você se registrar para o <xref:System.Windows.Media.CompositionTarget.Rendering> evento do objeto que contém os objetos que você deseja animar. Esse método de manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual para o gráfico de cena de composição, o método de manipulador de eventos será chamado.  
  
 Em seu manipulador de evento, realize todos cálculos necessários para a animação em vigor e definir as propriedades dos objetos que você deseja animar com esses valores.  
  
 Para obter a hora de apresentação do quadro atual, o <xref:System.EventArgs> associado com esse evento pode ser convertido como <xref:System.Windows.Media.RenderingEventArgs>, que fornecem um <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> tempo de processamento da propriedade que você pode usar para obter o quadro atual.  
  
 Para obter mais informações, consulte o <xref:System.Windows.Media.CompositionTarget.Rendering> página.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.IKeyFrame>  
 [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Visão geral de animações de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral da animação e do sistema de tempo](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Exemplo de animação personalizada](http://go.microsoft.com/fwlink/?LinkID=159981)
