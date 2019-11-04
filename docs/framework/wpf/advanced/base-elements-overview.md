---
title: Visão geral de elementos base
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 6f8542be5a84a4b8b4cabf594c32d6fdfd3757d2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453770"
---
# <a name="base-elements-overview"></a>Visão geral de elementos base
Um alto percentual de classes em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] são derivadas de quatro classes que são normalmente referenciadas no [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] documentação como classes de elemento base. Essas classes são <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>e <xref:System.Windows.FrameworkContentElement>. A classe <xref:System.Windows.DependencyObject> também está relacionada, porque é uma classe base comum de <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>APIs de elemento base nas Classes do WPF  
 Tanto <xref:System.Windows.UIElement> quanto <xref:System.Windows.ContentElement> derivam de <xref:System.Windows.DependencyObject>, por meio de caminhos um pouco diferentes. A divisão nesse nível lida com o modo como um <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> são usados em uma interface do usuário e qual é a finalidade que eles atendem em um aplicativo. <xref:System.Windows.UIElement> também tem <xref:System.Windows.Media.Visual> em sua hierarquia de classes, que é uma classe que expõe o suporte a gráficos de nível inferior subjacente à [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> fornece uma estrutura de renderização definindo regiões de tela retangulares independentes. Na prática, <xref:System.Windows.UIElement> é para elementos que oferecerão suporte a um modelo de objeto maior, devem ser renderizados e inseridos em regiões que podem ser descritas como regiões de tela retangulares e onde o modelo de conteúdo é deliberadamente mais aberto, para permitir combinações diferentes de elementos. <xref:System.Windows.ContentElement> não deriva de <xref:System.Windows.Media.Visual>; seu modelo é que um <xref:System.Windows.ContentElement> seria consumido por outra coisa, como um leitor ou um visualizador que, em seguida, interpretaria os elementos e produzisse o <xref:System.Windows.Media.Visual> completo para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] consumir. Determinadas classes de <xref:System.Windows.UIElement> devem ser hosts de conteúdo: fornecem a hospedagem e a renderização para uma ou mais classes de <xref:System.Windows.ContentElement> (<xref:System.Windows.Controls.DocumentViewer> é um exemplo dessa classe). <xref:System.Windows.ContentElement> é usado como classe base para elementos com modelos de objeto um pouco menores e que mais abordam o texto, as informações ou o conteúdo do documento que podem ser hospedados em um <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Nível de Framework e nível de núcleo  
 <xref:System.Windows.UIElement> serve como a classe base para <xref:System.Windows.FrameworkElement>e <xref:System.Windows.ContentElement> serve como a classe base para <xref:System.Windows.FrameworkContentElement>. O motivo para esse próximo nível de classes é dar suporte a um nível de núcleo do WPF separado de um nível de estrutura do WPF, com essa divisão também existente em como as APIs são divididas entre os assemblies de PresentationCore e PresentationFramework. O nível da estrutura de WPF apresenta uma solução mais completa para necessidades básicas de aplicativos, incluindo a implementação do Gerenciador de layout para apresentação. O nível de núcleo de WPF oferece uma maneira de usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sem a sobrecarga do assembly adicional. A distinção entre esses níveis raramente é importante para os cenários de desenvolvimento de aplicativos mais comuns e, em geral, você deve considerar as APIs de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como um todo e não se preocupar com a diferença entre o nível do WPF Framework e do WPF core. Você talvez precise saber sobre as distinções dos níveis se seu projeto de aplicativo optar por substituir quantidades substanciais de funcionalidade de nível de framework WPF, por exemplo se sua solução já tiver suas próprias implementações de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] composição e layout.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Escolher de qual elemento derivar  
 A maneira mais prática para criar uma classe personalizada que estende o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é derivar de uma das classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], da qual você obtém tanto quanto possível da funcionalidade desejada por meio da hierarquia existente. Esta seção lista a funcionalidade que vem com três das classes de elemento mais importantes para ajudá-lo a decidir de qual classe herdar.  
  
 Se você estiver implementando um controle, que é, na verdade, um dos motivos mais comuns para derivar de uma classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], provavelmente desejará derivar de uma classe que seja um controle prático, uma classe base da família de controle ou pelo menos da classe base <xref:System.Windows.Controls.Control>. Para obter algumas diretrizes e exemplos práticos, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).  
  
 Se você não estiver criando um controle e precisa derivar de uma classe que é superior na hierarquia, as seções a seguir servirão como um guia para que características são definidas em cada classe base de elemento.  
  
 Se você criar uma classe derivada de <xref:System.Windows.DependencyObject>, herdará a seguinte funcionalidade:  
  
- suporte a <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> e suporte geral ao sistema de propriedades.  
  
- Capacidade de usar propriedades de dependência e propriedades anexadas que são implementadas como propriedades de dependência.  
  
 Se você criar uma classe derivada de <xref:System.Windows.UIElement>, herdará a funcionalidade a seguir, além da fornecida pelo <xref:System.Windows.DependencyObject>:  
  
- Suporte básico para valores de propriedade animados. Para obter mais informações, consulte [Visão geral de animação](../graphics-multimedia/animation-overview.md).  
  
- Suporte básico de eventos de entrada e comando. Para obter mais informações, consulte [visão geral de entrada](input-overview.md) e [visão geral do comando](commanding-overview.md).  
  
- Métodos virtuais que podem ser substituídos para fornecer informações em um sistema de layout.  
  
 Se você criar uma classe derivada de <xref:System.Windows.FrameworkElement>, herdará a funcionalidade a seguir, além da fornecida pelo <xref:System.Windows.UIElement>:  
  
- Suporte a estilos e storyboards. Para obter mais informações, consulte Visão geral de <xref:System.Windows.Style> e [storyboards](../graphics-multimedia/storyboards-overview.md).  
  
- Suporte para a vinculação de dados. Para obter mais informações, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
- Suporte para referências a recursos dinâmicos. Para obter mais informações, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Suporte à herança de valor da propriedade e outros sinalizadores nos metadados, que ajudam a relatar condições sobre propriedades para serviços do framework, como vinculação de dados, estilos ou a implementação da estrutura de layout. Para obter mais informações, consulte [metadados de propriedade do Framework](framework-property-metadata.md).  
  
- O conceito de árvore lógica. Para obter mais informações, consulte [Árvores no WPF](trees-in-wpf.md).  
  
- Suporte para a implementação prática do WPF Framework do sistema de layout, incluindo uma substituição de <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> que pode detectar alterações nas propriedades que influenciam o layout.  
  
 Se você criar uma classe derivada de <xref:System.Windows.ContentElement>, herdará a funcionalidade a seguir, além da fornecida pelo <xref:System.Windows.DependencyObject>:  
  
- Suporte para animações. Para obter mais informações, consulte [Visão geral de animação](../graphics-multimedia/animation-overview.md).  
  
- Suporte básico de eventos de entrada e comando. Para obter mais informações, consulte [visão geral de entrada](input-overview.md) e [visão geral do comando](commanding-overview.md).  
  
 Se você criar uma classe derivada de <xref:System.Windows.FrameworkContentElement>, obterá a funcionalidade a seguir além da fornecida pelo <xref:System.Windows.ContentElement>:  
  
- Suporte a estilos e storyboards. Para obter mais informações, consulte [visão geral](../graphics-multimedia/animation-overview.md)de <xref:System.Windows.Style> e animação.  
  
- Suporte para a vinculação de dados. Para obter mais informações, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
- Suporte para referências a recursos dinâmicos. Para obter mais informações, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Suporte à herança de valor da propriedade e outros sinalizadores nos metadados, que ajudam a relatar condições sobre propriedades para serviços do framework, como a vinculação de dados, estilos ou a implementação da estrutura de layout. Para obter mais informações, consulte [metadados de propriedade do Framework](framework-property-metadata.md).  
  
- Você não herda o acesso às modificações do sistema de layout (como <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). As implementações do sistema de layout só estão disponíveis no <xref:System.Windows.FrameworkElement>. No entanto, você herda uma substituição de <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> que pode detectar alterações nas propriedades que influenciam o layout e as relatam a quaisquer hosts de conteúdo.  
  
 Modelos de conteúdo estão documentados para uma variedade de classes. O modelo de conteúdo de uma classe é um fator que você deve considerar se você deseja localizar uma classe adequada para derivar dela. Para obter mais informações, consulte [Modelo de conteúdo do WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Outras classes base  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> fornece suporte para o modelo de threading de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e permite que todos os objetos criados para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos sejam associados a um <xref:System.Windows.Threading.Dispatcher>. Mesmo que você não derive de <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>ou <xref:System.Windows.Media.Visual>, você deve considerar a derivação de <xref:System.Windows.Threading.DispatcherObject> para obter esse suporte ao modelo de Threading. Para obter mais informações, consulte [Modelo de Threading](threading-model.md).  
  
### <a name="visual"></a>Visual  
 <xref:System.Windows.Media.Visual> implementa o conceito de um objeto 2D que geralmente requer apresentação visual em uma região aproximadamente retangular. A renderização real de um <xref:System.Windows.Media.Visual> ocorre em outras classes (não é independente), mas a classe <xref:System.Windows.Media.Visual> fornece um tipo conhecido que é usado pelos processos de renderização em vários níveis. <xref:System.Windows.Media.Visual> implementa os testes de clique, mas não expõe eventos que relatam positivos de teste de colisão (eles estão em <xref:System.Windows.UIElement>). Para obter mais informações, consulte [Programação de Camada Visual](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Congelável  
 <xref:System.Windows.Freezable> simula a imutabilidade em um objeto mutável fornecendo os meios para gerar cópias do objeto quando um objeto imutável é necessário ou desejado por motivos de desempenho. O tipo de <xref:System.Windows.Freezable> fornece uma base comum para determinados elementos gráficos, como geometrias e pincéis, bem como animações. Notavelmente, um <xref:System.Windows.Freezable> não é um <xref:System.Windows.Media.Visual>; Ele pode conter propriedades que se tornam subpropriedades quando a <xref:System.Windows.Freezable> é aplicada para preencher um valor de propriedade de outro objeto, e essas subpropriedades podem afetar a renderização. Para obter mais informações, consulte a [Visão geral de objetos congeláveis](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> é uma classe derivada <xref:System.Windows.Freezable> que adiciona especificamente a camada de controle de animação e alguns membros do utilitário para que as propriedades animadas no momento possam ser diferenciadas das propriedades não animadas.  
  
### <a name="control"></a>Controle  
 <xref:System.Windows.Controls.Control> é a classe base pretendida para o tipo de objeto que tem várias condições de um controle ou componente, dependendo da tecnologia. Em geral, as classes de controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são classes que representam um controle de interface do usuário ou participam fortemente da composição de controle diretamente. A principal funcionalidade que o <xref:System.Windows.Controls.Control> permite é a modelagem de controle.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Control>
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Visão geral da criação de controle](../controls/control-authoring-overview.md)
- [Arquitetura do WPF](wpf-architecture.md)
