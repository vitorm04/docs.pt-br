---
title: 'Como: Criar um controle TextBox multilinha'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 29fb4c9498fe163c36e71680242d3ef8cf98c089
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181162"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Como: Criar um controle TextBox multilinha
Este exemplo mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle expandirá automaticamente para acomodar várias linhas de texto.  
  
## <a name="example"></a>Exemplo  
 Definindo o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> de atributo para **encapsular** fará com que o texto inserido quebre para uma nova linha quando a borda da <xref:System.Windows.Controls.TextBox> controle é alcançada, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se necessário.  
  
 Definindo o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> de atributo para **verdadeira** faz com que uma nova linha seja inserida quando a tecla RETURN é pressionada, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> para incluir espaço para uma nova linha, se necessário.  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem para o <xref:System.Windows.Controls.TextBox>, de modo que o conteúdo da <xref:System.Windows.Controls.TextBox> poderá ser rolado se o <xref:System.Windows.Controls.TextBox> ultrapassar o tamanho do quadro ou janela que o contém.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.TextWrapping>
- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
