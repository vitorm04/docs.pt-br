---
title: 'Como: Adicionar e remover itens com o controle ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040082"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Como: Adicionar e remover itens com o controle ListView do Windows Forms usando o Designer

O processo de adicionar um item a um controle <xref:System.Windows.Forms.ListView> de Windows Forms consiste principalmente em especificar o item e atribuir propriedades a ele. A adição ou remoção de itens de lista pode ser feita a qualquer momento.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ListView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-items-using-the-designer"></a>Para adicionar ou remover itens usando o designer

1. Selecione o <xref:System.Windows.Forms.ListView> controle.

2. Na janela **Propriedades** , clique nas **reticências** (![o botão de reticências (...) no janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) botão ao lado <xref:System.Windows.Forms.ListView.Items%2A> da propriedade.

     O **Editor de coleção de ListViewItem** é exibido.

3. Para adicionar um item, clique no botão **Adicionar**. Em seguida, você pode definir as propriedades do novo item, como <xref:System.Windows.Forms.ListView.Text%2A> as <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> Propriedades e.

4. Para remover um item, selecione-o e clique no botão **Remover**.

## <a name="see-also"></a>Consulte também

- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como: Adicionar colunas ao controle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Como: Exibir subitens em colunas com o controle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Como: Exibir ícones para o controle Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Como: Agrupar itens em um controle Windows Forms ListView](how-to-group-items-in-a-windows-forms-listview-control.md)
