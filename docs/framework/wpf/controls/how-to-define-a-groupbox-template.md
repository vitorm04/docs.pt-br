---
title: Como definir um modelo de GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: a47ce896be4d1c38147584dd80b1bc841737d526
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062489"
---
# <a name="how-to-define-a-groupbox-template"></a>Como definir um modelo de GroupBox
Este exemplo mostra como criar um modelo para um <xref:System.Windows.Controls.GroupBox> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma <xref:System.Windows.Controls.GroupBox> modelo de controle usando um <xref:System.Windows.Controls.Grid> controle de layout. O modelo usa um <xref:System.Windows.Controls.BorderGapMaskConverter> para definir a borda da <xref:System.Windows.Controls.GroupBox> para que a borda não oculte o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> conteúdo.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.GroupBox>  
 [Tópicos explicativos de GroupBox](https://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
