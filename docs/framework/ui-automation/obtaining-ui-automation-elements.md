---
title: "Obtendo elementos da automação interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: f657d4289e46f84246059010a2f9550d1c831d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="obtaining-ui-automation-elements"></a>Obtendo elementos da automação interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico descreve as várias maneiras de obter <xref:System.Windows.Automation.AutomationElement> objetos para [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos.  
  
> [!CAUTION]
>  Se seu aplicativo cliente tentar localizar elementos na sua própria interface de usuário, você deve fazer todas as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chama em um thread separado. Para obter mais informações, consulte [problemas de Threading de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Elemento raiz  
 Todas as pesquisas para <xref:System.Windows.Automation.AutomationElement> objetos devem ter um local inicial. Isso pode ser qualquer elemento, incluindo a área de trabalho, uma janela de aplicativo ou um controle.  
  
 O elemento raiz para a área de trabalho, do qual todos os elementos são descendentes, é obtido da estático <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> propriedade.  
  
> [!CAUTION]
>  Em geral, você deve tentar obter apenas filhos diretos do <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Uma pesquisa por descendentes pode percorrer centenas ou mesmo milhares de elementos, possivelmente resultando em um estouro de pilha. Se você está tentando obter um elemento específico em um nível inferior, você deve iniciar sua pesquisa de janela do aplicativo ou de um contêiner em um nível inferior.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Condições  
 A maioria das técnicas que você pode usar para recuperar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos, você deve especificar um <xref:System.Windows.Automation.Condition>, que é um conjunto de critérios que definem quais elementos você deseja recuperar.  
  
 A condição mais simples é <xref:System.Windows.Automation.Condition.TrueCondition>, um objeto predefinido especificando que todos os elementos dentro do escopo de pesquisa serão retornados. <xref:System.Windows.Automation.Condition.FalseCondition>, o oposto de <xref:System.Windows.Automation.Condition.TrueCondition>, é menos útil, pois ela impediria todos os elementos de serem encontrados.  
  
 Três outras condições predefinidas podem ser usadas sozinha ou em combinação com outras condições: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, e <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, usado por si só, é equivalente a <xref:System.Windows.Automation.Condition.TrueCondition>, porque ele não filtra elementos por suas <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> ou <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> propriedades.  
  
 Outras condições são criadas de um ou mais <xref:System.Windows.Automation.PropertyCondition> objetos, cada um deles especifica um valor de propriedade. Por exemplo, um <xref:System.Windows.Automation.PropertyCondition> pode especificar que o elemento está habilitado, ou que ele oferece suporte a um determinado padrão de controle.  
  
 Condições podem ser combinadas usando lógica booleana construindo objetos dos tipos <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, e <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Escopo de pesquisa  
 Pesquisas feitas usando <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A> devem ter um escopo, bem como um local inicial.  
  
 O escopo define o espaço em torno de local inicial que será pesquisado. Isso pode incluir o próprio elemento, seus irmãos, seu pai, seus ancestrais, seus filhos imediatos e seus descendentes.  
  
 O escopo de uma pesquisa é definido por uma combinação bit a bit de valores da <xref:System.Windows.Automation.TreeScope> enumeração.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Localizar um elemento conhecidos  
 Para localizar um elemento conhecido, identificado por seu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, ou alguma outra propriedade ou combinação de propriedades, é mais fácil de usar o <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> método. Se o elemento procurado é uma janela de aplicativo, o ponto inicial da pesquisa pode ser o <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Essa maneira de localizar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos é mais útil em cenários de teste automatizados.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Localizando elementos em uma subárvore  
 Para localizar todos os elementos que estão relacionados a um elemento conhecido satisfazem critérios específicos, você pode usar <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Por exemplo, você pode usar esse método para recuperar itens da lista ou itens de menu de uma lista ou menu, ou para identificar todos os controles em uma caixa de diálogo.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Percorrer uma subárvore  
 Se você não tiver nenhum conhecimento prévio dos aplicativos que seu cliente pode ser usado, você pode construir uma subárvore de todos os elementos de interesse usando a <xref:System.Windows.Automation.TreeWalker> classe. O aplicativo pode fazer isso em resposta a um evento de foco alterado. ou seja, quando um aplicativo ou controle recebe foco de entrada, o cliente de automação de interface do usuário examina filhos e talvez todos os descendentes do elemento focalizado atualmente.  
  
 Outra maneira na qual <xref:System.Windows.Automation.TreeWalker> pode ser usado é identificar os ancestrais de um elemento. Por exemplo, percorrendo a árvore, você pode identificar a janela pai de um controle.  
  
 Você pode usar <xref:System.Windows.Automation.TreeWalker> , criando um objeto da classe (definindo os elementos de interesse passando um <xref:System.Windows.Automation.Condition>), ou usando um dos seguintes objetos predefinidos que são definidos como campos de <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Localiza somente elementos cujo <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> é de propriedade `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Localiza somente elementos cujo <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> é de propriedade `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Localiza todos os elementos.|  
  
 Depois de obter um <xref:System.Windows.Automation.TreeWalker>, usá-lo é simples. Basta chamar o `Get` métodos para navegar entre os elementos da subárvore.  
  
 O <xref:System.Windows.Automation.TreeWalker.Normalize%2A> método pode ser usado para navegar para um elemento na subárvore do outro elemento que não faz parte da exibição. Por exemplo, suponha que você criou um modo de exibição de uma subárvore usando <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Em seguida, o aplicativo recebe a notificação de que uma barra de rolagem recebeu o foco de entrada. Como uma barra de rolagem não é um elemento de conteúdo, ele não está presente no modo de exibição da subárvore. No entanto, você pode passar o <xref:System.Windows.Automation.AutomationElement> representando a barra de rolagem para <xref:System.Windows.Automation.TreeWalker.Normalize%2A> e recuperar o ancestral mais próximo que está na exibição de conteúdo.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Outras maneiras de recuperar um elemento  
 Além de navegação e pesquisa, você pode recuperar um <xref:System.Windows.Automation.AutomationElement> das seguintes maneiras.  
  
### <a name="from-an-event"></a>De um evento  
 Quando seu aplicativo recebe um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento, o objeto de origem passado para o manipulador de eventos é um <xref:System.Windows.Automation.AutomationElement>. Por exemplo, se você se inscreveu para eventos de foco alterado, a fonte passada para o <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> é o elemento que recebeu o foco.  
  
 Para obter mais informações, consulte [assinar eventos de automação de interface do usuário](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>De um ponto  
 Se você tiver coordenadas de tela (por exemplo, uma posição do cursor), você pode recuperar um <xref:System.Windows.Automation.AutomationElement> usando estático <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> método.  
  
### <a name="from-a-window-handle"></a>De um identificador de janela  
 Para recuperar um <xref:System.Windows.Automation.AutomationElement> de um HWND, use estático <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> método.  
  
### <a name="from-the-focused-control"></a>Do controle focalizado  
 Você pode recuperar um <xref:System.Windows.Automation.AutomationElement> que representa o controle focalizado de estático <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Localizar um elemento de automação de interface do usuário com base em uma condição de propriedade](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [Navegar em elementos de automação de interface do usuário com TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
