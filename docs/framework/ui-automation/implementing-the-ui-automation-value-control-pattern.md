---
title: Implementando o Padrão Controle de Value de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: 54991ce16aa905f4138013944fb8b5a317675d9b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043156"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementando o Padrão Controle de Value de Automação de Interface de Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IValueProvider>, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.ValuePattern> padrão de controle é usado para dar suporte a controles que têm um valor intrínseco que não abrange um intervalo e que pode ser representado como uma cadeia de caracteres. Essa cadeia de caracteres pode ser editável, dependendo do controle e de suas configurações. Para obter exemplos de controles que implementam esse padrão, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de valor, observe as seguintes diretrizes e convenções:  
  
- Controles como <xref:System.Windows.Automation.ControlType.ListItem> e <xref:System.Windows.Automation.ControlType.TreeItem> devem oferecer suporte <xref:System.Windows.Automation.ValuePattern> se o valor de qualquer um dos itens for editável, independentemente do modo de edição atual do controle. O controle pai também deve oferecer <xref:System.Windows.Automation.ValuePattern> suporte se os itens filho forem editáveis.  
  
 ![Item de lista editável.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Exemplo de um item de lista editável  
  
- Os controles de edição de linha única dão suporte ao acesso programático <xref:System.Windows.Automation.Provider.IValueProvider>a seu conteúdo implementando. No entanto, os controles de edição de várias <xref:System.Windows.Automation.Provider.IValueProvider>linhas não são implementados; em vez disso, <xref:System.Windows.Automation.Provider.ITextProvider>eles fornecem acesso ao seu conteúdo implementando.  
  
- Para recuperar o conteúdo textual de um controle de edição de várias linhas, o controle deve <xref:System.Windows.Automation.Provider.ITextProvider>implementar. No entanto, <xref:System.Windows.Automation.Provider.ITextProvider> o não oferece suporte à definição do valor de um controle.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>o não oferece suporte à recuperação de informações de formatação ou valores de subcadeias. Implemente <xref:System.Windows.Automation.Provider.ITextProvider> nesses cenários.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>deve ser implementado por controles como o controle de seleção de **seletor de cor** de (ilustrado abaixo), que dá suporte ao mapeamento de cadeia de [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] caracteres entre um valor de cor (por exemplo, "amarelo") e uma estrutura RGB interna equivalente.  
  
 ![Seletor de cores com amarelo realçado.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemplo de mapeamento de cadeia de caracteres de amostra de cor  
  
- Um controle deve ter seu <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> definido como `true` e seu <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> definido como `false` antes de permitir uma chamada <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>para.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Membros necessários para IValueProvider  
 As propriedades e os métodos a seguir são necessários <xref:System.Windows.Automation.Provider.IValueProvider>para implementar o.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Método|Nenhum|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Se informações específicas de localidade forem passadas para um controle em um formato incorreto, como uma data formatada incorretamente.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Se um novo valor não puder ser convertido de uma cadeia de caracteres em um formato reconhecido pelo controle.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Quando é feita uma tentativa de manipular um controle que não está habilitado.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Exemplo de inserção de texto do ValuePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
