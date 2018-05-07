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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 66ae453a8b82ea78acfb0dc423bce546324f901f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-properties-for-clients"></a>Automação de Propriedades de Interface de Usuário para Clientes.
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral apresenta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades conforme eles são expostos para aplicativos de cliente de automação de interface do usuário.  
  
 Propriedades em <xref:System.Windows.Automation.AutomationElement> objetos contêm informações sobre [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos, geralmente controles. As propriedades de um <xref:System.Windows.Automation.AutomationElement> são genérico; o que é, não é específico a um tipo de controle. Muitas dessas propriedades são expostas no <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> estrutura.  
  
 Padrões de controle também têm propriedades. As propriedades dos padrões de controle são específicas para o padrão. Por exemplo, <xref:System.Windows.Automation.ScrollPattern> tem propriedades que permitem que um aplicativo cliente para descobrir se uma janela é rolável vertical ou horizontalmente, e quais são os tamanhos de exibição atual e as posições de rolagem. Padrões de controle expõem todas as suas propriedades por meio de uma estrutura; Por exemplo, <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades são somente leitura. Para definir propriedades de um controle, você deve usar os métodos do padrão de controle apropriado. Por exemplo, use <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> para alterar os valores de posição de uma janela rolável.  
  
 Para melhorar o desempenho, os valores de propriedade de controles e padrões de controle pode ser armazenados em cache quando <xref:System.Windows.Automation.AutomationElement> objetos são recuperados. Para obter mais informações, consulte [cache em clientes de automação de interface do usuário](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
<a name="Property_IDs"></a>   
## <a name="property-ids"></a>IDs de propriedade  
 Propriedade [!INCLUDE[TLA#tla_id#plural](../../../includes/tlasharptla-idsharpplural-md.md)] são valores únicos e constantes que são encapsulados em <xref:System.Windows.Automation.AutomationProperty> objetos. Aplicativos de cliente de automação de interface de usuário obtém esses [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] do <xref:System.Windows.Automation.AutomationElement> de classe ou de apropriado classe de controle padrão, como <xref:System.Windows.Automation.ScrollPattern>. Provedores de automação de interface do usuário obtêm-los de <xref:System.Windows.Automation.AutomationElementIdentifiers> ou de um controle padrão, como classes de identificadores, <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 O valor numérico <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> de um <xref:System.Windows.Automation.AutomationProperty> é usado pelos provedores para identificar as propriedades que estão sendo consultadas no <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> método. Em geral, os aplicativos cliente não precisam examinar o <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. O <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> é usado apenas para fins de depuração e diagnósticos.  
  
<a name="Property_Conditions"></a>   
## <a name="property-conditions"></a>Condições de propriedade  
 A propriedade [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] são usados para construir <xref:System.Windows.Automation.PropertyCondition> objetos usados para localizar <xref:System.Windows.Automation.AutomationElement> objetos. Por exemplo, pode ser conveniente localizar um <xref:System.Windows.Automation.AutomationElement> que tem um determinado nome, ou todos os controles que estão habilitados. Cada <xref:System.Windows.Automation.PropertyCondition> Especifica um <xref:System.Windows.Automation.AutomationProperty> identificador e o valor que a propriedade deve corresponder.  
  
 Para obter mais informações, consulte os seguintes tópicos de referência:  
  
-   <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
-   <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
<a name="Retrieving_Properties"></a>   
## <a name="retrieving-properties"></a>Recuperando propriedades  
 Algumas propriedades de <xref:System.Windows.Automation.AutomationElement> e todas as propriedades de um padrão de controle são expostas como propriedades aninhadas do `Current` ou `Cached` propriedade o <xref:System.Windows.Automation.AutomationElement> ou objeto de padrão de controle.  
  
 Além disso, qualquer <xref:System.Windows.Automation.AutomationElement> ou a propriedade padrão, incluindo uma propriedade que não está disponível no controle de <xref:System.Windows.Automation.AutomationElement.Cached%2A> ou <xref:System.Windows.Automation.AutomationElement.Current%2A> estrutura, pode ser recuperada usando um dos seguintes métodos:  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Esses métodos oferecem um pouco melhor desempenho bem como acesso a toda a gama de propriedades.  
  
 O exemplo de código a seguir mostra duas maneiras de recuperar uma propriedade em um <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Para recuperar as propriedades dos padrões de controle com suporte a <xref:System.Windows.Automation.AutomationElement>, você não precisa recuperar o objeto de padrão de controle. Basta passe um dos identificadores de propriedade padrão para o método.  
  
 O exemplo de código a seguir mostra duas maneiras de recuperar uma propriedade em um padrão de controle.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 O `Get` métodos retornam um <xref:System.Object>. O aplicativo deve converter o objeto retornado para o tipo apropriado antes de usar o valor.  
  
<a name="_Default_Property_Values"></a>   
## <a name="default-property-values"></a>Valores de propriedade padrão  
 Se um provedor de automação de interface do usuário implementa uma propriedade, o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistema é capaz de fornecer um valor padrão. Por exemplo, se o provedor para um controle não oferece suporte para a propriedade identificada por <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] retorna uma cadeia de caracteres vazia. Da mesma forma, se o provedor não oferece suporte a propriedade identificada por <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] retorna `false`.  
  
 Você pode alterar esse comportamento usando o <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> sobrecargas do método. Quando você especifica `true` como o segundo parâmetro, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] não retorna um valor padrão, mas em vez disso, retorna o valor especial <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 O exemplo de código a seguir tenta recuperar uma propriedade de um elemento, e se não há suporte para a propriedade, será usado um valor definido pelo aplicativo.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Para descobrir quais propriedades são suportadas por um elemento, use <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Isso retorna uma matriz de <xref:System.Windows.Automation.AutomationProperty> identificadores.  
  
<a name="Property_changed_Events"></a>   
## <a name="property-changed-events"></a>Eventos de propriedade alterada  
 Quando um valor de propriedade em uma <xref:System.Windows.Automation.AutomationElement> ou padrão de controle for alterada, um evento é gerado. Um aplicativo pode assinar esses eventos chamando <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, fornecendo uma matriz de <xref:System.Windows.Automation.AutomationProperty> identificadores como o último parâmetro para especificar as propriedades de interesse.  
  
 No <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, você pode identificar a propriedade que foi alterada, verificando o <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> membro dos argumentos do evento. Os argumentos também contêm os valores novos e antigos do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedade foi alterada. Esses valores são do tipo <xref:System.Object> e devem ser convertidos para o tipo correto antes de serem usados.  
  
<a name="Additional_AutomationElement_Properties"></a>   
## <a name="additional-automationelement-properties"></a>Propriedades adicionais AutomationElement  
 Além de <xref:System.Windows.Automation.AutomationElement.Current%2A> e <xref:System.Windows.Automation.AutomationElement.Cached%2A> estruturas de propriedade <xref:System.Windows.Automation.AutomationElement> tem as seguintes propriedades são recuperadas através de acessadores de propriedade simples.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Uma coleção de filhos <xref:System.Windows.Automation.AutomationElement> objetos que estão no cache.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Um <xref:System.Windows.Automation.AutomationElement> objeto pai que está no cache.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Propriedade estática) O <xref:System.Windows.Automation.AutomationElement> que tem o foco de entrada.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Propriedade estática) A raiz <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Consulte também  
 [Armazenamento em cache em clientes de automação de interface do usuário](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Assinar eventos de automação de interface do usuário](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
