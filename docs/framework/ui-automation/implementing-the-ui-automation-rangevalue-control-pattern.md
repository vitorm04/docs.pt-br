---
title: Implementando o padrão de controle RangeValue de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180177"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementando o padrão de controle RangeValue de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IRangeValueProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.RangeValuePattern> padrão de controle é usado para suportar controles que podem ser definidos como um valor dentro de um intervalo. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle de valor de intervalo, observe as seguintes diretrizes e convenções:  
  
- Os controles permitem a recalibração de suas propriedades suportadas com base na localização ou preferência do usuário. Um exemplo disso é um controle de termômetro que pode ser definido para exibir a temperatura em Fahrenheit ou Celsius.  
  
- Controles que tenham valores de alcance ambíguos, como barras de progresso ou controles deslizantes, devem ter esses valores normalizados.  
  
 ![Barra de progresso.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Exemplo de barra de progresso onde o valor é do tipo inteiro e os valores mínimos e máximos da propriedade são normalizados em 0 e 100, respectivamente  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a>Membros obrigatórios para IRangeValueProvider  
  
|Membro obrigatório|Tipo de membro|Observações|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Métodos|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>é chamado com um valor <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> que é <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>maior ou menor do que .|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
