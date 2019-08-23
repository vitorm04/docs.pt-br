---
title: Obter detalhes de atributos de texto misto usando automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 24aad50647fc5aef5b2c2a83cbab37120eccd88c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966404"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Obter detalhes de atributos de texto misto usando automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o para obter detalhes de atributo de texto de um intervalo de texto que abrange vários valores de atributo. Um intervalo de texto pode corresponder ao local atual do cursor (ou degenerar a seleção) dentro de um documento, uma seleção de texto contígua, uma coleção de seleções de texto não contíguos ou todo o conteúdo textual de um documento.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como obter <xref:System.Windows.Automation.TextPattern.FontNameAttribute> o de um intervalo de <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> texto em <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> que retorna um objeto.  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 O <xref:System.Windows.Automation.TextPattern> padrão de controle, em conjunto com <xref:System.Windows.Automation.Text.TextPatternRange> a classe, dá suporte a atributos, propriedades e métodos de texto básico. Para funcionalidade específica de controle que não é suportada <xref:System.Windows.Automation.Text.TextPatternRange>pelo <xref:System.Windows.Automation.TextPattern> ou <xref:System.Windows.Automation.AutomationElement> , a classe fornece métodos para um cliente de automação da interface do usuário acessar o modelo de objeto nativo correspondente.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextPattern de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [Localizar e destacar texto usando automação de interface do usuário](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Obter atributos de texto usando automação de interface do usuário](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
