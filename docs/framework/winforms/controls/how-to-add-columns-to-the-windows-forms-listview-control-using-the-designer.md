---
title: Adicionar colunas ao controle ListView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744612"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Como adicionar colunas ao controle ListView dos Windows Forms usando o designer

O controle de <xref:System.Windows.Forms.ListView> de Windows Forms pode exibir várias colunas para cada item de lista no modo de exibição de **detalhes** . Você pode usar as colunas para exibir vários tipos de informações sobre cada item de lista. Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo. Para obter informações sobre como preencher as colunas depois que elas forem criadas, consulte [Como exibir subitens em colunas com o controle ListView dos Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.ListView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-columns-in-the-designer"></a>Para adicionar colunas no designer

1. Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.ListView.View%2A> do controle como <xref:System.Windows.Forms.View.Details>.

2. Na janela **Propriedades** , clique no botão de **reticências** (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Columns%2A>.

     O **Editor de coleção ColumnHeader** é exibido.

3. Use o botão **Adicionar** para adicionar novas colunas. Em seguida, você pode selecionar o cabeçalho da coluna e definir seu texto (a legenda da coluna), o alinhamento do texto e a largura.

## <a name="see-also"></a>Consulte também

- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como adicionar e remover itens com o controle ListView do Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como exibir subitens em colunas com o controle ListView do Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Como exibir ícones do controle ListView do Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
