---
title: Usar a propriedade AutomationID
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: bd5985dd531b13ca91efd9c0aa7987ff6a57e56a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="use-the-automationid-property"></a>Usar a propriedade AutomationID
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico contém cenários e código de exemplo que mostram como e quando o <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> pode ser usado para localizar um elemento dentro do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> identifica exclusivamente um elemento de automação de interface do usuário de seus irmãos. Para obter mais informações sobre identificadores de propriedade relacionados à identificação de controles, consulte [visão geral de propriedades de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> não garante uma identidade exclusiva em toda a árvore; Normalmente, ele deve contêiner e informações de escopo para ser útil. Por exemplo, um aplicativo pode conter um controle de menu com vários itens de menu de nível superior que, por sua vez, têm vários itens de menu filho. Esses itens de menu secundários podem ser identificados por um esquema genérico, como "Item1", "Item 2" e assim por diante, permitindo identificadores duplicados para os filhos entre itens de menu de nível superior.  
  
## <a name="scenarios"></a>Cenários  
 Foram identificados três cenários de aplicativo de cliente automação de interface do usuário primários que exigem o uso de <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> para obter resultados precisos e consistentes ao procurar elementos.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> há suporte para todos os elementos de automação de interface do usuário na exibição de controle, exceto windows de aplicativos de nível superior, os elementos de automação de interface do usuário derivados [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controles que não têm uma ID ou X:UID e elementos de automação de interface do usuário derivados [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] controla que não tem uma ID de controle.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>Use um AutomationID exclusivo e identificável para localizar um elemento específico na árvore de automação de interface do usuário  
  
-   Usar uma ferramenta como [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] relatório o <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> de um [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elemento de interesse. Esse valor pode ser copiado e colado em um aplicativo cliente como um script de teste para testes automatizados subsequentes. Essa abordagem reduz e simplifica o código necessário para identificar e localizar um elemento em tempo de execução.  
  
> [!CAUTION]
>  Em geral, você deve tentar obter apenas filhos diretos do <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Uma pesquisa por descendentes pode percorrer centenas ou mesmo milhares de elementos, possivelmente resultando em um estouro de pilha. Se você está tentando obter um elemento específico em um nível inferior, você deve iniciar sua pesquisa de janela do aplicativo ou de um contêiner em um nível inferior.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Usar um caminho persistente para retornar a um AutomationElement identificado anteriormente  
  
-   Aplicativos de cliente, de scripts de teste simples para registro robusto e utilitários de reprodução, podem exigir acesso aos elementos que atualmente não estão instanciados, como um arquivo de abrir a caixa de diálogo ou um item de menu e, portanto, não existem na árvore de automação de interface do usuário. Esses elementos só podem ser instanciados através da reprodução, ou "reproduzir", uma sequência específica de [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ações com o uso de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades como AutomationID, padrões de controle e ouvintes de evento. Consulte [Test Script Generator Sample](http://msdn.microsoft.com/library/028467fd-2980-4691-9522-0131dcef23a0) para obter um exemplo que usa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para gerar scripts de teste com base na interação do usuário com o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Use um caminho relativo para retornar a um AutomationElement identificado anteriormente  
  
-   Em determinadas circunstâncias, como AutomationID só tem a garantia de exclusividade entre irmãos, vários elementos na árvore de automação de interface do usuário podem ter valores de propriedade AutomationID idênticos. Nessas situações os elementos podem ser identificados exclusivamente com base em um pai e, se necessário, avô. Por exemplo, um desenvolvedor pode fornecer uma barra de menus com vários itens de menu cada com filho vários itens de menu onde os filhos são identificados com sequencial AutomationID como "Item1", "2" e assim por diante. Cada item de menu, em seguida, pode ser identificado exclusivamente por seu AutomationID junto com o AutomationID de seu pai e, se necessário, seu avô.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Localizar um elemento de automação de interface do usuário com base em uma condição de propriedade](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
