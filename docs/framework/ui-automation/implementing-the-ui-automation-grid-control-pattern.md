---
title: Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 04f3ee1e01054df6a13ab2391e14a6a7f7274bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180224"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IGridProvider>convenções para a implementação, incluindo informações sobre propriedades, métodos e eventos. Os links para referências adicionais são listados no final da visão geral.  
  
 O <xref:System.Windows.Automation.GridPattern> padrão de controle é usado para apoiar controles que atuam como recipientes para uma coleção de elementos infantis. Os filhos deste elemento <xref:System.Windows.Automation.Provider.IGridItemProvider> devem implementar e ser organizados em um sistema de coordenadas lógicabidimensional que pode ser atravessado por linha e coluna. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle de grade, observe as seguintes diretrizes e convenções:  
  
- As coordenadas da grade são baseadas em zero com a célula superior esquerda (ou superior direita, dependendo da localidade) tendo coordenadas (0, 0).  
  
- Se uma célula estiver vazia, um elemento de Automação de <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> UI ainda deve ser devolvido para suportar a propriedade dessa célula. Isso é possível quando o layout de elementos infantis na grade é semelhante a uma matriz irregular (veja exemplo abaixo).  
  
 ![Visualização do Windows Explorer mostrando layout irregular.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Exemplo de um controle de grade com coordenadas vazias  
  
- Uma grade com um único item <xref:System.Windows.Automation.Provider.IGridProvider> ainda é necessária para ser implementada se for logicamente considerada uma grade. O número de itens infantis na grade é imaterial.  
  
- Linhas e colunas ocultas, dependendo da implementação do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedor, podem ser carregadas <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> na árvore e, portanto, serão refletidas nas propriedades. Se as linhas e colunas ocultas ainda não tiverem sido carregadas, elas não devem ser contadas.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>não permite a manipulação ativa de uma grade; <xref:System.Windows.Automation.Provider.ITransformProvider> deve ser implementado para habilitar essa funcionalidade.  
  
- Use <xref:System.Windows.Automation.StructureChangedEventHandler> um para ouvir alterações estruturais ou de layout na grade, como células que foram adicionadas, removidas ou fundidas.  
  
- Use <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> um para rastrear a travessia através dos itens ou células de uma grade.  
  
<a name="Required_Members_for_IGridProvider"></a>
## <a name="required-members-for-igridprovider"></a>Membros obrigatórios para IGridProvider  
 As seguintes propriedades e métodos são necessários para implementar a interface IGridProvider.  
  
|Membros necessários|Type|Observações|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - Se a coordenada de linha <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> solicitada for maior do <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>que a coordenada da coluna ou a coordenada for maior que a .|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - Se qualquer uma das coordenadas de linha ou coluna solicitadas for inferior a zero.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle GridItem de interface de usuário ](implementing-the-ui-automation-griditem-control-pattern.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
