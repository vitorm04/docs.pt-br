---
title: Implementando o padrão de controle Toggle de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 2293dc77369ecf019bd1093808135eeefd99c115
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932057"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>Implementando o padrão de controle Toggle de automação de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IToggleProvider>, incluindo informações sobre métodos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.TogglePattern> padrão de controle é usado para dar suporte a controles que podem percorrer um conjunto de Estados e manter um estado depois de definido. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de alternância, observe as seguintes diretrizes e convenções:  
  
- Os controles que não mantêm o estado quando ativados, como botões, botões da barra de ferramentas e hiperlinks <xref:System.Windows.Automation.Provider.IInvokeProvider> , devem implementar em seu lugar.  
  
- Um controle deve <xref:System.Windows.Automation.ToggleState> percorrer seu na seguinte ordem <xref:System.Windows.Automation.ToggleState.Off> : <xref:System.Windows.Automation.ToggleState.On>e, se houver suporte, <xref:System.Windows.Automation.ToggleState.Indeterminate>.  
  
- <xref:System.Windows.Automation.TogglePattern>não fornece um método SetState (NewState) devido a problemas em torno da configuração direta de uma caixa de seleção de três Estados sem percorrer a <xref:System.Windows.Automation.ToggleState> sequência apropriada.  
  
- O controle RadioButton não implementa <xref:System.Windows.Automation.Provider.IToggleProvider>, pois não é capaz de percorrer seus Estados válidos.  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a>Membros necessários para IToggleProvider  
 As propriedades e os métodos a seguir são necessários <xref:System.Windows.Automation.Provider.IToggleProvider>para implementar o.  
  
|Membro necessário|Tipo de membro|Observações|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Propriedade|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem nenhuma exceção associada.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Obter o estado de Alternância de uma caixa de seleção usando automação de interface do usuário](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
