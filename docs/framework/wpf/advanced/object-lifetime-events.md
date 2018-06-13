---
title: Eventos de tempo de vida do objeto
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: 02a6736fe54be4683044f648e9d5ed5e8a3d95dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547528"
---
# <a name="object-lifetime-events"></a>Eventos de tempo de vida do objeto
Este tópico descreve os eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] específicos que indicam os estágios de criação, uso e destruição no tempo de vida do objeto.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você entenda as propriedades de dependência da perspectiva de um consumidor das propriedades de dependência existentes em classes do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e que leu o tópico [Visão geral das propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Para seguir os exemplos deste tópico, você também deve compreender [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (consulte [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)) e saber como escrever aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Eventos de tempo de vida do objeto  
 Todos os objetos no código gerenciado do Microsoft .NET Framework passam por um conjunto similar de estágios de vida, criação, use e destruição. Muitos objetos têm um estágio de vida de finalização que ocorre como parte da fase de destruição. Objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais especificamente os objetos visuais que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifica como elementos, também têm um conjunto de estágios comuns de vida útil do objeto. Os modelos de programação e aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expõem esses estágios como uma série de eventos. Há quatro tipos principais de objetos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com relação a eventos de tempo de vida; elementos em geral, elementos de janela, hosts de navegação e objetos de aplicativo. Janelas e hosts de navegação também estão no agrupamento maior de objetos visuais (elementos). Este tópico descreve os eventos de tempo de vida que são comuns a todos os elementos e, em seguida, apresenta os mais específicos que se aplicam a definições de aplicativo, janelas ou hosts de navegação.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Eventos de tempo de vida comuns aos elementos  
 Qualquer elemento de nível de framework do WPF (esses objetos derivados do <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>) tem três eventos comuns de tempo de vida: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, e <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Inicializado  
 <xref:System.Windows.FrameworkElement.Initialized> é gerado pela primeira vez e aproximadamente corresponde a inicialização do objeto pela chamada para o construtor. Como o evento ocorre em resposta à inicialização, há a garantia de que todas as propriedades do objeto são definidas. (Uma exceção são os usos de expressões como recursos dinâmicos ou associação; elas serão expressões não avaliadas). Como consequência o requisito de que todas as propriedades são definidas, a sequência de <xref:System.Windows.FrameworkElement.Initialized> sendo gerados pelos elementos aninhados são definidos na marcação parecem ocorrer primeiro, na ordem dos elementos de nível mais profundos na árvore do elemento pai, em seguida, os elementos à raiz. Essa ordem ocorre porque as relações de pai e filho e o confinamento são propriedades e, portanto, o pai não pode relatar a inicialização até que os elementos filho que preenchem a propriedade também sejam inicializados completamente.  
  
 Quando você está escrevendo manipuladores em resposta ao <xref:System.Windows.FrameworkElement.Initialized> evento, você deve considerar se não há nenhuma garantia de que todos os outros elementos na árvore de elementos (árvore lógica ou árvore visual) em torno de onde o manipulador é anexado foram criados, particularmente elementos pai. Variáveis de membro podem ser nulas ou fontes de dados podem ainda não ter sido preenchidas pela associação subjacente (mesmo no nível da expressão).  
  
### <a name="loaded"></a>Carregado  
 <xref:System.Windows.FrameworkElement.Loaded> é gerado em seguida. O <xref:System.Windows.FrameworkElement.Loaded> é gerado antes do processamento final, mas depois que o sistema de layout calculou a todos os valores necessários para renderização. <xref:System.Windows.FrameworkElement.Loaded> exige que a árvore lógica que está dentro de um elemento for concluída e se conecta a uma fonte de apresentação que fornece o HWND e a superfície de renderização. Associação de dados padrão (associação de fontes locais, como outras propriedades ou fontes de dados definidas diretamente) terá ocorrido antes <xref:System.Windows.FrameworkElement.Loaded>. A vinculação de dados assíncrona (fontes externas ou dinâmicas) pode ter ocorrido, mas, por definição de sua natureza assíncrona, não pode haver garantia de que ela ocorreu.  
  
 O mecanismo pelo qual o <xref:System.Windows.FrameworkElement.Loaded> é gerado é diferente de <xref:System.Windows.FrameworkElement.Initialized>. O <xref:System.Windows.FrameworkElement.Initialized> evento é um elemento gerado pelo elemento, sem uma coordenação direta por uma árvore de elemento concluído. Por outro lado, o <xref:System.Windows.FrameworkElement.Loaded> é gerado como um esforço coordenado em toda a árvore de todo elemento (especificamente, a árvore lógica). Quando todos os elementos na árvore de estão em um estado em que eles são considerados carregado, o <xref:System.Windows.FrameworkElement.Loaded> evento é gerado pela primeira vez no elemento raiz. O <xref:System.Windows.FrameworkElement.Loaded> evento é gerado, em seguida, sucessivamente em cada elemento filho.  
  
> [!NOTE]
>  Esse comportamento pode lembrar superficialmente o túnel de um evento roteado. No entanto, nenhuma informação é levada de um evento para outro. Cada elemento sempre tem a oportunidade de controlar seu <xref:System.Windows.FrameworkElement.Loaded> eventos e marcar os dados do evento como tratado não tem nenhum efeito além desse elemento.  
  
### <a name="unloaded"></a>Descarregado  
 <xref:System.Windows.FrameworkElement.Unloaded> é gerado por último e é iniciado com a fonte de apresentação ou visual pai que está sendo removido. Quando <xref:System.Windows.FrameworkElement.Unloaded> é gerado e manipulados, o elemento que é o pai de origem do evento (conforme determinado pela <xref:System.Windows.FrameworkElement.Parent%2A> propriedade) ou qualquer elemento determinado para cima em árvores lógicos ou visuais pode ter sido não definido, o que significa que a associação de dados, referências de recurso , e estilos não podem ser definidos como seu valor de tempo de execução normal ou último conhecido.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Elementos de modelo de aplicativo dos eventos de tempo de vida  
 Aproveitando os eventos de tempo de vida comuns para elementos são os seguintes elementos de modelo de aplicativo: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, e <xref:System.Windows.Controls.Frame>. Eles estendem os eventos de tempo de vida comuns com eventos adicionais que são relevantes para suas finalidades específicas. Eles são discutidos com detalhes nos seguintes locais:  
  
-   <xref:System.Windows.Application>: [Visão geral do gerenciamento de aplicativo](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [Visão geral do Windows WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, e <xref:System.Windows.Controls.Frame>: [visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do valor da propriedade da dependência](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
