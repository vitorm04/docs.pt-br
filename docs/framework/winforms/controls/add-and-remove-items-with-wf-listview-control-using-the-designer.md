---
title: Adicionar e remover itens com controle ListView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732303"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Como adicionar e remover itens com o componente ListView dos Windows Forms usando o designer

O processo de adicionar um item a um controle de <xref:System.Windows.Forms.ListView> de Windows Forms consiste principalmente em especificar o item e atribuir propriedades a ele. A adição ou remoção de itens de lista pode ser feita a qualquer momento.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.ListView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-items-using-the-designer"></a>Para adicionar ou remover itens usando o designer

1. Selecione o controle <xref:System.Windows.Forms.ListView>.

2. Na janela **Propriedades** , clique nas **reticências** (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Items%2A>.

     O **Editor de coleção de ListViewItem** é exibido.

3. Para adicionar um item, clique no botão **Adicionar**. Em seguida, você pode definir as propriedades do novo item, como as propriedades <xref:System.Windows.Forms.ListView.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.

4. Para remover um item, selecione-o e clique no botão **Remover**.

## <a name="see-also"></a>Veja também

- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como adicionar colunas ao controle ListView do Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Como Exibir Subitens em Colunas com o Controle ListView dos Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Como Exibir Ícones do Controle ListView dos Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Como agrupar itens em um controle ListView dos Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
