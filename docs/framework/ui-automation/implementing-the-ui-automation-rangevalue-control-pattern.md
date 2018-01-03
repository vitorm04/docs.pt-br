---
title: "Implementando o padrão de controle RangeValue de interface de usuário "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a53f5f802d451d7575188d4687b6d88f96ec64fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>Implementando o padrão de controle RangeValue de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IRangeValueProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.RangeValuePattern> padrão de controle é usado para oferecer suporte aos controles que podem ser definidos para um valor dentro do intervalo. Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de valor de intervalo, observe as seguintes diretrizes e convenções:  
  
-   Controles permitem recalibragem de suas propriedades com suporte com base na preferência de localidade ou usuário. Um exemplo disso é um controle de termômetro que pode ser definido para exibir a temperatura em Fahrenheit ou em Celsius.  
  
-   Controles que têm intervalos de valores ambíguos, como barras de progresso ou controles deslizantes, devem ter esses valores normalizados.  
  
 ![Barra de progresso. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Exemplo de uma barra de progresso em que o valor é do tipo inteiro e valores de propriedade mínimo e máximo são normalizados para 0 e 100, respectivamente  
  
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
  
 Esse padrão de controle não possui eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>é chamado com um valor que seja maior do que <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> ou menor que <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
