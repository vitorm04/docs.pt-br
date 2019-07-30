---
title: Visão Geral dos Provedores de Automação de Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 1ffb8101ba0182c8ff11667f59d9bc10c5ffe670
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629564"
---
# <a name="ui-automation-providers-overview"></a>Visão Geral dos Provedores de Automação de Interface do Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Provedores de automação de interface do usuário permitem que controles se comuniquem com aplicativos cliente de automação de interface Em geral, cada controle ou outro elemento distinto em um [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] é representado por um provedor. O provedor expõe informações sobre o elemento e, opcionalmente, implementa padrões de controle que permitem que o aplicativo cliente interaja com o controle.  
  
 Normalmente, os aplicativos cliente não precisam trabalhar diretamente com os provedores. A maioria dos controles padrão em aplicativos que usam as [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]estruturas [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], ou [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] são automaticamente expostas para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistema. Os aplicativos que implementam controles personalizados também [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podem implementar provedores para esses controles, e os aplicativos cliente não precisam realizar etapas especiais para obter acesso a eles.  
  
 Este tópico fornece uma visão geral de como os desenvolvedores [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle implementam provedores, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] especialmente [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] para controles no e no Windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Tipos de provedores  
 Os provedores de automação da interface do usuário se enquadram em duas categorias: provedores do lado do cliente e provedores do lado do servidor.  
  
### <a name="client-side-providers"></a>Provedores do lado do cliente  
 Os provedores do lado do cliente são implementados por clientes de automação da interface do usuário para se comunicar com um aplicativo que não dá [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]suporte a, ou que não oferece suporte completo ao. Provedores do lado do cliente geralmente se comunicam com o servidor pelo limite do processo enviando e recebendo mensagens do Windows.  
  
 Como os provedores de automação da interface [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]do usuário para controles [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] no, Windows Forms ou aplicativos são fornecidos como parte do sistema operacional, os aplicativos cliente raramente precisam implementar seus próprios provedores, e essa visão geral não os cobre soluciona.  
  
### <a name="server-side-providers"></a>Provedores do lado do servidor  
 Os provedores do lado do servidor são implementados por controles personalizados ou por aplicativos baseados em uma estrutura de interface [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]do usuário diferente de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Windows Forms ou.  
  
 Os provedores do lado do servidor se comunicam com aplicativos cliente durante o limite do processo expondo interfaces ao [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistema principal, que, por sua vez, atende a solicitações de clientes.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Conceitos do provedor de automação de interface do usuário  
 Esta seção fornece breves explicações de alguns dos principais conceitos que você precisa entender para implementar provedores de automação de interface do usuário.  
  
### <a name="elements"></a>Elementos  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementos são partes do [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] que são visíveis para clientes de automação da interface do usuário. Os exemplos incluem janelas de aplicativo, painéis, botões, dicas de ferramenta, caixas de listagem e itens de lista.  
  
### <a name="navigation"></a>Navegação  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]os elementos são expostos aos clientes como [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uma árvore. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]constrói a árvore navegando de um elemento para outro. A navegação é habilitada pelos provedores para cada elemento, cada um deles pode apontar para um pai, irmãos e filhos.  
  
 Para obter mais informações sobre a exibição de cliente [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore, consulte [visão geral da árvore de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Exibições  
 Um cliente pode ver a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore em três exibições principais, conforme mostrado na tabela a seguir.  
  
|||  
|-|-|  
|Exibição bruta|Contém todos os elementos.|  
|Exibição de controle|Contém elementos que são controles.|  
|Exibição de conteúdo|Contém elementos que têm conteúdo.|  
  
 Para obter mais informações sobre as exibições [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de cliente da árvore, consulte [visão geral da árvore de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 É responsabilidade da implementação do provedor definir um elemento como um elemento de conteúdo ou um elemento de controle. Elementos de controle podem ou não ser elementos de conteúdo, mas todos os elementos de conteúdo são elementos de controle.  
  
### <a name="frameworks"></a>Estruturas  
 Uma estrutura é um componente que gerencia controles filho, testes de clique e renderização em uma área da tela. Por exemplo, uma [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] janela, geralmente conhecida como HWND, pode servir como uma estrutura que contém vários [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos, como uma barra de menus, uma barra de status e botões.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]controles de contêiner, como caixas de listagem e exibições de árvore, são considerados estruturas, pois contêm seu próprio código para renderizar itens filho e executar testes de impacto neles. Por outro lado, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uma caixa de listagem não é uma estrutura, porque a renderização e o teste de impacto estão sendo tratados [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pela janela que a contém.  
  
 O [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] em um aplicativo pode ser composto de estruturas diferentes. Por exemplo, uma janela de aplicativo HWND pode conter HTML dinâmico (DHTML) que, por sua vez, contém um componente, como uma caixa de combinação em um HWND.  
  
### <a name="fragments"></a>Fragmentos  
 Um fragmento é uma subárvore completa de elementos de uma estrutura específica. O elemento no nó raiz da subárvore é chamado de raiz do fragmento. Uma raiz de fragmento não tem um pai, mas está hospedada em alguma outra estrutura, geralmente [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] uma janela (HWND).  
  
### <a name="hosts"></a>Hosts  
 O nó raiz de cada fragmento deve ser hospedado em um elemento, geralmente uma [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] janela (HWND). A exceção é a área de trabalho, que não está hospedada em nenhum outro elemento. O host de um controle personalizado é o HWND do próprio controle, não a janela do aplicativo ou qualquer outra janela que possa conter grupos de controles de nível superior.  
  
 O host de um fragmento desempenha um papel importante no fornecimento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de serviços. Ele permite a navegação para a raiz do fragmento e fornece algumas propriedades padrão para que o provedor personalizado não precise implementá-las.  
  
## <a name="see-also"></a>Consulte também

- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
