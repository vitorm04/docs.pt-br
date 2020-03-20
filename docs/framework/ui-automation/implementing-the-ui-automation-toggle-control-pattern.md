---
title: Implementando o padrão de controle Toggle de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180057"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>Implementando o padrão de controle Toggle de automação de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IToggleProvider>convenções para a implementação, incluindo informações sobre métodos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.TogglePattern> padrão de controle é usado para suportar controles que podem percorrer um conjunto de estados e manter um estado uma vez definido. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle Alternar, observe as seguintes diretrizes e convenções:  
  
- Controles que não mantêm o estado quando ativados, como botões, botões de <xref:System.Windows.Automation.Provider.IInvokeProvider> barra de ferramentas e hiperlinks, devem ser implementados em seu lugar.  
  
- Um controle deve <xref:System.Windows.Automation.ToggleState> percorrer a sua <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> na seguinte ordem: <xref:System.Windows.Automation.ToggleState.Indeterminate>, e, se apoiado, .  
  
- <xref:System.Windows.Automation.TogglePattern>não fornece um método SetState (newState) devido a problemas envolvendo a configuração <xref:System.Windows.Automation.ToggleState> direta de uma Caixa de Seleção de três estados sem passar por sua seqüência apropriada.  
  
- O controle RadioButton <xref:System.Windows.Automation.Provider.IToggleProvider>não implementa, pois não é capaz de pedalar através de seus estados válidos.  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a>Membros obrigatórios para IToggleProvider  
 As seguintes propriedades e métodos <xref:System.Windows.Automation.Provider.IToggleProvider>são necessários para a implementação.  
  
|Membro obrigatório|Tipo de membro|Observações|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Propriedade|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem exceções associadas.  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Obter o estado Toggle de uma caixa de seleção usando automação de interface do usuário](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
