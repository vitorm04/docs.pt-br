---
title: Visão Geral dos Provedores de Automação de Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 1f780ffc37b0aff93a3358c1980d271fe10c1321
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179883"
---
# <a name="ui-automation-providers-overview"></a>Visão Geral dos Provedores de Automação de Interface do Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Os provedores de automação de interface do usuário permitem que os controles se comuniquem com os aplicativos clientes de automação de interface do usuário. Em geral, cada controle ou [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] outro elemento distinto em um é representado por um provedor. O provedor expõe informações sobre o elemento e, opcionalmente, implementa padrões de controle que permitem ao aplicativo cliente interagir com o controle.  
  
 Os aplicativos clientes geralmente não têm que trabalhar diretamente com os provedores. A maioria dos controles padrão em aplicativos que usam o [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] Win32, Windows Forms [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ou frameworks são automaticamente expostos ao sistema. Aplicativos que implementam controles personalizados também podem implementar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedores para esses controles, e os aplicativos clientes não têm que tomar nenhuma medida especial para ter acesso a eles.  
  
 Este tópico fornece uma visão geral [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de como os desenvolvedores de controle implementam provedores, particularmente para controles em Formulários Windows e janelas Win32.  
  
<a name="Types_of_Providers"></a>
## <a name="types-of-providers"></a>Tipos de Provedores  
 Os provedores de automação de ui se enquadram em duas categorias: provedores do lado do cliente e provedores do lado do servidor.  
  
### <a name="client-side-providers"></a>Provedores do lado do cliente  
 Os provedores do lado do cliente são implementados por clientes de automação [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]de interface do usuário para se comunicar com um aplicativo que não suporta ou não suporta totalmente, . Os provedores do lado do cliente geralmente se comunicam com o servidor através do limite do processo enviando e recebendo mensagens do Windows.  
  
 Como os provedores de automação de interface do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] usuário para controles no Win32, Windows Forms ou aplicativos são fornecidos como parte do sistema operacional, os aplicativos clientes raramente têm que implementar seus próprios provedores, e essa visão geral não os cobre mais.  
  
### <a name="server-side-providers"></a>Provedores do lado do servidor  
 Os provedores do lado do servidor são implementados por controles personalizados ou por aplicativos que [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]são baseados em uma estrutura de interface do usuário que não seja o Win32, o Windows Forms ou .  
  
 Os provedores do lado do servidor se comunicam com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] aplicativos clientes através do limite do processo, expondo interfaces ao sistema principal, que por sua vez atende solicitações de clientes.  
  
<a name="AutomationProviderConcepts"></a>
## <a name="ui-automation-provider-concepts"></a>Conceitos de provedor de automação de UI  
 Esta seção fornece explicações breves de alguns dos conceitos-chave que você precisa entender para implementar provedores de automação de ui.  
  
### <a name="elements"></a>Elementos  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementos são [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] peças que são visíveis para clientes de Automação de Interface do Usuário. Exemplos incluem janelas de aplicativos, painéis, botões, dicas de ferramentas, caixas de lista e itens de lista.  
  
### <a name="navigation"></a>Navegação  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]elementos são expostos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] aos clientes como uma árvore. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]constrói a árvore navegando de um elemento para outro. A navegação é habilitada pelos provedores para cada elemento, cada um dos quais pode apontar para um pai, irmãos e filhos.  
  
 Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a visão do cliente da árvore, consulte Visão geral da árvore de [automação de ui](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Exibições  
 Um cliente pode [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ver a árvore em três pontos de vista principais, como mostrado na tabela a seguir.  
  
|||  
|-|-|  
|Vista bruta|Contém todos os elementos.|  
|Exibição de controle|Contém elementos que são controles.|  
|Exibição de conteúdo|Contém elementos que têm conteúdo.|  
  
 Para obter mais informações [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sobre as visualizações do cliente da árvore, consulte Visão geral da árvore de [automação de ui](ui-automation-tree-overview.md).  
  
 É responsabilidade da implementação do provedor definir um elemento como um elemento de conteúdo ou um elemento de controle. Os elementos de controle podem ou não ser também elementos de conteúdo, mas todos os elementos de conteúdo são elementos de controle.  
  
### <a name="frameworks"></a>Estruturas  
 Uma estrutura é um componente que gerencia controles de crianças, testes de hit e renderização em uma área da tela. Por exemplo, uma janela Win32, muitas vezes referida como hwnd, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pode servir como uma estrutura que contém vários elementos, como uma barra de menu, uma barra de status e botões.  
  
 Os controles de contêiner Win32, como caixas de lista e visualizações de árvores, são considerados frameworks, porque contêm seu próprio código para renderizar itens infantis e realizar testes de hit neles. Em contraste, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uma caixa de lista não é uma estrutura, porque a renderização e o teste de hit estão sendo manuseados pela janela de contenção. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]  
  
 O [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] em uma aplicação pode ser composto de diferentes estruturas. Por exemplo, uma janela de aplicativo HWND pode conter Html Dinâmico (DHTML) que, por sua vez, contém um componente como uma caixa de combinação em um HWND.  
  
### <a name="fragments"></a>Fragmentos  
 Um fragmento é uma subárvore completa de elementos de uma estrutura específica. O elemento no nó raiz da subárvore é chamado de raiz de fragmento. Uma raiz de fragmento não tem um pai, mas está hospedada dentro de algum outro quadro, geralmente uma janela Win32 (HWND).  
  
### <a name="hosts"></a>Hosts  
 O nó raiz de cada fragmento deve ser hospedado em um elemento, geralmente uma janela Win32 (HWND). A exceção é a área de trabalho, que não está hospedada em nenhum outro elemento. O hospedeiro de um controle personalizado é o HWND do controle em si, não a janela do aplicativo ou qualquer outra janela que possa conter grupos de controles de alto nível.  
  
 O hospedeiro de um fragmento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desempenha um papel importante na prestação de serviços. Ele permite a navegação na raiz do fragmento e fornece algumas propriedades padrão para que o provedor personalizado não precise implementá-las.  
  
## <a name="see-also"></a>Confira também

- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](server-side-ui-automation-provider-implementation.md)
