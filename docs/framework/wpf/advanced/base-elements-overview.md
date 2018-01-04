---
title: "Visão geral de elementos base"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52f0bb90d7eb61a199097813eb8313cd9c154f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="base-elements-overview"></a>Visão geral de elementos base
Um alto percentual de classes em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] são derivadas de quatro classes que são normalmente referenciadas no [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] documentação como classes de elemento base. Essas classes são <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, e <xref:System.Windows.FrameworkContentElement>. O <xref:System.Windows.DependencyObject> classe também é relacionada, pois é uma classe base comum de ambos <xref:System.Windows.UIElement> e<xref:System.Windows.ContentElement>  
 
  
<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>APIs de elemento base nas Classes do WPF  
 Ambos <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement> são derivados de <xref:System.Windows.DependencyObject>, por meio de caminhos um pouco diferentes. A divisão nesse nível lida com como um <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> são usados em uma interface do usuário e que finalidade servem em um aplicativo. <xref:System.Windows.UIElement>também tem <xref:System.Windows.Media.Visual> na sua hierarquia de classe, que é uma classe que expõe o suporte gráfico de baixo nível subjacente a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual>Fornece uma estrutura de renderização definindo regiões retangulares de tela independentes. Na prática, <xref:System.Windows.UIElement> é para elementos que darão suporte a um modelo de objeto maior, servem para renderização e layout em áreas que podem ser descritas como regiões retangulares de tela, e onde o modelo de conteúdo é deliberadamente mais aberto, para permitir diferentes combinações de elementos. <xref:System.Windows.ContentElement>não é derivada de <xref:System.Windows.Media.Visual>; seu modelo é que um <xref:System.Windows.ContentElement> poderia ser consumido por algo, como um leitor ou visualizador que, em seguida, interpretar os elementos e produziria completo <xref:System.Windows.Media.Visual> para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] para consumir. Determinados <xref:System.Windows.UIElement> classes devem ser hosts de conteúdo: elas fornecem hospedagem e renderização para uma ou mais <xref:System.Windows.ContentElement> classes (<xref:System.Windows.Controls.DocumentViewer> é um exemplo de tal classe). <xref:System.Windows.ContentElement>é usado como classe base para elementos com modelos de objeto um pouco menores e que focam em texto, informações ou conteúdo do documento que podem ser hospedados em um <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Nível de Framework e nível de núcleo  
 <xref:System.Windows.UIElement>serve como a classe base para <xref:System.Windows.FrameworkElement>, e <xref:System.Windows.ContentElement> serve como a classe base para <xref:System.Windows.FrameworkContentElement>. A razão para esse outro nível de classes é oferecer suporte a um nível de núcleo do WPF que é separado de um nível de framework do WPF, com essa divisão também existente em como [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] são divididos entre os assemblies PresentationCore e PresentationFramework. O nível da estrutura de WPF apresenta uma solução mais completa para necessidades básicas de aplicativos, incluindo a implementação do Gerenciador de layout para apresentação. O nível de núcleo de WPF oferece uma maneira de usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sem a sobrecarga do assembly adicional. A distinção entre esses níveis muito raramente é importante para cenários mais comuns de desenvolvimento de aplicativo e, em geral você deve pensar a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] como um todo e não a preocupação com a diferença entre o nível de framework de WPF e o nível de núcleo de WPF. Você talvez precise saber sobre as distinções dos níveis se seu projeto de aplicativo optar por substituir quantidades substanciais de funcionalidade de nível de framework WPF, por exemplo se sua solução já tiver suas próprias implementações de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] composição e layout.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Escolher de qual elemento derivar  
 A maneira mais prática para criar uma classe personalizada que estende o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é derivar de uma das classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], da qual você obtém tanto quanto possível da funcionalidade desejada por meio da hierarquia existente. Esta seção lista a funcionalidade que vem com três das classes de elemento mais importantes para ajudá-lo a decidir de qual classe herdar.  
  
 Se você estiver implementando um controle, que é um dos motivos mais comuns para derivar de um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe, você provavelmente deseja derivar de uma classe que seja um controle prático, uma classe base família de controle, ou em menos do <xref:System.Windows.Controls.Control> classe base. Para obter algumas diretrizes e exemplos práticos, consulte [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Se você não estiver criando um controle e precisa derivar de uma classe que é superior na hierarquia, as seções a seguir servirão como um guia para que características são definidas em cada classe base de elemento.  
  
 Se você criar uma classe que deriva de <xref:System.Windows.DependencyObject>, herdam a seguinte funcionalidade:  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A>e <xref:System.Windows.DependencyObject.SetValue%2A> suporte do sistema de propriedade geral e suporte.  
  
-   Capacidade de usar propriedades de dependência e propriedades anexadas que são implementadas como propriedades de dependência.  
  
 Se você criar uma classe que deriva de <xref:System.Windows.UIElement>, herdam a seguinte funcionalidade além fornecida pelo <xref:System.Windows.DependencyObject>:  
  
-   Suporte básico para valores de propriedade animados. Para obter mais informações, consulte [Visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Suporte básico de eventos de entrada e comando. Para obter mais informações, consulte [visão geral de entrada](../../../../docs/framework/wpf/advanced/input-overview.md) e [visão geral do comando](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
-   Métodos virtuais que podem ser substituídos para fornecer informações em um sistema de layout.  
  
 Se você criar uma classe que deriva de <xref:System.Windows.FrameworkElement>, herdam a seguinte funcionalidade além fornecida pelo <xref:System.Windows.UIElement>:  
  
-   Suporte a estilos e storyboards. Para obter mais informações, consulte <xref:System.Windows.Style> e [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
-   Suporte para a vinculação de dados. Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Suporte para referências a recursos dinâmicos. Para obter mais informações, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Suporte à herança de valor da propriedade e outros sinalizadores nos metadados, que ajudam a relatar condições sobre propriedades para serviços do framework, como vinculação de dados, estilos ou a implementação da estrutura de layout. Para obter mais informações, consulte [metadados de propriedade do Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   O conceito de árvore lógica. Para obter mais informações, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
-   Suporte para a implementação de nível de framework WPF prática do sistema de layout, incluindo um <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> substituição que pode detectar alterações em propriedades que influenciam o layout.  
  
 Se você criar uma classe que deriva de <xref:System.Windows.ContentElement>, herdam a seguinte funcionalidade além fornecida pelo <xref:System.Windows.DependencyObject>:  
  
-   Suporte para animações. Para obter mais informações, consulte [Visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Suporte básico de eventos de entrada e comando. Para obter mais informações, consulte [visão geral de entrada](../../../../docs/framework/wpf/advanced/input-overview.md) e [visão geral do comando](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 Se você criar uma classe que deriva de <xref:System.Windows.FrameworkContentElement>, obter a funcionalidade além fornecida por <xref:System.Windows.ContentElement>:  
  
-   Suporte a estilos e storyboards. Para obter mais informações, consulte <xref:System.Windows.Style> e [visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Suporte para a vinculação de dados. Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Suporte para referências a recursos dinâmicos. Para obter mais informações, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Suporte à herança de valor da propriedade e outros sinalizadores nos metadados, que ajudam a relatar condições sobre propriedades para serviços do framework, como a vinculação de dados, estilos ou a implementação da estrutura de layout. Para obter mais informações, consulte [metadados de propriedade do Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Você não herda acesso a modificações no sistema de layout (como <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Implementações do sistema de layout só estão disponíveis em <xref:System.Windows.FrameworkElement>. No entanto, você herda um <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> substituição que pode detectar alterações nas propriedades que influenciam o layout e de relatório para os hosts de conteúdo.  
  
 Modelos de conteúdo estão documentados para uma variedade de classes. O modelo de conteúdo de uma classe é um fator que você deve considerar se você deseja localizar uma classe adequada para derivar dela. Para obter mais informações, consulte [Modelo de conteúdo do WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Outras classes base  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject>fornece suporte para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] threading de modelo e permite que todos os objetos criados para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos a ser associado com um <xref:System.Windows.Threading.Dispatcher>. Mesmo se você não derivar de <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>, ou <xref:System.Windows.Media.Visual>, você deve considerar a derivação de <xref:System.Windows.Threading.DispatcherObject> para obter esse suporte ao modelo de threading. Para obter mais informações, consulte [Modelo de Threading](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
### <a name="visual"></a>Visual  
 <xref:System.Windows.Media.Visual>implementa o conceito de um objeto 2D que geralmente requer apresentação visual em uma região aproximadamente retangular. O processamento real de um <xref:System.Windows.Media.Visual> acontece em outras classes (ele não é auto contido), mas o <xref:System.Windows.Media.Visual> classe fornece um tipo conhecido que é usado pelo processo de renderização em vários níveis. <xref:System.Windows.Media.Visual>implementa o teste de hit, mas ele não expõe eventos que reportam positivos nos testes (estes estão em <xref:System.Windows.UIElement>). Para obter mais informações, consulte [Programação de Camada Visual](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Congelável  
 <xref:System.Windows.Freezable>simula imutabilidade em um objeto mutável, fornecendo os meios para gerar cópias do objeto quando um objeto imutável é necessário ou desejado por razões de desempenho. O <xref:System.Windows.Freezable> tipo fornece uma base comum para determinados elementos gráficos como geometrias e pincéis, bem como animações. Em especial, um <xref:System.Windows.Freezable> não é um <xref:System.Windows.Media.Visual>; ele pode conter propriedades que se tornam subpropriedades quando o <xref:System.Windows.Freezable> é aplicado para preencher um valor de propriedade de outro objeto, e estas subpropriedades podem afetar a renderização. Para obter mais informações, consulte a [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>é um <xref:System.Windows.Freezable> que especificamente adiciona a camada de controle de animação e alguns membros utilitários para que as propriedades de animação no momento podem ser distinguidas de propriedades se classe derivada.  
  
### <a name="control"></a>Controle  
 <xref:System.Windows.Controls.Control>é a classe base para o tipo de objeto que é chamado as vezes de controle ou componente, dependendo da tecnologia. Em geral, as classes de controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são classes que representam um controle de interface do usuário ou participam fortemente da composição de controle diretamente. A principal funcionalidade que <xref:System.Windows.Controls.Control> habilita é modelos de controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Control>  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Arquitetura do WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
