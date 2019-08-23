---
title: Automação de Propriedades de Interface de Usuário para Clientes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
ms.openlocfilehash: 6f02a4825206da0dd4949083cc54f555a8ae40b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914451"
---
# <a name="ui-automation-properties-for-clients"></a>Automação de Propriedades de Interface de Usuário para Clientes.
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Esta visão geral apresenta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] as propriedades conforme elas são expostas aos aplicativos cliente de automação da interface do usuário.  
  
 Propriedades em <xref:System.Windows.Automation.AutomationElement> objetos contêm informações sobre [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos, geralmente controles. As propriedades de um <xref:System.Windows.Automation.AutomationElement> são genéricas, ou seja, não específicas de um tipo de controle. Muitas dessas propriedades são expostas na <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> estrutura.  
  
 Os padrões de controle também têm propriedades. As propriedades dos padrões de controle são específicas do padrão. Por exemplo, <xref:System.Windows.Automation.ScrollPattern> tem propriedades que permitem que um aplicativo cliente descubra se uma janela é vertical ou horizontalmente rolável e quais são os tamanhos de exibição e as posições de rolagem atuais. Padrões de controle expõem todas as suas propriedades por meio de uma estrutura; por exemplo, <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]as propriedades são somente leitura. Para definir as propriedades de um controle, você deve usar os métodos do padrão de controle apropriado. Por exemplo, use <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> para alterar os valores de posição de uma janela de rolagem.  
  
 Para melhorar o desempenho, os valores de propriedade de controles e padrões de controle podem <xref:System.Windows.Automation.AutomationElement> ser armazenados em cache quando objetos são recuperados. Para obter mais informações, consulte [Caching em clientes de automação da interface do usuário](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>IDs de propriedade  
 Identificadores de propriedade (IDs) são valores exclusivos e constantes encapsulados em <xref:System.Windows.Automation.AutomationProperty> objetos. Os aplicativos cliente de automação da interface do usuário <xref:System.Windows.Automation.AutomationElement> obtêm essas IDs da classe ou da classe de padrão <xref:System.Windows.Automation.ScrollPattern>de controle apropriada, como. Os provedores de automação de interface <xref:System.Windows.Automation.AutomationElementIdentifiers> do usuário os obtêm de ou para uma das classes de identificadores de padrão de controle, <xref:System.Windows.Automation.ScrollPatternIdentifiers>como.  
  
 O numérico <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> de um <xref:System.Windows.Automation.AutomationProperty> é usado pelos provedores para identificar as propriedades que estão sendo <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> consultadas no método. Em geral, os aplicativos cliente não precisam examinar o <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. O <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> é usado apenas para fins de depuração e diagnóstico.  
  
## <a name="property-conditions"></a>Condições de propriedade  
 As IDs de propriedade são usadas na construção <xref:System.Windows.Automation.PropertyCondition> de objetos usados para <xref:System.Windows.Automation.AutomationElement> localizar objetos. Por exemplo, talvez você queira encontrar um <xref:System.Windows.Automation.AutomationElement> que tenha um determinado nome ou todos os controles que estão habilitados. Cada <xref:System.Windows.Automation.PropertyCondition> especifica um <xref:System.Windows.Automation.AutomationProperty> identificador e o valor que a propriedade deve corresponder.  
  
 Para obter mais informações, consulte os seguintes tópicos de referência:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Recuperando propriedades  
 Algumas propriedades de <xref:System.Windows.Automation.AutomationElement> e todas as propriedades de uma classe de padrão de controle são expostas `Current` como `Cached` propriedades aninhadas <xref:System.Windows.Automation.AutomationElement> da propriedade ou do objeto de padrão de controle ou.  
  
 Além disso, qualquer <xref:System.Windows.Automation.AutomationElement> propriedade ou padrão de controle, incluindo uma propriedade que não está disponível <xref:System.Windows.Automation.AutomationElement.Cached%2A> na estrutura <xref:System.Windows.Automation.AutomationElement.Current%2A> ou, pode ser recuperada usando um dos seguintes métodos:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Esses métodos oferecem um desempenho ligeiramente melhor, bem como o acesso à gama completa de propriedades.  
  
 O exemplo de código a seguir mostra as duas maneiras de recuperar uma propriedade em <xref:System.Windows.Automation.AutomationElement>um.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Para recuperar propriedades de padrões de controle com suporte <xref:System.Windows.Automation.AutomationElement>no, não é necessário recuperar o objeto de padrão de controle. Basta passar um dos identificadores de propriedade de padrão para o método.  
  
 O exemplo de código a seguir mostra as duas maneiras de recuperar uma propriedade em um padrão de controle.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 Os `Get` métodos retornam <xref:System.Object>um. O aplicativo deve converter o objeto retornado para o tipo apropriado antes de usar o valor.  
  
## <a name="default-property-values"></a>Valores de propriedade padrão  
 Se um provedor de automação de interface do usuário não implementar uma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedade, o sistema será capaz de fornecer um valor padrão. Por exemplo, se o provedor de um controle não oferecer suporte à propriedade identificada <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>por [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , o retornará uma cadeia de caracteres vazia. Da mesma forma, se o provedor não oferecer suporte à propriedade <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>identificada `false`por, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] retorna.  
  
 Você pode alterar esse comportamento usando as sobrecargas de <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> método e. <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> Quando você especifica `true` como o segundo parâmetro, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o não retorna um valor padrão, mas, em vez disso, <xref:System.Windows.Automation.AutomationElement.NotSupported>retorna o valor especial.  
  
 O código de exemplo a seguir tenta recuperar uma propriedade de um elemento e, se a propriedade não tiver suporte, um valor definido pelo aplicativo será usado em seu lugar.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Para descobrir quais propriedades são suportadas por um elemento <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>, use. Isso retorna uma matriz de <xref:System.Windows.Automation.AutomationProperty> identificadores.  
  
## <a name="property-changed-events"></a>Eventos de alteração de propriedade  
 Quando um valor de propriedade em <xref:System.Windows.Automation.AutomationElement> um padrão de controle ou é alterado, um evento é gerado. Um aplicativo pode assinar esses eventos chamando <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, fornecendo uma matriz de <xref:System.Windows.Automation.AutomationProperty> identificadores como o último parâmetro, a fim de especificar as propriedades de interesse.  
  
 No, você pode identificar a propriedade que foi alterada verificando o <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> membro dos argumentos do evento. <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler> Os argumentos também contêm os valores novos e antigos da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedade que foi alterada. Esses valores são do tipo <xref:System.Object> e devem ser convertidos para o tipo correto antes de serem usados.  
  
## <a name="additional-automationelement-properties"></a>Propriedades de AutomationElement adicionais  
 Além das estruturas de <xref:System.Windows.Automation.AutomationElement.Current%2A> propriedade <xref:System.Windows.Automation.AutomationElement.Cached%2A> e, <xref:System.Windows.Automation.AutomationElement> o tem as seguintes propriedades, que são recuperadas por meio de acessadores de propriedade simples.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Uma coleção de objetos <xref:System.Windows.Automation.AutomationElement> filho que estão no cache.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Um <xref:System.Windows.Automation.AutomationElement> objeto pai que está no cache.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Propriedade estática) O <xref:System.Windows.Automation.AutomationElement> que tem o foco de entrada.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Propriedade estática) A raiz <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Consulte também

- [Armazenamento em cache em clientes de automação de interface do usuário](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [Assinar eventos de automação de interface do usuário](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
