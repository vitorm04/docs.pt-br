---
title: Implementando o Padrão Controle de Window de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180042"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>Implementando o Padrão Controle de Window de Automação de Interface de Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IWindowProvider>convenções para <xref:System.Windows.Automation.WindowPattern> a implementação, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.WindowPattern> padrão de controle é usado para suportar controles que fornecem funcionalidade sinuosa baseada em janelas dentro de uma interface gráfica tradicional (GUI). Exemplos de controles que devem implementar esse padrão de controle incluem janelas de aplicativos de nível superior, janelas de crianças de interface de vários documentos (MDI), controles de painel split resizáveis, diálogos modais e janelas de ajuda de balão.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle de janelas, observe as seguintes diretrizes e convenções:  
  
- Para suportar a capacidade de modificar o tamanho da janela e <xref:System.Windows.Automation.Provider.ITransformProvider> a <xref:System.Windows.Automation.Provider.IWindowProvider>posição da tela usando a Automação de UI, um controle deve ser implementado além de .  
  
- Controles que contêm barras de título e elementos da barra de título que permitem que o controle <xref:System.Windows.Automation.Provider.IWindowProvider>seja movido, redimensionado, maximizado, minimizado ou fechado são normalmente necessários para implementar .  
  
- Controles como pop-ups de ponta de ferramenta e caixa de combinação <xref:System.Windows.Automation.Provider.IWindowProvider>ou menu suspenso sem normalimplemento .  
  
- As janelas de ajuda de balão são diferenciadas dos pop-ups básicos da dica de ferramenta pelo fornecimento de um botão Close semelhante à janela.  
  
- O modo de tela cheia não é suportado pelo IWindowProvider, pois é específico de recurso para um aplicativo e não é um comportamento típico da janela.  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a>Membros obrigatórios para IWindowProvider  
 As seguintes propriedades, métodos e eventos são necessários para a interface IWindowProvider.  
  
|Membro obrigatório|Tipo de membro|Observações|  
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
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Evento|Nenhum|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Evento|Nenhum|  
|<xref:System.Windows.Automation.WindowInteractionState>|Evento|Não é garantido ser<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> - Quando um controle não suporta um comportamento solicitado.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> - Quando o parâmetro não é um número válido.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
