---
title: Obtendo elementos da automação interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: eab4e59ee219808a4c0ae9ca5331a14928b66b5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179993"
---
# <a name="obtaining-ui-automation-elements"></a>Obtendo elementos da automação interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico descreve as várias formas de obtenção <xref:System.Windows.Automation.AutomationElement> de objetos para [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos.  
  
> [!CAUTION]
> Se o seu aplicativo cliente tentar encontrar elementos em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sua própria interface de usuário, você deve fazer todas as chamadas em um segmento separado. Para obter mais informações, consulte [Problemas de threading de automação de ui](ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>
## <a name="root-element"></a>Elemento Root  
 Todas as <xref:System.Windows.Automation.AutomationElement> buscas por objetos devem ter um ponto de partida. Isso pode ser qualquer elemento, incluindo a área de trabalho, uma janela de aplicativo ou um controle.  
  
 O elemento raiz da área de trabalho, do qual todos <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> os elementos são descendentes, é obtido a partir da propriedade estática.  
  
> [!CAUTION]
> Em geral, você deve tentar obter <xref:System.Windows.Automation.AutomationElement.RootElement%2A>apenas filhos diretos do . Uma busca por descendentes pode iterar através de centenas ou mesmo milhares de elementos, possivelmente resultando em um estouro de pilha. Se você estiver tentando obter um elemento específico em um nível mais baixo, você deve iniciar sua pesquisa a partir da janela de aplicativo ou de um contêiner em um nível mais baixo.  
  
<a name="Using_Conditions"></a>
## <a name="conditions"></a>Condições  
 Para a maioria das [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] técnicas que você <xref:System.Windows.Automation.Condition>pode usar para recuperar elementos, você deve especificar um , que é um conjunto de critérios definindo quais elementos você deseja recuperar.  
  
 A condição mais <xref:System.Windows.Automation.Condition.TrueCondition>simples é, um objeto predefinido especificando que todos os elementos dentro do escopo de pesquisa devem ser devolvidos. <xref:System.Windows.Automation.Condition.FalseCondition>, o <xref:System.Windows.Automation.Condition.TrueCondition>inverso de , é menos útil, pois impediria qualquer elemento de ser encontrado.  
  
 Três outras condições predefinidas podem ser utilizadas <xref:System.Windows.Automation.Automation.ContentViewCondition> <xref:System.Windows.Automation.Automation.ControlViewCondition>sozinhas <xref:System.Windows.Automation.Automation.RawViewCondition>ou em combinação com outras condições: , e . <xref:System.Windows.Automation.Automation.RawViewCondition>, usado por si <xref:System.Windows.Automation.Condition.TrueCondition>só, é equivalente a, porque não filtra elementos por suas <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> propriedades ou <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> propriedades.  
  
 Outras condições são construídas <xref:System.Windows.Automation.PropertyCondition> a partir de um ou mais objetos, cada um dos quais especifica um valor de propriedade. Por exemplo, <xref:System.Windows.Automation.PropertyCondition> um pode especificar que o elemento está ativado ou que suporta um determinado padrão de controle.  
  
 As condições podem ser combinadas usando a <xref:System.Windows.Automation.AndCondition>lógica <xref:System.Windows.Automation.OrCondition>booleana através da construção de objetos de tipos, e <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>
## <a name="search-scope"></a>Escopo de pesquisa  
 As pesquisas <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> feitas <xref:System.Windows.Automation.AutomationElement.FindAll%2A> usando ou devem ter um escopo, bem como um ponto de partida.  
  
 O escopo define o espaço em torno do local de partida que deve ser pesquisado. Isso pode incluir o elemento em si, seus irmãos, seus pais, seus ancestrais, seus filhos imediatos e seus descendentes.  
  
 O escopo de uma pesquisa é definido por <xref:System.Windows.Automation.TreeScope> uma combinação de valores da enumeração.  
  
<a name="Finding_a_Known_Element"></a>
## <a name="finding-a-known-element"></a>Encontrando um elemento conhecido  
 Para encontrar um elemento conhecido, identificado por sua <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>ou alguma outra propriedade <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou combinação de propriedades, é mais fácil usar o método. Se o elemento procurado for uma janela de aplicativo, <xref:System.Windows.Automation.AutomationElement.RootElement%2A>o ponto de partida da pesquisa pode ser o .  
  
 Essa forma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de encontrar elementos é mais útil em cenários de teste automatizados.  
  
<a name="Finding_Elements_in_a_Subtree"></a>
## <a name="finding-elements-in-a-subtree"></a>Encontrando elementos em uma subárvore  
 Para encontrar todos os elementos que atendem a <xref:System.Windows.Automation.AutomationElement.FindAll%2A>critérios específicos que estão relacionados a um elemento conhecido, você pode usar . Por exemplo, você pode usar este método para recuperar itens de lista ou itens de menu de uma lista ou menu, ou para identificar todos os controles em uma caixa de diálogo.  
  
<a name="Walking_a_Subtree"></a>
## <a name="walking-a-subtree"></a>Caminhando por uma Subárvore  
 Se você não tiver conhecimento prévio dos aplicativos com os seus clientes, você pode construir <xref:System.Windows.Automation.TreeWalker> uma subárvore de todos os elementos de interesse usando a classe. Seu aplicativo pode fazer isso em resposta a um evento alterado com foco; ou seja, quando um aplicativo ou controle recebe foco de entrada, o cliente de Automação de Interface do Usuário examina crianças e talvez todos os descendentes do elemento focalizado.  
  
 Outra maneira <xref:System.Windows.Automation.TreeWalker> de ser usada é identificar os ancestrais de um elemento. Por exemplo, ao subir a árvore você pode identificar a janela pai de um controle.  
  
 Você pode <xref:System.Windows.Automation.TreeWalker> usar, criando um objeto da classe (definindo <xref:System.Windows.Automation.Condition>os elementos de interesse ao passar a), <xref:System.Windows.Automation.TreeWalker>ou usando um dos seguintes objetos predefinidos que são definidos como campos de .  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Encontra apenas <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> elementos `true`cuja propriedade é.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Encontra apenas <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> elementos `true`cuja propriedade é.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Encontra todos os elementos.|  
  
 Depois de obter <xref:System.Windows.Automation.TreeWalker>um , usá-lo é simples. Basta chamar `Get` os métodos para navegar entre os elementos da subárvore.  
  
 O <xref:System.Windows.Automation.TreeWalker.Normalize%2A> método pode ser usado para navegar até um elemento na subárvore a partir de outro elemento que não faz parte da visão. Por exemplo, suponha que você tenha criado <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>uma visão de uma subárvore usando . Em seguida, seu aplicativo recebe a notificação de que uma barra de rolagem recebeu o foco de entrada. Como uma barra de rolagem não é um elemento de conteúdo, ela não está presente na sua visão da subárvore. No entanto, <xref:System.Windows.Automation.AutomationElement> você pode passar <xref:System.Windows.Automation.TreeWalker.Normalize%2A> a representação da barra de rolagem para e recuperar o ancestral mais próximo que está na exibição de conteúdo.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>
## <a name="other-ways-to-retrieve-an-element"></a>Outras maneiras de recuperar um elemento  
 Além de pesquisas e navegação, <xref:System.Windows.Automation.AutomationElement> você pode recuperar um nas seguintes maneiras.  
  
### <a name="from-an-event"></a>De um evento  
 Quando seu aplicativo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] recebe um evento, o objeto <xref:System.Windows.Automation.AutomationElement>de origem passado para o manipulador de eventos é um . Por exemplo, se você se inscreveu em eventos alterados pelo foco, a fonte passada para o seu <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> é o elemento que recebeu o foco.  
  
 Para obter mais informações, consulte [Inscreva-se em Eventos de Automação de UI](subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>De um ponto  
 Se você tiver coordenadas de tela (por exemplo, <xref:System.Windows.Automation.AutomationElement> uma posição <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> cursor), você pode recuperar uma usando o método estático.  
  
### <a name="from-a-window-handle"></a>De uma alça de janela  
 Para recuperar <xref:System.Windows.Automation.AutomationElement> um de um HWND, use o método estático. <xref:System.Windows.Automation.AutomationElement.FromHandle%2A>  
  
### <a name="from-the-focused-control"></a>Do Controle Focado  
 Você pode <xref:System.Windows.Automation.AutomationElement> recuperar um que representa o <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> controle focalizado da propriedade estática.  
  
## <a name="see-also"></a>Confira também

- [Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Navegar em elementos de automação de interface do usuário com TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
