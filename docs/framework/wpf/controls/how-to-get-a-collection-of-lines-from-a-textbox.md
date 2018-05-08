---
title: Como obter uma coleção de linhas a partir de um TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 64187527da3cfb97343e2036338822d479dd997a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Como obter uma coleção de linhas a partir de um TextBox
Este exemplo mostra como obter um conjunto de linhas de texto de um <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método simple que usa um <xref:System.Windows.Controls.TextBox> como o argumento e retorna um <xref:System.Collections.Specialized.StringCollection> contendo as linhas do texto no **caixa de texto**.  O <xref:System.Windows.Controls.TextBox.LineCount%2A> propriedade é usada para determinar quantas linhas estão atualmente no **TextBox**e o <xref:System.Windows.Controls.TextBox.GetLineText%2A> método é usado para extrair cada linha e adicioná-lo à coleção de linhas.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
