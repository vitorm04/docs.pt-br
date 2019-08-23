---
title: Implementando o padrão de controle de tabela de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0852e904414ac4af6777b9476b4b6ad504a09ef3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935701"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementando o padrão de controle de tabela de automação de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico apresenta as diretrizes e convenções para <xref:System.Windows.Automation.Provider.ITableProvider>implementar o, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final da visão geral.  
  
 O <xref:System.Windows.Automation.TablePattern> padrão de controle é usado para dar suporte a controles que atuam como contêineres para uma coleção de elementos filho. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.ITableItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que pode ser atravessado por linha e coluna. Esse padrão de controle é análogo <xref:System.Windows.Automation.Provider.IGridProvider>a, com a diferença de que qualquer <xref:System.Windows.Automation.Provider.ITableProvider> controle que implementa também deve expor uma relação de cabeçalho de coluna e/ou linha para cada elemento filho. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de tabela, observe as seguintes diretrizes e convenções:  
  
- O acesso ao conteúdo de células individuais é por meio de um sistema de coordenadas lógica bidimensional ou uma matriz fornecida pela implementação simultânea <xref:System.Windows.Automation.Provider.IGridProvider>necessária do.  
  
- Um cabeçalho de coluna ou de linha pode estar contido em um objeto de tabela ou ser um objeto de cabeçalho separado que está associado a um objeto de tabela.  
  
- Cabeçalhos de coluna e linha podem incluir um cabeçalho principal, bem como quaisquer cabeçalhos de suporte.  
  
> [!NOTE]
> Esse conceito se torna evidente em [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] uma planilha em que um usuário definiu uma coluna "First Name". Esta coluna agora tem dois cabeçalhos — o cabeçalho "First Name" definido pelo usuário e a designação alfanumérica para aquela coluna atribuída pelo aplicativo.  
  
- Consulte [implementando o padrão de controle de grade de automação da interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) para funcionalidade de grade relacionada.  
  
 ![Tabela com itens de cabeçalho complexos.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Exemplo de uma tabela com cabeçalhos de coluna complexos  
  
 ![Tabela com Propriedade RowOrColumnMajor ambígua.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Exemplo de uma tabela com a propriedade RowOrColumnMajor ambígua  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Membros necessários para ITableProvider  
 As propriedades e os métodos a seguir são necessários para a interface ITableProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem nenhuma exceção associada.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle TableItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementando o padrão de controle Grid de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
