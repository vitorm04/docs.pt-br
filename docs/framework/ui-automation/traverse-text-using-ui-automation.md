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
ms.openlocfilehash: 71df7c8f9dde388ffc4445389e105a4ad686539f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441868"
---
# <a name="traverse-text-using-ui-automation"></a>Percorrer texto usando automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para percorrer o conteúdo textual de um documento por <xref:System.Windows.Automation.Text.TextUnit> incrementos.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como atravessar o conteúdo de um provedor de texto de automação de interface do usuário. O método <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> move os pontos de extremidade <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> e <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> de um <xref:System.Windows.Automation.Text.TextPatternRange>. Normalmente, esse intervalo de texto é um intervalo de degeneramento que representa o ponto de inserção de texto.  
  
> [!NOTE]
> Como apenas objetos inseridos com base em texto são considerados parte do fluxo de texto, objetos incorporados, como imagens, não afetam `Move` ou seu valor de retorno.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Qualquer método que use <xref:System.Windows.Automation.Text.TextUnit> será adiado para o maior <xref:System.Windows.Automation.Text.TextUnit> com suporte se o <xref:System.Windows.Automation.Text.TextUnit> especificado não for suportado pelo controle.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextPattern de automação de interface do usuário](ui-automation-textpattern-overview.md)
- [Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário](add-content-to-a-text-box-using-ui-automation.md)
- [Localizar e destacar texto usando automação de interface do usuário](find-and-highlight-text-using-ui-automation.md)
- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
