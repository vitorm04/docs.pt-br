---
title: "Implementando o padrão de controle de tabela de automação de interface de usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4a1fbe175abf07eaccfd177c6e32f5515e88c4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementando o padrão de controle de tabela de automação de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ITableProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listadas no final da visão geral.  
  
 O <xref:System.Windows.Automation.TablePattern> padrão de controle é usado para oferecer suporte aos controles que atuam como contêineres para uma coleção de elementos filho. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.ITableItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que pode ser percorrido por linha e coluna. Esse padrão de controle é análogo a <xref:System.Windows.Automation.Provider.IGridProvider>, com a diferença que qualquer controle implementando <xref:System.Windows.Automation.Provider.ITableProvider> também deve expor uma relação de cabeçalho de coluna e/ou linha para cada elemento filho. Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de tabela, observe as seguintes diretrizes e convenções:  
  
-   Acesso ao conteúdo das células individuais é por meio de um sistema de coordenadas bidimensional lógico ou matriz fornecida pela implementação simultânea necessária de <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
-   Um cabeçalho de coluna ou linha pode estar contido em um objeto de tabela ou ser um objeto separado de cabeçalho que está associado um objeto de tabela.  
  
-   Cabeçalhos de coluna e linha podem incluir um cabeçalho principal, bem como os cabeçalhos de suporte.  
  
> [!NOTE]
>  Esse conceito fica evidente em uma [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] planilha em que um usuário tenha definido uma coluna "Nome". Esta coluna agora tem dois cabeçalhos — o cabeçalho de "Nome" definido pelo usuário e a designação alfanumérica para aquela coluna atribuída pelo aplicativo.  
  
-   Consulte [Implementando o padrão de controle Grid de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) para a funcionalidade de grade relacionados.  
  
 ![Tabela com itens de cabeçalho complexos. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Exemplo de uma tabela com cabeçalhos de coluna complexa  
  
 ![Tabela com RowOrColumnMajor ambíguas. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Exemplo de uma tabela com RowOrColumnMajor ambíguas  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Membros necessários para IToggleProvider  
 As propriedades e métodos a seguir são necessários para a interface ITableProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Método|Nenhum|  
  
 Esse padrão de controle não possui eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Esse padrão de controle não tem exceção associada.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementando o padrão de controle TableItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [Implementando o padrão de controle Grid de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
