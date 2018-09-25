---
title: Implementando o Padrão Controle de Value de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b45ea5f032b0315de2c37e65f61a30ab4dc13e49
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070364"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementando o Padrão Controle de Value de Automação de Interface de Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IValueProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.ValuePattern> padrão de controle é usado para dar suporte a controles que têm um valor intrínseco não abrangem um intervalo e que pode ser representado como uma cadeia de caracteres. Essa cadeia de caracteres pode ser editável, dependendo do controle e suas configurações. Para obter exemplos de controles que implementam esse padrão, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de valor, observe as seguintes diretrizes e convenções:  
  
-   Controles como <xref:System.Windows.Automation.ControlType.ListItem> e <xref:System.Windows.Automation.ControlType.TreeItem> deve oferecer suporte a <xref:System.Windows.Automation.ValuePattern> se o valor de qualquer um dos itens for editável, independentemente do atual modo de edição do controle. O controle pai também deve suportar <xref:System.Windows.Automation.ValuePattern> se os itens filhos são editáveis.  
  
 ![Item de lista editável. ](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Exemplo de um Item de lista editável  
  
-   Controles de edição de linha única oferecem suporte a acesso programático aos seus conteúdos implementando <xref:System.Windows.Automation.Provider.IValueProvider>. No entanto, os controles de edição de várias linhas não implementam <xref:System.Windows.Automation.Provider.IValueProvider>; em vez disso, eles oferecem acesso a seus conteúdos implementando <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
-   Para recuperar o conteúdo textual de um controle de edição de várias linhas, o controle deve implementar <xref:System.Windows.Automation.Provider.ITextProvider>. No entanto, <xref:System.Windows.Automation.Provider.ITextProvider> não oferece suporte para a definição do valor de um controle.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> não oferece suporte a recuperação de informações ou valores de subcadeia de caracteres de formatação. Implemente <xref:System.Windows.Automation.Provider.ITextProvider> nesses cenários.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> deve ser implementado por controles, como o **seletor de cor** controle de seleção do [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (ilustrado abaixo), que dá suporte ao mapeamento de cadeia de caracteres entre um valor de cor (por exemplo, "yellow") e um equivalente interno[!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]estrutura.  
  
 ![Seletor de cores com amarelo realçado. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemplo de mapeamento de cadeia de caracteres de amostra de cor  
  
-   Um controle deve ter sua <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> definido como `true` e seu <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> definido como `false` antes de permitir que uma chamada para <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Membros necessários para IValueProvider  
 As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Método|Nenhum|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Se informações específicas de localidade são passadas para um controle em um formato incorreto, como uma data formatada incorretamente.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Se um novo valor não pode ser convertido de uma cadeia de caracteres em um formato o controle reconhece.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Quando é feita uma tentativa para manipular um controle que não está habilitado.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Exemplo de inserção de TextPattern de texto](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
