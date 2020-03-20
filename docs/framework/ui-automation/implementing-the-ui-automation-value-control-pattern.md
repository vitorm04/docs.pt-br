---
title: Implementando o Padrão Controle de Value de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: eb77f26bbe3546a3f90804c3648f8547fb6abad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180085"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementando o Padrão Controle de Value de Automação de Interface de Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IValueProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.ValuePattern> padrão de controle é usado para suportar controles que têm um valor intrínseco que não abrange uma faixa e que pode ser representado como uma string. Esta seqüência pode ser editável, dependendo do controle e suas configurações. Para exemplos de controles que implementam esse padrão, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário.](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle de valor, observe as seguintes diretrizes e convenções:  
  
- Controles como <xref:System.Windows.Automation.ControlType.ListItem> e <xref:System.Windows.Automation.ControlType.TreeItem> devem <xref:System.Windows.Automation.ValuePattern> ser suportados se o valor de qualquer um dos itens for editável, independentemente do modo de edição atual do controle. O controle dos <xref:System.Windows.Automation.ValuePattern> pais também deve ser suportado se os itens da criança forem editáveis.  
  
 ![Item da lista editável.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Exemplo de um item de lista editável  
  
- Controles de edição de linha única suportam acesso <xref:System.Windows.Automation.Provider.IValueProvider>programático ao seu conteúdo implementando . No entanto, os controles de <xref:System.Windows.Automation.Provider.IValueProvider>edição multi-linha não são implementados; em vez disso, eles fornecem <xref:System.Windows.Automation.Provider.ITextProvider>acesso ao seu conteúdo implementando .  
  
- Para recuperar o conteúdo textual de um controle de <xref:System.Windows.Automation.Provider.ITextProvider>edição multilinha, o controle deve implementar . No <xref:System.Windows.Automation.Provider.ITextProvider> entanto, não suporta definir o valor de um controle.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>não suporta a recuperação de informações de formatação ou valores de substring. Implementar <xref:System.Windows.Automation.Provider.ITextProvider> nesses cenários.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>deve ser implementado por controles como o controle de seleção **do Color Picker** do Microsoft Word (ilustrado abaixo), que suporta mapeamento de strings entre um valor de cor (por exemplo, "amarelo") e uma estrutura RGB interna equivalente.  
  
 ![Seletor de cores com amarelo destacado.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemplo de Mapeamento de Cordas de Swatch de Cor  
  
- Um controle deve <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> ter `true` seu <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> conjunto `false` e seu <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>conjunto para antes de permitir uma chamada para .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a>Membros obrigatórios para IValueProvider  
 As seguintes propriedades e métodos <xref:System.Windows.Automation.Provider.IValueProvider>são necessários para a implementação.  
  
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
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Se as informações específicas do local forem passadas para um controle em um formato incorreto, como uma data formatada incorretamente.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Se um novo valor não puder ser convertido de uma string para um formato, o controle reconhecerá.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Quando se tenta manipular um controle que não está ativado.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Exemplo de texto de inserção de valor](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
