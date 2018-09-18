---
title: Implementando o Padrão Controle de Window de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 551e4ac5dc8917931e41d7aaa7dca1f8613852bd
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45994436"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementando o Padrão Controle de Window de Automação de Interface de Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IWindowProvider>, incluindo informações sobre <xref:System.Windows.Automation.WindowPattern> propriedades, métodos e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.WindowPattern> padrão de controle é usado para dar suporte a controles que fornecem funcionalidade de baseados em janela fundamental dentro de um tradicional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]. Exemplos de controles que devem implementar esse padrão de controle incluem janelas de aplicativos de nível superior, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] janelas filho, controles de painel de divisão redimensionável, caixas de diálogo modais e balão de ajudam do windows.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de janela, observe as seguintes diretrizes e convenções:  
  
-   Para dar suporte a capacidade de modificar tanto o tamanho da janela e posição na tela usando automação de interface do usuário, um controle deve implementar <xref:System.Windows.Automation.Provider.ITransformProvider> além <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Controles que contêm as barras de título e elementos de barra de título que permitem o controle a ser movido, redimensionado, maximizada, minimizada ou fechada são geralmente necessários para implementar <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Controles como pop-ups de dica de ferramenta e combinação caixa ou menus suspensos normalmente não implementam <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
-   Janelas da Ajuda de balão são diferenciadas de pop-ups de dica de ferramenta básica pela provisão de um botão de fechar janela semelhante.  
  
-   Modo de tela inteira não é suportado por IWindowProvider conforme ele é um recurso específico a um aplicativo e não é o comportamento de janela típica.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Membros necessários para IWindowProvider  
 As seguintes propriedades, métodos e eventos são necessários para a interface IWindowProvider.  
  
|Membro necessário|Tipo de membro|Observações|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|evento|Nenhum|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|evento|Nenhum|  
|<xref:System.Windows.Automation.WindowInteractionState>|evento|Não é garantido para ser <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -Quando um controle não oferece suporte a um comportamento solicitado.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -Quando o parâmetro não é um número válido.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
