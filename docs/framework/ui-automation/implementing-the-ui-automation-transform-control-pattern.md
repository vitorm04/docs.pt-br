---
title: Implementando o Padrão de Controle de Transformação de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: d038991da4048e3279ae974cbf4d3e53691349af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088543"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementando o Padrão de Controle de Transformação de Automação de IU
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ITransformProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.TransformPattern> padrão de controle é usado para dar suporte a controles que podem ser movidos, redimensionados ou girados dentro de um espaço bidimensional. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle Transform, observe as seguintes diretrizes e convenções:  
  
-   Suporte para esse padrão de controle não está limitado a objetos na área de trabalho. Esse padrão de controle também deve ser suportado pelos filhos de um objeto de contêiner, se os filhos podem ser movidos, redimensionados ou girados livremente dentro dos limites do contêiner.  
  
-   Um objeto não pode ser movido, redimensionado ou rotacionado de forma que sua localização na tela resultante seria ser completamente fora das coordenadas de seu contêiner e, portanto, inacessível para o teclado ou mouse (por exemplo, quando uma janela de nível superior é movida de fora da tela ou um objeto filho é movido para fora dos limites do visor do contêiner). Nesses casos, o objeto será colocado o mais próximo das coordenadas de tela solicitada possível com as coordenadas esquerdas ou superior, substituídas para estar dentro dos limites do contêiner.  
  
-   Para sistemas de vários monitores, se um objeto for movido, redimensionado ou girado completamente fora das coordenadas de tela da área de trabalho combinado, o objeto é colocado no monitor principal o mais próximo das coordenadas solicitadas quanto possível.  
  
-   Todos os parâmetros e valores de propriedade são absolutos e independente da localidade.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Membros necessários para ITransformProvider  
 As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Método|Nenhum|  
  
 Esse padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -Se a <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> é false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -Se a <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> é false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -Se a <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> é false.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
