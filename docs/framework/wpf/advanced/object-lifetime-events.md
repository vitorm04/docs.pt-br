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
ms.openlocfilehash: dd2e116c4241a44786af3a56b931b0c3c0571814
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933496"
---
# <a name="object-lifetime-events"></a>Eventos de tempo de vida do objeto
Este tópico descreve os eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] específicos que indicam os estágios de criação, uso e destruição no tempo de vida do objeto.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você entenda as propriedades de dependência da perspectiva de um consumidor das propriedades de dependência existentes em classes do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e que leu o tópico [Visão geral das propriedades de dependência](dependency-properties-overview.md). Para seguir os exemplos deste tópico, você também deve compreender [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (consulte [Visão geral de XAML (WPF)](xaml-overview-wpf.md)) e saber como escrever aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Eventos de tempo de vida do objeto  
 Todos os objetos no código gerenciado do Microsoft .NET Framework passam por um conjunto semelhante de estágios de vida, criação, uso e destruição. Muitos objetos têm um estágio de vida de finalização que ocorre como parte da fase de destruição. Objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais especificamente os objetos visuais que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifica como elementos, também têm um conjunto de estágios comuns de vida útil do objeto. Os modelos de programação e aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expõem esses estágios como uma série de eventos. Há quatro tipos principais de objetos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com relação a eventos de tempo de vida; elementos em geral, elementos de janela, hosts de navegação e objetos de aplicativo. Janelas e hosts de navegação também estão no agrupamento maior de objetos visuais (elementos). Este tópico descreve os eventos de tempo de vida que são comuns a todos os elementos e, em seguida, apresenta os mais específicos que se aplicam a definições de aplicativo, janelas ou hosts de navegação.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Eventos de tempo de vida comuns aos elementos  
 Qualquer elemento de nível de estrutura do WPF (aqueles objetos derivados de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>) tem três eventos de tempo de <xref:System.Windows.FrameworkElement.Initialized>vida <xref:System.Windows.FrameworkElement.Loaded>comuns: <xref:System.Windows.FrameworkElement.Unloaded>, e.  
  
### <a name="initialized"></a>Inicializado  
 <xref:System.Windows.FrameworkElement.Initialized>é gerado primeiro e, aproximadamente, corresponde à inicialização do objeto pela chamada para seu construtor. Como o evento ocorre em resposta à inicialização, há a garantia de que todas as propriedades do objeto são definidas. (Uma exceção são os usos de expressões como recursos dinâmicos ou associação; elas serão expressões não avaliadas). Como consequência do requisito de que todas as propriedades são definidas, a sequência de <xref:System.Windows.FrameworkElement.Initialized> serem geradas por elementos aninhados que são definidos na marcação parece ocorrer na ordem dos elementos mais profundos na árvore de elementos primeiro, depois pelos elementos pai em direção à raiz. Essa ordem ocorre porque as relações de pai e filho e o confinamento são propriedades e, portanto, o pai não pode relatar a inicialização até que os elementos filho que preenchem a propriedade também sejam inicializados completamente.  
  
 Quando você está escrevendo manipuladores em resposta ao <xref:System.Windows.FrameworkElement.Initialized> evento, deve considerar que não há nenhuma garantia de que todos os outros elementos na árvore de elementos (árvore lógica ou árvore visual) em que o manipulador está anexado tenha sido criado, particularmente elementos pai. Variáveis de membro podem ser nulas ou fontes de dados podem ainda não ter sido preenchidas pela associação subjacente (mesmo no nível da expressão).  
  
### <a name="loaded"></a>Carregado  
 <xref:System.Windows.FrameworkElement.Loaded>é gerado em seguida. O <xref:System.Windows.FrameworkElement.Loaded> evento é gerado antes da renderização final, mas depois que o sistema de layout calculava todos os valores necessários para renderização. <xref:System.Windows.FrameworkElement.Loaded>implica que a árvore lógica na qual um elemento está contido está concluída e se conecta a uma fonte de apresentação que fornece o HWND e a superfície de renderização. A <xref:System.Windows.FrameworkElement.Loaded>Associação de dados padrão (a associação a fontes locais, como outras propriedades ou fontes de dados definidas diretamente) ocorrerá antes do. A vinculação de dados assíncrona (fontes externas ou dinâmicas) pode ter ocorrido, mas, por definição de sua natureza assíncrona, não pode haver garantia de que ela ocorreu.  
  
 O mecanismo pelo qual o <xref:System.Windows.FrameworkElement.Loaded> evento é gerado é diferente de <xref:System.Windows.FrameworkElement.Initialized>. O <xref:System.Windows.FrameworkElement.Initialized> evento é gerado elemento por elemento, sem uma coordenação direta por uma árvore de elementos concluída. Por outro lado, <xref:System.Windows.FrameworkElement.Loaded> o evento é gerado como um esforço coordenado em toda a árvore de elementos (especificamente, a árvore lógica). Quando todos os elementos na árvore estão em um estado em que são considerados carregados, o <xref:System.Windows.FrameworkElement.Loaded> evento é gerado pela primeira vez no elemento raiz. O <xref:System.Windows.FrameworkElement.Loaded> evento é então gerado sucessivamente em cada elemento filho.  
  
> [!NOTE]
> Esse comportamento pode lembrar superficialmente o túnel de um evento roteado. No entanto, nenhuma informação é levada de um evento para outro. Cada elemento sempre tem a oportunidade de lidar com <xref:System.Windows.FrameworkElement.Loaded> seu evento e a marcação dos dados do evento como manipulado não tem nenhum efeito além desse elemento.  
  
### <a name="unloaded"></a>Descarregado  
 <xref:System.Windows.FrameworkElement.Unloaded>é gerado por último e é iniciado pela origem da apresentação ou pelo pai do Visual que está sendo removido. Quando <xref:System.Windows.FrameworkElement.Unloaded> é gerado e manipulado, o elemento que é o pai da origem do evento ( <xref:System.Windows.FrameworkElement.Parent%2A> conforme determinado pela propriedade) ou qualquer elemento em diante nas árvores lógicas ou visuais pode já ter sido desdefinido, o que significa que a associação de dados, referências de recursos , e os estilos podem não ser definidos para seu valor normal ou último tempo de execução conhecido.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Elementos de modelo de aplicativo dos eventos de tempo de vida  
 A criação dos eventos de tempo de vida comuns para elementos são os seguintes elementos <xref:System.Windows.Application>de modelo <xref:System.Windows.Controls.Page>de <xref:System.Windows.Navigation.NavigationWindow>aplicativo: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Window>,, e. Eles estendem os eventos de tempo de vida comuns com eventos adicionais que são relevantes para suas finalidades específicas. Eles são discutidos com detalhes nos seguintes locais:  
  
- <xref:System.Windows.Application>: [Visão geral do gerenciamento de aplicativos](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [Visão geral do WPF Windows](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>e :<xref:System.Windows.Controls.Frame> [Visão geral de navegação](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Precedência do valor da propriedade da dependência](dependency-property-value-precedence.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
