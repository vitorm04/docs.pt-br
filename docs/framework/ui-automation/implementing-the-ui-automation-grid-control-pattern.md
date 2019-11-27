---
title: Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: f4b5f1763b655026b20f37605d4649606af7fea6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435367"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final da visão geral.  
  
 O padrão de controle <xref:System.Windows.Automation.GridPattern> é usado para dar suporte a controles que atuam como contêineres para uma coleção de elementos filho. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.IGridItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que possa ser atravessado por linha e coluna. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de grade, observe as seguintes diretrizes e convenções:  
  
- As coordenadas de grade são baseadas em zero com o canto superior esquerdo (ou célula superior direita, dependendo da localidade) com coordenadas (0, 0).  
  
- Se uma célula estiver vazia, um elemento de automação da interface do usuário ainda deverá ser retornado para dar suporte à propriedade <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> para essa célula. Isso é possível quando o layout dos elementos filho na grade é semelhante a uma matriz irregular (Veja o exemplo abaixo).  
  
 ![Exibição do Windows Explorer mostrando layout irregular.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Exemplo de um controle de grade com coordenadas vazias  
  
- Uma grade com um único item ainda é necessária para implementar <xref:System.Windows.Automation.Provider.IGridProvider> se for considerada logicamente uma grade. O número de itens filho na grade é irrelevante.  
  
- Linhas e colunas ocultas, dependendo da implementação do provedor, podem ser carregadas na árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] e, portanto, serão refletidas nas propriedades <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> e <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A>. Se as linhas e colunas ocultas ainda não tiverem sido carregadas, elas não deverão ser contadas.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider> não habilita a manipulação ativa de uma grade; <xref:System.Windows.Automation.Provider.ITransformProvider> deve ser implementado para habilitar essa funcionalidade.  
  
- Use um <xref:System.Windows.Automation.StructureChangedEventHandler> para escutar alterações estruturais ou de layout na grade, como células que foram adicionadas, removidas ou mescladas.  
  
- Use um <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> para controlar a passagem pelos itens ou células de uma grade.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Membros necessários para IGridProvider  
 As propriedades e os métodos a seguir são necessários para implementar a interface IGridProvider.  
  
|Membros necessários|Tipo|{1&gt;Observações&lt;1}|  
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
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Se a coordenada de linha solicitada for maior do que o <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> ou a coordenada de coluna for maior do que o <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Se uma das coordenadas de linha ou coluna solicitada for menor que zero.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle GridItem de automação de interface do usuário](implementing-the-ui-automation-griditem-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
