---
title: Implementando o padrão de controle de tabela de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0b3d000112060550734890ad3c4063a26c320b04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180110"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementando o padrão de controle de tabela de automação de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.ITableProvider>convenções para a implementação, incluindo informações sobre propriedades, métodos e eventos. Os links para referências adicionais são listados no final da visão geral.  
  
 O <xref:System.Windows.Automation.TablePattern> padrão de controle é usado para apoiar controles que atuam como recipientes para uma coleção de elementos infantis. Os filhos deste elemento <xref:System.Windows.Automation.Provider.ITableItemProvider> devem implementar e ser organizados em um sistema de coordenadas lógicabidimensional que pode ser atravessado por linha e coluna. Este padrão de controle <xref:System.Windows.Automation.Provider.IGridProvider>é análogo a, <xref:System.Windows.Automation.Provider.ITableProvider> com a distinção de que qualquer implementação de controle também deve expor uma relação de cabeçalho de coluna e/ou linha para cada elemento filho. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle de tabela, observe as seguintes diretrizes e convenções:  
  
- O acesso ao conteúdo de células individuais é através de um sistema de coordenadas ou matriz lógica bidimensional fornecido pela implementação simultânea necessária de <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
- Um cabeçalho de coluna ou linha pode ser contido dentro de um objeto de tabela ou ser um objeto de cabeçalho separado que está associado a um objeto de tabela.  
  
- Os cabeçalhos de coluna e linha podem incluir tanto um cabeçalho primário como quaisquer cabeçalhos de suporte.  
  
> [!NOTE]
> Esse conceito se torna evidente em uma planilha do Microsoft Excel onde um usuário definiu uma coluna "Primeiro nome". Esta coluna agora tem dois cabeçalhos — o cabeçalho "Primeiro nome" definido pelo usuário e a designação alfanumérica para aquela coluna atribuída pelo aplicativo.  
  
- Consulte [Implementando o padrão de controle da grade](implementing-the-ui-automation-grid-control-pattern.md) de automação de ui para a funcionalidade da grade relacionada.  
  
 ![Tabela com itens de cabeçalho complexos.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Exemplo de uma tabela com cabeçalhos de coluna complexos  
  
 ![Tabela com propriedade ambígua RowOrColumnMajor.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Exemplo de uma tabela com linha ambíguaOupropriedadeMaior Coluna  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a>Membros obrigatórios para ITableProvider  
 As seguintes propriedades e métodos são necessários para a interface ITableProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem exceções associadas.  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle TableItem de interface de usuário](implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementando o Padrão de Controle Grid de Automação de Interface de Usuário](implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
