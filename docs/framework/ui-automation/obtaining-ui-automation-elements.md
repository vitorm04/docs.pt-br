---
title: Obtendo elementos da automação interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 23b1b92c52988761aa67eb2de16a1b9141a0de30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524852"
---
# <a name="obtaining-ui-automation-elements"></a>Obtendo elementos da automação interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico descreve as várias maneiras de obter <xref:System.Windows.Automation.AutomationElement> objetos para [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos.  
  
> [!CAUTION]
>  Se seu aplicativo cliente pode tentar localizar elementos em sua própria interface do usuário, você deve fazer todas as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] chama em um thread separado. Para obter mais informações, consulte [problemas de Threading de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Elemento raiz  
 Todas as pesquisas de <xref:System.Windows.Automation.AutomationElement> objetos devem ter um local inicial. Isso pode ser qualquer elemento, incluindo a área de trabalho, uma janela do aplicativo ou um controle.  
  
 O elemento raiz para a área de trabalho, do qual todos os elementos são descendentes, é obtido do estático <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> propriedade.  
  
> [!CAUTION]
>  Em geral, você deve tentar obter apenas os filhos diretos do <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Uma pesquisa por descendentes pode percorrer centenas ou mesmo milhares de elementos, possivelmente resultando em um estouro de pilha. Se você está tentando obter um elemento específico em um nível inferior, você deve iniciar a pesquisa de janela do aplicativo ou de um contêiner em um nível inferior.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Condições  
 Para a maioria das técnicas que você pode usar para recuperar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos, você deve especificar um <xref:System.Windows.Automation.Condition>, que é um conjunto de critérios que definem quais elementos você deseja recuperar.  
  
 A condição mais simples é <xref:System.Windows.Automation.Condition.TrueCondition>, um objeto predefinido especificando que todos os elementos dentro do escopo de pesquisa serão retornados. <xref:System.Windows.Automation.Condition.FalseCondition>, o oposto de <xref:System.Windows.Automation.Condition.TrueCondition>, é menos útil, pois ela impediria todos os elementos de serem encontrados.  
  
 Três outras condições predefinidas podem ser usadas sozinho ou em combinação com outras condições: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, e <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, usado por si só, é equivalente a <xref:System.Windows.Automation.Condition.TrueCondition>, porque ele não filtra elementos por seus <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> ou <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> propriedades.  
  
 Outras condições são criadas de um ou mais <xref:System.Windows.Automation.PropertyCondition> objetos, cada um deles especifica um valor da propriedade. Por exemplo, um <xref:System.Windows.Automation.PropertyCondition> pode especificar que o elemento está habilitado, ou que ele oferece suporte a um determinado padrão de controle.  
  
 Condições podem ser combinadas usando a lógica booleana construindo objetos de tipos <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, e <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Escopo da pesquisa  
 Pesquisas feitas usando <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A> deve ter um escopo, bem como um local inicial.  
  
 O escopo define o espaço em torno do local inicial a ser pesquisado. Isso pode incluir o próprio elemento, seus irmãos, seu pai, seus ancestrais, seus filhos imediatos e seus descendentes.  
  
 O escopo de uma pesquisa é definido por uma combinação bit a bit de valores da <xref:System.Windows.Automation.TreeScope> enumeração.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Localizar um elemento conhecidos  
 Para localizar um elemento conhecido, identificado por seu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, ou alguma outra propriedade ou combinação de propriedades, é mais fácil de usar o <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> método. Se o elemento procurado é uma janela do aplicativo, o ponto inicial da pesquisa pode ser o <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Essa maneira de localizar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos é mais útil em cenários de teste automatizados.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Localizando elementos em uma subárvore  
 Para localizar todos os elementos atendem a critérios específicos que estão relacionada a um elemento conhecido, você pode usar <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Por exemplo, você pode usar esse método para recuperar itens da lista ou itens de menu de uma lista ou um menu, ou para identificar todos os controles em uma caixa de diálogo.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Caminhando uma subárvore  
 Se você não possui conhecimento prévio dos aplicativos que seu cliente pode ser usado, você pode construir uma subárvore de todos os elementos de seu interesse, usando o <xref:System.Windows.Automation.TreeWalker> classe. Seu aplicativo pode fazer isso em resposta a um evento com foco alterado. ou seja, quando um aplicativo ou controle recebe foco de entrada, o cliente de automação de interface do usuário examina filhos e talvez todos os descendentes do elemento focalizado atualmente.  
  
 Outra maneira na qual <xref:System.Windows.Automation.TreeWalker> pode ser usado é identificar os ancestrais de um elemento. Por exemplo, percorrendo a árvore, você pode identificar a janela pai de um controle.  
  
 Você pode usar <xref:System.Windows.Automation.TreeWalker> criando um objeto da classe (definindo os elementos de interesse passando um <xref:System.Windows.Automation.Condition>), ou usando um dos seguintes objetos predefinidos que são definidos como campos de <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Localiza somente elementos cujos <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> é de propriedade `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Localiza somente elementos cujos <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> é de propriedade `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Localiza todos os elementos.|  
  
 Depois de obter um <xref:System.Windows.Automation.TreeWalker>, usá-lo é simples. Basta chamar o `Get` métodos para navegar entre os elementos da subárvore.  
  
 O <xref:System.Windows.Automation.TreeWalker.Normalize%2A> método pode ser usado para navegar para um elemento na subárvore de outro elemento que não faz parte do modo de exibição. Por exemplo, suponha que você criou um modo de exibição de uma subárvore usando <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Seu aplicativo, em seguida, recebe a notificação de que uma barra de rolagem recebeu o foco de entrada. Como uma barra de rolagem não é um elemento de conteúdo, ele não está presente no modo de exibição da subárvore. No entanto, você pode passar o <xref:System.Windows.Automation.AutomationElement> que representa a barra de rolagem para <xref:System.Windows.Automation.TreeWalker.Normalize%2A> e recuperar o ancestral mais próximo que está na exibição de conteúdo.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Outras maneiras de recuperar um elemento  
 Além de navegação e pesquisa, você pode recuperar um <xref:System.Windows.Automation.AutomationElement> das seguintes maneiras.  
  
### <a name="from-an-event"></a>De um evento  
 Quando seu aplicativo recebe um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento, o objeto de origem passado para o manipulador de eventos é um <xref:System.Windows.Automation.AutomationElement>. Por exemplo, se você se inscreveu para eventos com foco alterado, o código-fonte passados para o <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> é o elemento que recebeu o foco.  
  
 Para obter mais informações, consulte [assinar eventos de automação de interface do usuário](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>De um ponto  
 Se você tiver coordenadas de tela (por exemplo, uma posição do cursor), você pode recuperar um <xref:System.Windows.Automation.AutomationElement> usando a estatística <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> método.  
  
### <a name="from-a-window-handle"></a>De um identificador de janela  
 Para recuperar um <xref:System.Windows.Automation.AutomationElement> de um HWND, use estático <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> método.  
  
### <a name="from-the-focused-control"></a>De controle em foco  
 Você pode recuperar um <xref:System.Windows.Automation.AutomationElement> que representa o controle com foco do estático <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também
- [Localizar um elemento de automação de interface do usuário com base em uma condição de propriedade](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [Navegar em elementos de automação de interface do usuário com o TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
