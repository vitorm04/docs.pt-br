---
title: Obter detalhes de atributos de texto misto usando automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 9f2cba1f602cedf3a13bd909b4dc2f1a7b4ab972
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443116"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Obter detalhes de atributos de texto misto usando automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para obter detalhes de atributo de texto de um intervalo de texto que abrange vários valores de atributo. Um intervalo de texto pode corresponder ao local atual do cursor (ou degenerar a seleção) dentro de um documento, uma seleção de texto contígua, uma coleção de seleções de texto não contíguos ou todo o conteúdo textual de um documento.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como obter o <xref:System.Windows.Automation.TextPattern.FontNameAttribute> de um intervalo de texto em que <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> retorna um objeto <xref:System.Windows.Automation.TextPattern.MixedAttributeValue>.  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 O padrão de controle de <xref:System.Windows.Automation.TextPattern>, em conjunto com a classe <xref:System.Windows.Automation.Text.TextPatternRange>, dá suporte a atributos, propriedades e métodos de texto básico. Para funcionalidade específica de controle que não tem suporte pelo <xref:System.Windows.Automation.TextPattern> ou <xref:System.Windows.Automation.Text.TextPatternRange>, a classe <xref:System.Windows.Automation.AutomationElement> fornece métodos para um cliente de automação de interface do usuário acessar o modelo de objeto nativo correspondente.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextPattern de automação de interface do usuário](ui-automation-textpattern-overview.md)
- [Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário](add-content-to-a-text-box-using-ui-automation.md)
- [Localizar e destacar texto usando automação de interface do usuário](find-and-highlight-text-using-ui-automation.md)
- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Obter atributos de texto usando automação de interface do usuário](obtain-text-attributes-using-ui-automation.md)
