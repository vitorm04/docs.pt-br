---
title: 'Como: Obter uma coleção de linhas de um TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052476"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Como: Obter uma coleção de linhas de um TextBox
Este exemplo mostra como obter um conjunto de linhas de texto de um <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método simple que usa um <xref:System.Windows.Controls.TextBox> como o argumento e retorna um <xref:System.Collections.Specialized.StringCollection> que contém as linhas de texto na **caixa de texto**.  O <xref:System.Windows.Controls.TextBox.LineCount%2A> propriedade é usada para determinar quantas linhas estão atualmente em de **TextBox**e o <xref:System.Windows.Controls.TextBox.GetLineText%2A> método é usado para extrair cada linha e adicioná-lo à coleção de linhas.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
