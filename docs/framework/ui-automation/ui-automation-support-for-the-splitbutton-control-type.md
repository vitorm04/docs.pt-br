---
title: Suporte de automação de interface de usuário para o tipo de controle SplitButton
ms.date: 03/30/2017
helpviewer_keywords:
- Split Button control type
- control types, Split Button
- UI Automation, Split Button control type
ms.assetid: 14b05ccf-bcd8-4045-9bae-f7679cd98711
ms.openlocfilehash: 7e8a8ec53a46d28bc37c7061332e18b39de450cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954681"
---
# <a name="ui-automation-support-for-the-splitbutton-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle SplitButton
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o suporte para o tipo de controle SplitButton. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar a <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , valores de propriedade e padrões de controle.  
  
 O controle botão de divisão habilita a capacidade de executar uma ação em um controle e expandir o controle para ver uma lista de outras ações possíveis que podem ser executadas.  
  
 As seções a seguir definem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a estrutura de árvore, as propriedades, os padrões de controle e os eventos necessários para o tipo de controle SplitButton. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]botão de divisão [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], seja, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou.  
  
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessária  
 A tabela a seguir descreve a exibição de controle e a exibição de conteúdo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore que pertence aos controles de botão de divisão e descreve o que pode ser contido em cada exibição. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a árvore, consulte [visão geral da árvore de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|SplitButton<br /><br /> <ul><li>Imagem (0 ou 1)</li><li>Texto (0 ou 1)</li><li>Botão (1 ou 2)<br /><br /> <ul><li>O menu (0 ou 1; é exibido como filho do botão que dá suporte ao padrão ExpandCollapse)</li><li>MenuItem (1 para muitos)</li></ul></li></ul>|SplitButton<br /><br /> -MenuItem (1 para muitos)|  
  
## <a name="required-ui-automation-properties"></a>Propriedades de automação da interface do usuário necessárias  
 A tabela a seguir lista [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] as propriedades cujo valor ou definição é especialmente relevante para controles de botão de divisão. Para obter mais informações [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sobre propriedades, consulte [Propriedades de automação da interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte observações.|O valor dessa propriedade precisa ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte observações.|Com suporte se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis e você executar um teste de clique especializado, substitua e forneça um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte observações.|Se o controle puder receber o foco do teclado, ele deverá dar suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Sofrer|O nome do controle do botão de divisão é exibido no botão.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Nulo|Os controles do botão de divisão não têm um rótulo de texto estático.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|SplitButton|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"botão de divisão"|Cadeia de caracteres localizada correspondente ao tipo de controle SplitButton.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consulte observações.|O texto de ajuda pode indicar o resultado da ativação do botão de divisão, que geralmente é o mesmo tipo de informações apresentadas por meio de uma dica de ferramenta.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de botão de divisão contém informações para o usuário final.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle do botão de divisão é visível para o usuário final.|  
  
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação da interface do usuário necessários  
 A tabela a seguir lista [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os padrões de controle necessários para serem suportados pelos controles de botão de divisão. Para obter mais informações sobre padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Necessária|Os botões de divisão sempre têm uma ação padrão associada à invocação.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Necessária|Os botões de divisão sempre têm a capacidade de expandir uma lista de opções.|  
  
## <a name="required-ui-automation-events"></a>Eventos de automação da interface do usuário necessários  
 A tabela a seguir lista [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os eventos necessários para serem suportados por todos os controles de botão de divisão. Para obter mais informações sobre eventos, consulte [visão geral dos eventos de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Circunstância|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="splitbutton-control-example"></a>Exemplo de controle SplitButton  
 A imagem a seguir ilustra um tipo de controle SplitButton em um controle de grade de dados.  
  
 ![Botão de divisão](../../../docs/framework/ui-automation/media/uiauto-splitbutton-detailed.gif "uiauto_splitbutton_detailed")  
  
 A exibição de controle e a exibição de conteúdo da árvore de automação da interface do usuário que pertencem aos controles da grade de dados e do botão de divisão são exibidas abaixo. Os padrões de controle para cada elemento de automação são mostrados entre parênteses.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Exibição de controle de árvore|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Árvore-exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>SplitButton "Name" (Invoke, ExpandCollapse)</li><li>Botão "mais opções" (Invoke)<br /><br /> <ul><li>Menu</li><li>MenuItem</li><li>…</li></ul></li></ul>|<ul><li>SplitButton "Name" (Invoke, ExpandCollapse)</li><li>Botão "mais opções" (Invoke)<br /><br /> <ul><li>Menu</li><li>MenuItem</li><li>…</li></ul></li></ul>|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType.SplitButton>
- [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
