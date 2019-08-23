---
title: 'Como: Exibir uma marca de inserção em um controle ListView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: f5de00fd41b24fc1a7f1ff4484c3a126e98952a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967827"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Como: Exibir uma marca de inserção em um controle ListView do Windows Forms
A marca de inserção no <xref:System.Windows.Forms.ListView> controle mostra aos usuários o ponto em que os itens arrastados serão inseridos. Quando um usuário arrasta um item para um ponto entre dois outros itens, a marca de inserção mostra o novo local esperado do item.  
  
> [!NOTE]
> O recurso de marca de inserção está disponível [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] somente em quando o aplicativo <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> chama o método. Em sistemas operacionais anteriores, qualquer código relacionado à marca de inserção não tem nenhum efeito e a marca de inserção não será exibida. Para obter mais informações, consulte <xref:System.Windows.Forms.ListViewInsertionMark>.  
  
 A imagem a seguir mostra uma marca de inserção:  
  
 ![Captura de tela que mostra uma marca de inserção de ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")  
  
 O exemplo de código a seguir demonstra como usar esse recurso.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies Sistema e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [Controle ListView](listview-control-windows-forms.md)
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
