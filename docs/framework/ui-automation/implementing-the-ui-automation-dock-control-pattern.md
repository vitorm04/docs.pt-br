---
title: Implementando o padrão de controle de encaixe da automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: b1213791609245209fa37e3cdcb0876c963bfeb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180199"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementando o padrão de controle de encaixe da automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IDockProvider>convenções para a implementação, incluindo informações sobre propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.DockPattern> padrão de controle é usado para expor as propriedades das docas de um controle dentro de um contêiner de acoplamento. Um recipiente de acoplamento é um controle que permite organizar elementos infantis horizontal e verticalmente, em relação um ao outro. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Contêiner de atracação com duas crianças ancoradas.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Exemplo de acoplamento do Visual Studio onde a janela "Class View" é dockPosition.Right e "Error List" Window is DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle dock, observe as seguintes diretrizes e convenções:  
  
- <xref:System.Windows.Automation.Provider.IDockProvider>não expõe quaisquer propriedades do contêiner de acoplamento ou quaisquer propriedades de controles que estejam ancoradas adjacentes ao controle atual dentro do recipiente de acoplamento.  
  
- Os controles são ancorados em relação uns aos outros com base na sua ordem z atual; quanto maior a colocação do pedido z, mais longe são colocados da borda especificada do recipiente de acoplamento.  
  
- Se o recipiente de acoplamento for redimensionado, quaisquer controles ancorados dentro do contêiner serão reposicionados na mesma borda para a qual foram originalmente ancorados. Os controles ancorados também serão redimensionados para preencher qualquer espaço <xref:System.Windows.Automation.DockPosition>dentro do contêiner de acordo com o comportamento de acoplamento de seus . Por exemplo, <xref:System.Windows.Automation.DockPosition.Top> se for especificado, os lados esquerdo e direito do controle se expandirão para preencher qualquer espaço disponível. Se <xref:System.Windows.Automation.DockPosition.Fill> for especificado, todos os quatro lados do controle se expandirão para preencher qualquer espaço disponível.  
  
- Em um sistema multi-monitor, os controles devem acoplar para o lado esquerdo ou direito do monitor atual. Se isso não for possível, eles devem acoplar para o lado esquerdo do monitor mais à esquerda ou para o lado direito do monitor mais à direita.  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a>Membros obrigatórios para IDockProvider  
 As seguintes propriedades e métodos são necessários para implementar a interface IDockProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> - Quando um controle não é capaz de executar o estilo de doca solicitado.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
