---
title: Obter atributos de texto usando automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: ced02347a27c85babb614cb4f0fea3248753f1b8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109950"
---
# <a name="obtain-text-attributes-using-ui-automation"></a>Obter atributos de texto usando automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ao obter atributos de texto de um intervalo de texto. Um intervalo de texto pode corresponder ao local atual do cursor (ou a seleção de degeneração) dentro de um documento, uma seleção contígua de texto, uma coleção de seleções de texto não contíguos ou todo o conteúdo textual de um documento.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como obter o <xref:System.Windows.Automation.TextPattern.FontNameAttribute> de um intervalo de texto.  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 O <xref:System.Windows.Automation.TextPattern> padrão de controle, em tandem com o <xref:System.Windows.Automation.Text.TextPatternRange> classe, dá suporte a atributos de texto básico, propriedades e métodos. Para a funcionalidade específica do controle que não é compatível com <xref:System.Windows.Automation.TextPattern> ou <xref:System.Windows.Automation.Text.TextPatternRange> o <xref:System.Windows.Automation.AutomationElement>, classe fornece métodos para um cliente de automação de interface do usuário acessar o modelo de objeto nativo correspondente.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextPattern de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Localizar e destacar texto usando automação de interface do usuário](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Obter detalhes de atributos de texto misto usando automação de interface do usuário](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
