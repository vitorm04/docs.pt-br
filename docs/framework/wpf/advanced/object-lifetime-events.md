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
ms.openlocfilehash: 3b761674bd2464ee87e07d9299c805431f8fdeb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141101"
---
# <a name="object-lifetime-events"></a>Eventos de tempo de vida do objeto
Este tópico descreve os eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] específicos que indicam os estágios de criação, uso e destruição no tempo de vida do objeto.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você entenda as propriedades de dependência da perspectiva de um consumidor das propriedades de dependência existentes em classes do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e que leu o tópico [Visão geral das propriedades de dependência](dependency-properties-overview.md). Para seguir os exemplos deste tópico, você também deve compreender [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (consulte [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) e saber como escrever aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>
## <a name="object-lifetime-events"></a>Eventos de tempo de vida do objeto  
 Todos os objetos no código gerenciado do Microsoft .NET Framework passam por um conjunto semelhante de estágios de vida, criação, uso e destruição. Muitos objetos têm um estágio de vida de finalização que ocorre como parte da fase de destruição. Objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais especificamente os objetos visuais que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifica como elementos, também têm um conjunto de estágios comuns de vida útil do objeto. Os modelos de programação e aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expõem esses estágios como uma série de eventos. Há quatro tipos principais de objetos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com relação a eventos de tempo de vida; elementos em geral, elementos de janela, hosts de navegação e objetos de aplicativo. Janelas e hosts de navegação também estão no agrupamento maior de objetos visuais (elementos). Este tópico descreve os eventos de tempo de vida que são comuns a todos os elementos e, em seguida, apresenta os mais específicos que se aplicam a definições de aplicativo, janelas ou hosts de navegação.  
  
<a name="common_events"></a>
## <a name="common-lifetime-events-for-elements"></a>Eventos de tempo de vida comuns aos elementos  
 Qualquer elemento de nível de estrutura wpf <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>(esses objetos derivados de qualquer um ou ) tem três eventos comuns ao longo da vida: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>e <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Inicializado  
 <xref:System.Windows.FrameworkElement.Initialized>é levantada primeiro, e aproximadamente corresponde à inicialização do objeto pela chamada ao seu construtor. Como o evento ocorre em resposta à inicialização, há a garantia de que todas as propriedades do objeto são definidas. (Uma exceção são os usos de expressão, como recursos dinâmicos ou vinculativos; estes serão expressões não avaliadas.) Como conseqüência da exigência de que todas <xref:System.Windows.FrameworkElement.Initialized> as propriedades sejam definidas, a seqüência de ser levantada por elementos aninhados que são definidos na marcação parece ocorrer em ordem de elementos mais profundos na árvore de elementos primeiro, em seguida, elementos pai em direção à raiz. Essa ordem ocorre porque as relações de pai e filho e o confinamento são propriedades e, portanto, o pai não pode relatar a inicialização até que os elementos filho que preenchem a propriedade também sejam inicializados completamente.  
  
 Quando você está escrevendo manipuladores <xref:System.Windows.FrameworkElement.Initialized> em resposta ao evento, você deve considerar que não há garantia de que todos os outros elementos na árvore de elementos (árvore lógica ou árvore visual) em torno de onde o manipulador está conectado foram criados, particularmente elementos parentais. Variáveis de membro podem ser nulas ou fontes de dados podem ainda não ter sido preenchidas pela associação subjacente (mesmo no nível da expressão).  
  
### <a name="loaded"></a>Carregado  
 <xref:System.Windows.FrameworkElement.Loaded>é levantada em seguida. O <xref:System.Windows.FrameworkElement.Loaded> evento é levantado antes da renderização final, mas após o sistema de layout ter calculado todos os valores necessários para a renderização. <xref:System.Windows.FrameworkElement.Loaded>implica que a árvore lógica em que um elemento está contido está completa e se conecta a uma fonte de apresentação que fornece o HWND e a superfície de renderização. A vinculação padrão de dados (vinculação a fontes locais, como outras propriedades ou fontes de dados diretamente definidas) terá ocorrido antes <xref:System.Windows.FrameworkElement.Loaded>de . A vinculação de dados assíncrona (fontes externas ou dinâmicas) pode ter ocorrido, mas, por definição de sua natureza assíncrona, não pode haver garantia de que ela ocorreu.  
  
 O mecanismo pelo <xref:System.Windows.FrameworkElement.Loaded> qual o evento <xref:System.Windows.FrameworkElement.Initialized>é levantado é diferente de . O <xref:System.Windows.FrameworkElement.Initialized> evento é levantado elemento por elemento, sem uma coordenação direta por uma árvore de elementos completa. Em contraste, <xref:System.Windows.FrameworkElement.Loaded> o evento é levantado como um esforço coordenado em toda a árvore do elemento (especificamente, a árvore lógica). Quando todos os elementos da árvore estão em um <xref:System.Windows.FrameworkElement.Loaded> estado onde são considerados carregados, o evento é levantado pela primeira vez sobre o elemento raiz. O <xref:System.Windows.FrameworkElement.Loaded> evento é então levantado sucessivamente em cada elemento infantil.  
  
> [!NOTE]
> Esse comportamento pode lembrar superficialmente o túnel de um evento roteado. No entanto, nenhuma informação é levada de um evento para outro. Cada elemento sempre tem a <xref:System.Windows.FrameworkElement.Loaded> oportunidade de lidar com seu evento, e marcar os dados do evento como manipulados não tem efeito além desse elemento.  
  
### <a name="unloaded"></a>Descarregado  
 <xref:System.Windows.FrameworkElement.Unloaded>é levantada por último e é iniciada pela fonte de apresentação ou pelo pai visual sendo removido. Quando <xref:System.Windows.FrameworkElement.Unloaded> é levantado e manipulado, o elemento que é <xref:System.Windows.FrameworkElement.Parent%2A> o pai-fonte do evento (conforme determinado pela propriedade) ou qualquer elemento para cima nas árvores lógicas ou visuais pode já ter sido desdefinido, o que significa que a vinculação de dados, referências de recursos e estilos podem não ser definidos para o seu valor normal ou último conhecido de tempo de execução.  
  
<a name="application_model_elements"></a>
## <a name="lifetime-events-application-model-elements"></a>Elementos de modelo de aplicativo dos eventos de tempo de vida  
 Com base nos eventos comuns da vida <xref:System.Windows.Application>útil <xref:System.Windows.Window> <xref:System.Windows.Controls.Page>para <xref:System.Windows.Navigation.NavigationWindow>elementos estão os seguintes elementos do modelo de aplicação: , , , e <xref:System.Windows.Controls.Frame>. Eles estendem os eventos de tempo de vida comuns com eventos adicionais que são relevantes para suas finalidades específicas. Eles são discutidos com detalhes nos seguintes locais:  
  
- <xref:System.Windows.Application>: [Visão geral do gerenciamento de aplicativos](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [Visão geral do WPF Windows](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>e <xref:System.Windows.Controls.Frame>: [Visão Geral da Navegação](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Confira também

- [Precedência do valor de propriedade da dependência](dependency-property-value-precedence.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
