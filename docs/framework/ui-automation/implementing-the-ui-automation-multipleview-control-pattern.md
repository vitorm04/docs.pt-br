---
title: 'Implementando o padrão de controle MultipleView de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 9063146ac4bee750c4865787b7b44cea6354d30c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712347"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementando o padrão de controle MultipleView de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.MultipleViewPattern> padrão de controle é usado para oferecer suporte aos controles que fornecem e podem alternar entre várias representações do mesmo conjunto de informações ou controles filho.  
  
 Exemplos de controles que podem apresentar vários modos de exibição incluem a exibição de lista (que pode mostrar seu conteúdo como miniaturas, blocos, ícones ou obter detalhes), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] gráficos (pizza, linha, barra, valor da célula com uma fórmula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documentos (normal, layout da Web, Imprimir layout, o layout de leitura, a estrutura de tópicos), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendário (ano, mês, semana, dia), e [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] capas. Os modos de exibição com suporte são determinados pelo desenvolvedor do controle e são específicos para cada controle.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de exibição de várias, observe as seguintes diretrizes e convenções:  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider> também deve ser implementada em um contêiner que gerencia a exibição atual se ele for diferente de um controle que fornece a exibição atual. Por exemplo, o Windows Explorer contém um controle de lista para o conteúdo da pasta atual, enquanto o modo de exibição para o controle é gerenciado do aplicativo Windows Explorer.  
  
-   Um controle que é capaz de classificar seu conteúdo não é considerado para dar suporte a vários modos de exibição.  
  
-   A coleção de exibições deve ser idêntica entre instâncias.  
  
-   Nomes de exibição devem ser adequados para uso em texto em fala, Braille e outros aplicativos legível por humanos.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Membros necessários para IMultipleViewProvider  
 As propriedades e métodos a seguir são necessários para implementar IMultipleViewProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Método|Nenhum|  
  
 Não há nenhum evento associado com esse padrão de controle.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 O provedor deve lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Quando o <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> é chamado com um parâmetro que não é um membro da coleção de exibições com suporte.|  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
