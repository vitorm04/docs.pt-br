---
title: "Implementando o padrão de controle MultipleView de interface de usuário "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5ff185ddb145d51fe8bc32ac10f3a45b57ec954c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementando o padrão de controle MultipleView de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.MultipleViewPattern> padrão de controle é usado para oferecer suporte aos controles que fornecem e pode alternar entre várias representações do mesmo conjunto de informações ou controles filho.  
  
 Exemplos de controles que podem apresentar vários modos de exibição incluem a exibição de lista (que pode mostrar o conteúdo como miniaturas, lado a lado, ícones ou detalhes), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] gráficos (pizza, linha, barras, valor da célula com uma fórmula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documentos (normal, layout de Web Imprimir layout, o layout de leitura, a estrutura de tópicos), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendário (ano, mês, semana, dia), e [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] capas. As exibições com suporte são determinadas pelo desenvolvedor do controle e são específicas para cada controle.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de exibição de várias, observe as seguintes diretrizes e convenções:  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider>também deve ser implementada em um contêiner que gerencia o modo de exibição atual, se ele for diferente de um controle que fornece a exibição atual. Por exemplo, o Windows Explorer contém um controle de lista para o conteúdo da pasta atual enquanto o modo de exibição para o controle é gerenciado pelo aplicativo Windows Explorer.  
  
-   Um controle que é capaz de classificar o seu conteúdo não é considerado para dar suporte a vários modos de exibição.  
  
-   A coleção de exibições deve ser idêntica em instâncias.  
  
-   Nomes de exibição devem ser adequados para uso em texto em fala, Braille e outros aplicativos legíveis por humanos.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Membros necessários para IMultipleViewProvider  
 As propriedades e métodos a seguir são necessários para implementar IMultipleViewProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Método|Nenhum|  
  
 Não existem eventos associados a esse padrão de controle.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 O provedor deve lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Quando o <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> é chamado com um parâmetro que não é um membro da coleção de exibições com suporte.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
