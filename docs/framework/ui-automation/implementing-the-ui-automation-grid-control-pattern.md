---
title: Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 5eceafee4d02478c9e011a473ee1d036df91075d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932177"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico apresenta as diretrizes e convenções para <xref:System.Windows.Automation.Provider.IGridProvider>implementar o, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final da visão geral.  
  
 O <xref:System.Windows.Automation.GridPattern> padrão de controle é usado para dar suporte a controles que atuam como contêineres para uma coleção de elementos filho. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.IGridItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que pode ser atravessado por linha e coluna. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de grade, observe as seguintes diretrizes e convenções:  
  
- As coordenadas de grade são baseadas em zero com o canto superior esquerdo (ou célula superior direita, dependendo da localidade) com coordenadas (0, 0).  
  
- Se uma célula estiver vazia, um elemento de automação da interface do usuário ainda deverá ser retornado para <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> dar suporte à propriedade dessa célula. Isso é possível quando o layout dos elementos filho na grade é semelhante a uma matriz irregular (Veja o exemplo abaixo).  
  
 ![Exibição do Windows Explorer mostrando layout irregular.](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Exemplo de um controle de grade com coordenadas vazias  
  
- Uma grade com um único item ainda é necessária para implementar <xref:System.Windows.Automation.Provider.IGridProvider> se for considerada logicamente como uma grade. O número de itens filho na grade é irrelevante.  
  
- Linhas e colunas ocultas, dependendo da implementação do provedor, podem ser carregadas na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore e, portanto, serão refletidas <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> nas <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> Propriedades e. Se as linhas e colunas ocultas ainda não tiverem sido carregadas, elas não deverão ser contadas.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>não habilita a manipulação ativa de uma grade; <xref:System.Windows.Automation.Provider.ITransformProvider> deve ser implementado para habilitar essa funcionalidade.  
  
- Use um <xref:System.Windows.Automation.StructureChangedEventHandler> para escutar alterações estruturais ou de layout na grade, como células que foram adicionadas, removidas ou mescladas.  
  
- Use um <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> para acompanhar a passagem pelos itens ou células de uma grade.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Membros necessários para IGridProvider  
 As propriedades e os métodos a seguir são necessários para implementar a interface IGridProvider.  
  
|Membros necessários|Tipo|Observações|  
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
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Se a coordenada de linha solicitada for <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> maior do que a ou a coordenada <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>de coluna for maior do que o.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Se uma das coordenadas de linha ou coluna solicitada for menor que zero.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle GridItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
