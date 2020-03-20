---
title: Visão geral de elementos base
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 7d52d951d4fa4df83bbcca6b4cb479e18e532d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141622"
---
# <a name="base-elements-overview"></a>Visão geral de elementos base
Uma alta porcentagem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de classes são derivadas de quatro classes que são comumente referidas na documentação SDK como as classes de elemento base. Essas aulas <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement>são, <xref:System.Windows.ContentElement> <xref:System.Windows.FrameworkContentElement>e . A <xref:System.Windows.DependencyObject> classe também está relacionada, porque é <xref:System.Windows.UIElement> uma classe de base comum de ambos e<xref:System.Windows.ContentElement>  

<a name="base_apis"></a>
## <a name="base-element-apis-in-wpf-classes"></a>APIs de elemento base nas Classes do WPF  
 Ambos <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> e são <xref:System.Windows.DependencyObject>derivados de , através de caminhos um pouco diferentes. A divisão neste nível <xref:System.Windows.UIElement> trata <xref:System.Windows.ContentElement> de como um ou são usados em uma interface de usuário e que propósito eles servem em um aplicativo. <xref:System.Windows.UIElement>também <xref:System.Windows.Media.Visual> tem em sua hierarquia de classe, que é uma classe que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]expõe o suporte gráfico de nível inferior subjacente ao . <xref:System.Windows.Media.Visual>fornece uma estrutura de renderização definindo regiões independentes de tela retangular. Na prática, <xref:System.Windows.UIElement> é para elementos que suportam um modelo de objeto maior, destinam-se a renderizar e layout em regiões que podem ser descritas como regiões de tela retangulares, e onde o modelo de conteúdo é deliberadamente mais aberto, para permitir diferentes combinações de elementos. <xref:System.Windows.ContentElement>não deriva <xref:System.Windows.Media.Visual>de; seu modelo é <xref:System.Windows.ContentElement> que um seria consumido por outra coisa, como um leitor ou <xref:System.Windows.Media.Visual> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] espectador que então interpretaria os elementos e produziria o completo para consumir. Certas <xref:System.Windows.UIElement> classes destinam-se a ser hosts de conteúdo: <xref:System.Windows.ContentElement> eles<xref:System.Windows.Controls.DocumentViewer> fornecem a hospedagem e a renderização para uma ou mais classes (é um exemplo de tal classe). <xref:System.Windows.ContentElement>é usado como classe base para elementos com modelos de objetos um pouco menores e <xref:System.Windows.UIElement>que mais abordam o conteúdo de texto, informação ou documento que pode ser hospedado dentro de um .  
  
### <a name="framework-level-and-core-level"></a>Nível de Framework e nível de núcleo  
 <xref:System.Windows.UIElement>serve como a <xref:System.Windows.FrameworkElement>classe <xref:System.Windows.ContentElement> base para , <xref:System.Windows.FrameworkContentElement>e serve como a classe base para . A razão para este próximo nível de classes é suportar um nível de núcleo WPF separado de um nível de estrutura WPF, com essa divisão também existente na forma como as APIs são divididas entre as assembléias PresentationCore e PresentationFramework. O nível da estrutura de WPF apresenta uma solução mais completa para necessidades básicas de aplicativos, incluindo a implementação do Gerenciador de layout para apresentação. O nível de núcleo de WPF oferece uma maneira de usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sem a sobrecarga do assembly adicional. A distinção entre esses níveis raramente importa para a maioria dos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cenários típicos de desenvolvimento de aplicativos, e em geral você deve pensar nas APIs como um todo e não se preocupar com a diferença entre o nível de estrutura do WPF e o nível central do WPF. Você talvez precise saber sobre as distinções dos níveis se seu projeto de aplicativo optar por substituir quantidades substanciais de funcionalidade de nível de framework WPF, por exemplo se sua solução já tiver suas próprias implementações de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] composição e layout.  
  
<a name="subclassing_elements"></a>
## <a name="choosing-which-element-to-derive-from"></a>Escolher de qual elemento derivar  
 A maneira mais prática para criar uma classe personalizada que estende o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é derivar de uma das classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], da qual você obtém tanto quanto possível da funcionalidade desejada por meio da hierarquia existente. Esta seção lista a funcionalidade que vem com três das classes de elemento mais importantes para ajudá-lo a decidir de qual classe herdar.  
  
 Se você está implementando um controle, que é realmente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uma das razões mais comuns para derivar de uma classe, você provavelmente quer derivar de uma classe que é um controle prático, uma classe de base de controle familiar, ou pelo menos da classe <xref:System.Windows.Controls.Control> base. Para obter algumas diretrizes e exemplos práticos, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).  
  
 Se você não estiver criando um controle e precisa derivar de uma classe que é superior na hierarquia, as seções a seguir servirão como um guia para que características são definidas em cada classe base de elemento.  
  
 Se você criar uma classe <xref:System.Windows.DependencyObject>derivada, você herda rá a seguinte funcionalidade:  
  
- <xref:System.Windows.DependencyObject.GetValue%2A>e <xref:System.Windows.DependencyObject.SetValue%2A> suporte, e suporte geral do sistema de propriedade.  
  
- Capacidade de usar propriedades de dependência e propriedades anexadas que são implementadas como propriedades de dependência.  
  
 Se você criar uma classe <xref:System.Windows.UIElement>derivada, você herda a seguinte <xref:System.Windows.DependencyObject>funcionalidade, além da fornecida por :  
  
- Suporte básico para valores de propriedade animados. Para obter mais informações, consulte [Visão geral da animação](../graphics-multimedia/animation-overview.md).  
  
- Suporte básico de eventos de entrada e comando. Para obter mais informações, consulte [visão geral de entrada](input-overview.md) e [visão geral do comando](commanding-overview.md).  
  
- Métodos virtuais que podem ser substituídos para fornecer informações em um sistema de layout.  
  
 Se você criar uma classe <xref:System.Windows.FrameworkElement>derivada, você herda a seguinte <xref:System.Windows.UIElement>funcionalidade, além da fornecida por :  
  
- Suporte a estilos e storyboards. Para obter mais <xref:System.Windows.Style> informações, consulte e [Storyboards Overview](../graphics-multimedia/storyboards-overview.md).  
  
- Suporte para a vinculação de dados. Para obter mais informações, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
- Suporte para referências a recursos dinâmicos. Para obter mais informações, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Suporte à herança de valor da propriedade e outros sinalizadores nos metadados, que ajudam a relatar condições sobre propriedades para serviços do framework, como vinculação de dados, estilos ou a implementação da estrutura de layout. Para obter mais informações, consulte [metadados de propriedade do Framework](framework-property-metadata.md).  
  
- O conceito de árvore lógica. Para obter mais informações, consulte [Árvores no WPF](trees-in-wpf.md).  
  
- Suporte para a implementação prática do nível de <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> estrutura wpf do sistema de layout, incluindo uma substituição que pode detectar alterações nas propriedades que influenciam o layout.  
  
 Se você criar uma classe <xref:System.Windows.ContentElement>derivada, você herda a seguinte <xref:System.Windows.DependencyObject>funcionalidade, além da fornecida por :  
  
- Suporte para animações. Para obter mais informações, consulte [Visão geral da animação](../graphics-multimedia/animation-overview.md).  
  
- Suporte básico de eventos de entrada e comando. Para obter mais informações, consulte [visão geral de entrada](input-overview.md) e [visão geral do comando](commanding-overview.md).  
  
 Se você criar uma classe <xref:System.Windows.FrameworkContentElement>que deriva, você obtém a seguinte <xref:System.Windows.ContentElement>funcionalidade, além da fornecida por :  
  
- Suporte a estilos e storyboards. Para obter mais <xref:System.Windows.Style> informações, consulte e [visão geral da animação](../graphics-multimedia/animation-overview.md).  
  
- Suporte para a vinculação de dados. Para obter mais informações, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).  
  
- Suporte para referências a recursos dinâmicos. Para obter mais informações, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Suporte à herança de valor da propriedade e outros sinalizadores nos metadados, que ajudam a relatar condições sobre propriedades para serviços do framework, como a vinculação de dados, estilos ou a implementação da estrutura de layout. Para obter mais informações, consulte [metadados de propriedade do Framework](framework-property-metadata.md).  
  
- Você não herda o acesso a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>modificações do sistema de layout (como ). As implementações do sistema <xref:System.Windows.FrameworkElement>de layout só estão disponíveis em . No entanto, <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> você herda uma substituição que pode detectar alterações nas propriedades que influenciam o layout e reportá-las a quaisquer hosts de conteúdo.  
  
 Modelos de conteúdo estão documentados para uma variedade de classes. O modelo de conteúdo de uma classe é um fator que você deve considerar se você deseja localizar uma classe adequada para derivar dela. Para obter mais informações, consulte [Modelo de conteúdo do WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>
## <a name="other-base-classes"></a>Outras classes base  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject>fornece suporte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para o modelo de rosca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e permite que <xref:System.Windows.Threading.Dispatcher>todos os objetos criados para aplicativos sejam associados a um . Mesmo que você não <xref:System.Windows.UIElement> <xref:System.Windows.DependencyObject>deseme de , <xref:System.Windows.Media.Visual>ou <xref:System.Windows.Threading.DispatcherObject> , você deve considerar derivar a fim de obter este suporte modelo de rosca. Para obter mais informações, consulte [Modelo de Threading](threading-model.md).  
  
### <a name="visual"></a>Visual  
 <xref:System.Windows.Media.Visual>implementa o conceito de um objeto 2D que geralmente requer apresentação visual em uma região aproximadamente retangular. A renderização <xref:System.Windows.Media.Visual> real de um acontece em outras classes <xref:System.Windows.Media.Visual> (não é auto-contida), mas a classe fornece um tipo conhecido que é usado por processos de renderização em vários níveis. <xref:System.Windows.Media.Visual>implementa testes de hit, mas não expõe eventos que relatam positivos <xref:System.Windows.UIElement>de teste de hit (estes estão em ). Para obter mais informações, consulte [Programação de Camada Visual](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Congelável  
 <xref:System.Windows.Freezable>simula imutabilidade em um objeto mutável, fornecendo os meios para gerar cópias do objeto quando um objeto imutável é necessário ou desejado por razões de desempenho. O <xref:System.Windows.Freezable> tipo fornece uma base comum para certos elementos gráficos, como geometrias e pincéis, bem como animações. Notavelmente, <xref:System.Windows.Freezable> a não <xref:System.Windows.Media.Visual>é um; ele pode conter propriedades que <xref:System.Windows.Freezable> se tornam subpropriedades quando a é aplicada para preencher um valor de propriedade de outro objeto, e essas subpropriedades podem afetar a renderização. Para obter mais informações, consulte a [Visão geral de objetos congeláveis](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>é <xref:System.Windows.Freezable> uma classe derivada que adiciona especificamente a camada de controle de animação e alguns membros do utilitário para que as propriedades atualmente animadas possam ser distinguidas de propriedades não animadas.  
  
### <a name="control"></a>Control  
 <xref:System.Windows.Controls.Control>é a classe base destinada para o tipo de objeto que é várias das formas denominadas de controle ou componente, dependendo da tecnologia. Em geral, as classes de controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são classes que representam um controle de interface do usuário ou participam fortemente da composição de controle diretamente. A principal funcionalidade <xref:System.Windows.Controls.Control> que permite é o controle de templating.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.Control>
- [Visão geral das propriedades de dependência](dependency-properties-overview.md)
- [Visão geral da criação de controle](../controls/control-authoring-overview.md)
- [Arquitetura do WPF](wpf-architecture.md)
