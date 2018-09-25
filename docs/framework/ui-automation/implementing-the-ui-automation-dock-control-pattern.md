---
title: Implementando o padrão de controle de encaixe da automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 518f49e004b98b3b3898ecc86fcc289821a8408c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071657"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementando o padrão de controle de encaixe da automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IDockProvider>, incluindo informações sobre as propriedades. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.DockPattern> padrão de controle é usado para expor as propriedades de encaixe de um controle dentro de um contêiner de encaixe. Um contêiner de encaixe é um controle que permite que você organize os elementos filho horizontal e verticalmente, relativos uns aos outros. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Contêiner de encaixe com dois filhos encaixados. ](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Exemplo do Visual Studio o encaixe em que a janela "Class View" é DockPosition.Right e a janela "Error List" é DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de encaixe, observe as seguintes diretrizes e convenções:  
  
-   <xref:System.Windows.Automation.Provider.IDockProvider> não expõe as propriedades do contêiner de encaixe ou propriedades de controles que estão encaixadas adjacente ao controle atual dentro do contêiner de encaixe.  
  
-   Controles são encaixados em relação aos outros com base no atual a ordem z; o mais alto sua ordem z colocação, quanto eles são colocados da borda especificada do contêiner de encaixe.  
  
-   Se o contêiner de encaixe é redimensionado, todos os controles encaixados dentro do contêiner serão reposicionados liberação para a mesma margem para o qual eles foram originalmente encaixados. Os controles encaixados também serão redimensionado para preencher espaços dentro do contêiner de acordo com o comportamento de encaixe de seus <xref:System.Windows.Automation.DockPosition>. Por exemplo, se <xref:System.Windows.Automation.DockPosition.Top> for especificado, os lados esquerdo e direito do controle se expandirá para preencher qualquer espaço disponível. Se <xref:System.Windows.Automation.DockPosition.Fill> for especificado, todos os quatro lados do controle se expandirá para preencher qualquer espaço disponível.  
  
-   Em um sistema de vários monitor, os controles devem encaixar à esquerda ou direita do monitor atual. Se isso não for possível, eles devem encaixar o lado esquerdo do monitor mais à esquerda ou à direita do monitor mais à direita.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Membros necessários para IDockProvider  
 As propriedades e métodos a seguir são necessários para implementar a interface IDockProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Método|Nenhum|  
  
 Esse padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> -Quando um controle não é capaz de executar o estilo de encaixe solicitado.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
