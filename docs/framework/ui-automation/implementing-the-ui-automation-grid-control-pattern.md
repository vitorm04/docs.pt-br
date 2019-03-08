---
title: Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 12588e6aa108813b2d857f6818bd27a275d12597
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676805"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementando o Padrão de Controle Grid de Automação de Interface de Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listadas no final da visão geral.  
  
 O <xref:System.Windows.Automation.GridPattern> padrão de controle é usado para dar suporte a controles que atuam como contêineres para uma coleção de elementos filho. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.IGridItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que pode ser percorrido por linha e coluna. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de grade, observe as seguintes diretrizes e convenções:  
  
-   Coordenadas de grade são baseadas em zero com o canto superior esquerdo (ou célula superior direita dependendo da localidade) tendo as coordenadas (0, 0).  
  
-   Se uma célula estiver vazia, um elemento de automação de interface do usuário ainda deve ser retornado para oferecer suporte a <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> propriedade para essa célula. Isso é possível quando o layout dos elementos filho na grade é semelhante a uma matriz irregular (veja o exemplo abaixo).  
  
 ![Windows Explorer exibir mostrando desbalanceada layout. ](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Exemplo de um controle de grade com coordenadas vazios  
  
-   Uma grade com um único item ainda é necessária para implementar <xref:System.Windows.Automation.Provider.IGridProvider> se ela é considerada como uma grade logicamente. O número de itens filho na grade é irrelevante.  
  
-   Linhas e colunas, dependendo da implementação do provedor, ocultas podem ser carregadas na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore e, portanto, serão refletidas na <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> e <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> propriedades. Se as linhas e colunas ocultas ainda não tiverem sido carregadas, eles não devem ser contados.  
  
-   <xref:System.Windows.Automation.Provider.IGridProvider> não permite a manipulação ativa de uma grade; <xref:System.Windows.Automation.Provider.ITransformProvider> devem ser implementados para habilitar essa funcionalidade.  
  
-   Use um <xref:System.Windows.Automation.StructureChangedEventHandler> para escutar alterações estruturais ou de layout para a grade, como as células que foram adicionados, removidos ou mesclados.  
  
-   Use um <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> para controlar a travessia pelos itens ou células de uma grade.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Membros necessários para IGridProvider  
 As propriedades e métodos a seguir são necessários para a implementação da interface IGridProvider.  
  
|Membros necessários|Tipo|Observações|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Método|Nenhum|  
  
 Esse padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Se a coordenada da linha solicitada é maior do que o <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> ou a coordenada da coluna é maior do que o <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -Se a coluna ou linha solicitada coordenadas é menor que zero.|  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle GridItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
