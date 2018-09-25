---
title: Visão Geral dos Provedores de Automação de Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7b4286abdb2e2b5bb3f91f6fa0bbffd6beda8efc
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072583"
---
# <a name="ui-automation-providers-overview"></a>Visão Geral dos Provedores de Automação de Interface do Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Provedores de automação de interface do usuário ativam os controles para se comunicar com aplicativos cliente de automação de interface do usuário. Em geral, cada controle ou outro elemento distinto em um [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] é representado por um provedor. O provedor expõe informações sobre o elemento e, opcionalmente, implementa os padrões de controle que permitem que o aplicativo cliente interagir com o controle.  
  
 Aplicativos cliente geralmente não é necessário trabalhar diretamente com provedores de. A maioria dos controles padrão em aplicativos que usam o [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], ou [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] estruturas são expostas automaticamente para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistema. Aplicativos que implementam os controles personalizados também podem implementar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedores para esses controles e aplicativos cliente não precisa tomar nenhuma medida especial para acessá-los.  
  
 Este tópico fornece uma visão geral de como implementam os desenvolvedores de controle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedores, especialmente para controles em [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Tipos de provedores  
 Provedores de automação de interface do usuário se enquadram em duas categorias: provedores do lado do cliente e provedores do lado do servidor.  
  
### <a name="client-side-providers"></a>Provedores do lado do cliente  
 Provedores do lado do cliente são implementados pelos clientes de automação de interface do usuário para se comunicar com um aplicativo que não dá suporte ou não suporta completamente, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Provedores do lado do cliente normalmente consegue se comunicar com o servidor além do limite de processo, enviando e recebendo mensagens do Windows.  
  
 Como provedores de automação de interface do usuário para controles em [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms, ou [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplicativos são fornecidos como parte do sistema operacional, aplicativos cliente raramente têm que implementar seus próprios provedores e esta visão geral não abordá-los Além disso.  
  
### <a name="server-side-providers"></a>Provedores do lado do servidor  
 Provedores do lado do servidor são implementados por controles personalizados ou aplicativos que são baseados em uma estrutura de interface do usuário diferente [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms, ou [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Provedores do lado do servidor se comunicar com aplicativos cliente além do limite de processo ao expor interfaces para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] principais do sistema, que por sua vez serve solicitações de clientes.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Conceitos de provedor de automação de interface do usuário  
 Esta seção fornece breves explicações sobre alguns dos principais conceitos que você precisa entender a fim de implementar provedores de automação de interface do usuário.  
  
### <a name="elements"></a>Elementos  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos são partes de [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] que são visíveis para os clientes de automação de interface do usuário. Exemplos incluem janelas de aplicativos, painéis, botões, dicas de ferramentas, caixas de listagem e itens de lista.  
  
### <a name="navigation"></a>Navegação  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos são expostos aos clientes como um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] constrói a árvore ao navegar de um elemento para outro. A navegação é habilitada pelos provedores para cada elemento, cada um deles pode apontar para um pai, irmãos e filhos.  
  
 Para obter mais informações sobre o modo de exibição de cliente do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral da árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Exibições  
 Um cliente pode ver o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore em três modos de exibição principais, conforme mostrado na tabela a seguir.  
  
|||  
|-|-|  
|Modo de exibição bruto|Contém todos os elementos.|  
|Modo de exibição de controle|Contém elementos que são controles.|  
|Exibição de conteúdo|Contém elementos que têm conteúdo.|  
  
 Para obter mais informações sobre modos de exibição de cliente para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral da árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 É responsabilidade da implementação do provedor para definir um elemento como um elemento de conteúdo ou um elemento de controle. Elementos de controle podem ou não ser também elementos de conteúdo, mas todos os elementos de conteúdo são elementos de controle.  
  
### <a name="frameworks"></a>Estruturas  
 Uma estrutura é um componente que gerencia controles de filho, teste de clique e renderização em uma área da tela. Por exemplo, uma [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] janela, geralmente conhecida como um HWND, pode servir como uma estrutura que contém várias [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos como botões, uma barra de status e uma barra de menus.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] contêiner de controles como caixas de listagem e modos de exibição de árvore são considerados frameworks, porque eles contêm seu próprio código para renderizar itens filhos e executar testes de clique neles. Por outro lado, uma [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] caixa de listagem não é uma estrutura, porque a renderização e teste de clique está sendo manipulado pelo recipiente [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] janela.  
  
 O [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] em um aplicativo pode ser constituído de estruturas diferentes. Por exemplo, uma janela do aplicativo HWND pode conter [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] que por sua vez contém um componente como uma caixa de combinação em um HWND.  
  
### <a name="fragments"></a>Fragmentos  
 Um fragmento é uma subárvore completa dos elementos de uma determinada estrutura. O elemento no nó raiz da subárvore é chamado uma raiz de fragmento. Uma raiz de fragmento não tem um pai, mas está hospedada em algum outro framework, geralmente um [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] janela (HWND).  
  
### <a name="hosts"></a>Hosts  
 O nó raiz de cada fragmento deve ser hospedado em um elemento, geralmente um [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] janela (HWND). A exceção é a área de trabalho, não é hospedada em qualquer outro elemento. O host de um controle personalizado é o HWND do controle em si, não a janela do aplicativo ou qualquer outra janela que pode conter grupos de controles de nível superior.  
  
 O host de um fragmento desempenha um papel importante no fornecimento de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] serviços. Ele permite a navegação para a raiz do fragmento e fornece algumas propriedades padrão para que o provedor personalizado não precisa implementá-los.  
  
## <a name="see-also"></a>Consulte também  
 [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
