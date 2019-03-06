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
ms.openlocfilehash: b5f38492fff9aa87094542b174becc54ee324a78
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371483"
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
 Qualquer elemento de nível de framework WPF (os objetos que derivam de qualquer um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>) tem três eventos de tempo de vida comuns: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, e <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Inicializado  
 <xref:System.Windows.FrameworkElement.Initialized> é gerado primeiro e corresponde aproximadamente à inicialização do objeto pela chamada para seu construtor. Como o evento ocorre em resposta à inicialização, há a garantia de que todas as propriedades do objeto são definidas. (Uma exceção são os usos de expressões como recursos dinâmicos ou associação; elas serão expressões não avaliadas). Como consequência o requisito de que todas as propriedades são definidas, a sequência de <xref:System.Windows.FrameworkElement.Initialized> que está sendo gerado por elementos aninhados que são definidos na marcação parece ocorrer na ordem dos elementos mais profundos da árvore de elementos em primeiro lugar, em seguida, elementos pais na direção da raiz. Essa ordem ocorre porque as relações de pai e filho e o confinamento são propriedades e, portanto, o pai não pode relatar a inicialização até que os elementos filho que preenchem a propriedade também sejam inicializados completamente.  
  
 Quando você estiver escrevendo manipuladores em resposta ao <xref:System.Windows.FrameworkElement.Initialized> evento, você deve considerar que não há nenhuma garantia de que todos os outros elementos na árvore de elementos (árvore lógica ou a árvore visual) em torno de onde o manipulador está anexado tiverem sido criados, particularmente elementos pai. Variáveis de membro podem ser nulas ou fontes de dados podem ainda não ter sido preenchidas pela associação subjacente (mesmo no nível da expressão).  
  
### <a name="loaded"></a>Carregado  
 <xref:System.Windows.FrameworkElement.Loaded> é gerado em seguida. O <xref:System.Windows.FrameworkElement.Loaded> é gerado antes da renderização final, mas depois que o sistema de layout ter calculado todos os valores necessários para a renderização. <xref:System.Windows.FrameworkElement.Loaded> implica que a árvore lógica que está dentro de um elemento for concluída e se conecta a uma fonte de apresentação que fornece o HWND e a superfície de renderização. Vinculação de dados padrão (vinculação a fontes locais, como outras propriedades ou fontes de dados definidas diretamente) terá ocorrido antes <xref:System.Windows.FrameworkElement.Loaded>. A vinculação de dados assíncrona (fontes externas ou dinâmicas) pode ter ocorrido, mas, por definição de sua natureza assíncrona, não pode haver garantia de que ela ocorreu.  
  
 O mecanismo pelo qual o <xref:System.Windows.FrameworkElement.Loaded> é gerado é diferente de <xref:System.Windows.FrameworkElement.Initialized>. O <xref:System.Windows.FrameworkElement.Initialized> evento é gerado elemento por elemento, sem uma coordenação direta por uma árvore de elemento completa. Por outro lado, o <xref:System.Windows.FrameworkElement.Loaded> evento é gerado como um esforço coordenado em toda a árvore de elementos (especificamente, a árvore lógica). Quando todos os elementos na árvore estão em um estado em que eles são considerados carregado, o <xref:System.Windows.FrameworkElement.Loaded> evento é gerado pela primeira vez no elemento raiz. O <xref:System.Windows.FrameworkElement.Loaded> é, em seguida, gerado sucessivamente em cada elemento filho.  
  
> [!NOTE]
>  Esse comportamento pode lembrar superficialmente o túnel de um evento roteado. No entanto, nenhuma informação é levada de um evento para outro. Cada elemento sempre tem a oportunidade de manipular seu <xref:System.Windows.FrameworkElement.Loaded> eventos e marcar os dados do evento como manipulados não tem nenhum efeito além desse elemento.  
  
### <a name="unloaded"></a>Descarregado  
 <xref:System.Windows.FrameworkElement.Unloaded> é gerado por último e é iniciado com a fonte de apresentação ou o visual pai que está sendo removido. Quando <xref:System.Windows.FrameworkElement.Unloaded> é gerado e manipulado, o elemento que é o pai de origem do evento (conforme determinado pela <xref:System.Windows.FrameworkElement.Parent%2A> propriedade) ou qualquer dado elemento para cima nas árvores visuais ou lógicas pode já ter sido definido, o que significa que a vinculação de dados, referências de recurso , e estilos não podem ser definidos como seu valor de tempo de execução normal ou último conhecido.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Elementos de modelo de aplicativo dos eventos de tempo de vida  
 Aproveitando os eventos de tempo de vida comuns para elementos são os seguintes elementos de modelo de aplicativo: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, e <xref:System.Windows.Controls.Frame>. Eles estendem os eventos de tempo de vida comuns com eventos adicionais que são relevantes para suas finalidades específicas. Eles são discutidos com detalhes nos seguintes locais:  
  
-   <xref:System.Windows.Application>: [Visão geral do gerenciamento de aplicativo](../app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [Visão geral do Windows WPF](../app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, e <xref:System.Windows.Controls.Frame>: [Visão geral da navegação](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Consulte também
- [Precedência do valor da propriedade da dependência](dependency-property-value-precedence.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
