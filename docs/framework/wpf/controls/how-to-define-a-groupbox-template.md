---
title: 'Como: Definir um modelo de GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: 6294a52d5914b52d191b564330f904e6a865c283
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745192"
---
# <a name="how-to-define-a-groupbox-template"></a>Como: Definir um modelo de GroupBox
Este exemplo mostra como criar um modelo para um <xref:System.Windows.Controls.GroupBox> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma <xref:System.Windows.Controls.GroupBox> modelo de controle usando um <xref:System.Windows.Controls.Grid> controle de layout. O modelo usa um <xref:System.Windows.Controls.BorderGapMaskConverter> para definir a borda da <xref:System.Windows.Controls.GroupBox> para que a borda não oculte o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> conteúdo.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.GroupBox>
- [Como: Criar uma caixa de grupo](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))
