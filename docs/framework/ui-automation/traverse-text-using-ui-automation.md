---
title: Percorrer texto usando automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: b22da8575fdc4360601946c3cba136466a393895
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042559"
---
# <a name="traverse-text-using-ui-automation"></a>Percorrer texto usando automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o para percorrer o conteúdo textual de um documento por <xref:System.Windows.Automation.Text.TextUnit> incrementos.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como atravessar o conteúdo de um provedor de texto de automação de interface do usuário. O <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> método move os <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> pontos <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> de extremidade e de um <xref:System.Windows.Automation.Text.TextPatternRange>. Normalmente, esse intervalo de texto é um intervalo de degeneramento que representa o ponto de inserção de texto.  
  
> [!NOTE]
> Como apenas objetos inseridos com base em texto são considerados parte do fluxo de texto, objetos incorporados, como imagens `Move` , não afetam ou seu valor de retorno.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Qualquer método que <xref:System.Windows.Automation.Text.TextUnit> use será adiado para o <xref:System.Windows.Automation.Text.TextUnit> próximo maior suporte se <xref:System.Windows.Automation.Text.TextUnit> o dado não for suportado pelo controle.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextPattern de automação de interface do usuário](ui-automation-textpattern-overview.md)
- [Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário](add-content-to-a-text-box-using-ui-automation.md)
- [Localizar e destacar texto usando automação de interface do usuário](find-and-highlight-text-using-ui-automation.md)
- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
