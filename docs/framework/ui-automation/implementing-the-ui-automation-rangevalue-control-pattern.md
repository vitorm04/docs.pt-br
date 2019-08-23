---
title: Implementando o padrão de controle RangeValue de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 70ee5009e2763348f7c69613a1776e02e82e0391
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932133"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementando o padrão de controle RangeValue de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IRangeValueProvider>, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.RangeValuePattern> padrão de controle é usado para dar suporte a controles que podem ser definidos para um valor dentro de um intervalo. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de valor de intervalo, observe as seguintes diretrizes e convenções:  
  
- Os controles permitem a recalibração de suas propriedades com suporte com base na localidade ou na preferência do usuário. Um exemplo disso é um controle de termômetro que pode ser definido para exibir a temperatura em Fahrenheit ou Celsius.  
  
- Controles que têm valores de intervalo ambíguos, como barras de progresso ou controles deslizantes, devem ter esses valores normalizados.  
  
 ![Barra de progresso.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Exemplo de uma barra de progresso em que o valor é do tipo inteiro e os valores de propriedade mínimo e máximo são normalizados para 0 e 100, respectivamente  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>Membros necessários para IRangeValueProvider  
  
|Membro necessário|Tipo de membro|Observações|  
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
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>é chamado com um valor que é maior <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> ou menor que. <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
