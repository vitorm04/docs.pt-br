---
title: Implementando o padrão de controle de tabela de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 1fec3671f017ae6c6864537805e6c793b5f9046b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458148"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementando o padrão de controle de tabela de automação de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ITableProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final da visão geral.  
  
 O padrão de controle <xref:System.Windows.Automation.TablePattern> é usado para dar suporte a controles que atuam como contêineres para uma coleção de elementos filho. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.ITableItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que possa ser atravessado por linha e coluna. Esse padrão de controle é análogo a <xref:System.Windows.Automation.Provider.IGridProvider>, com a diferença de que qualquer controle que está implementando <xref:System.Windows.Automation.Provider.ITableProvider> também deve expor uma relação de cabeçalho de coluna e/ou linha para cada elemento filho. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de tabela, observe as seguintes diretrizes e convenções:  
  
- O acesso ao conteúdo de células individuais é por meio de um sistema de coordenadas lógica bidimensional ou uma matriz fornecida pela implementação simultânea necessária de <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
- Um cabeçalho de coluna ou de linha pode estar contido em um objeto de tabela ou ser um objeto de cabeçalho separado que está associado a um objeto de tabela.  
  
- Cabeçalhos de coluna e linha podem incluir um cabeçalho principal, bem como quaisquer cabeçalhos de suporte.  
  
> [!NOTE]
> Esse conceito torna-se evidente em uma planilha do Microsoft Excel, na qual um usuário definiu uma coluna "First Name". Esta coluna agora tem dois cabeçalhos — o cabeçalho "First Name" definido pelo usuário e a designação alfanumérica para aquela coluna atribuída pelo aplicativo.  
  
- Consulte [implementando o padrão de controle de grade de automação da interface do usuário](implementing-the-ui-automation-grid-control-pattern.md) para funcionalidade de grade relacionada.  
  
 ![Tabela com itens de cabeçalho complexos.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Exemplo de uma tabela com cabeçalhos de coluna complexos  
  
 ![Tabela com Propriedade RowOrColumnMajor ambígua.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Exemplo de uma tabela com a propriedade RowOrColumnMajor ambígua  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Membros necessários para ITableProvider  
 As propriedades e os métodos a seguir são necessários para a interface ITableProvider.  
  
|Membros necessários|Tipo de membro|Anotações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem nenhuma exceção associada.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle TableItem de automação de interface do usuário](implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementando o padrão de controle Grid de automação de interface do usuário](implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
