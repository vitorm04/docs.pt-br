---
title: Como agrupar itens em um controle ListView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 03958109d4daa3fc369660de66973bb659e29c60
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960183"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Como agrupar itens em um controle ListView dos Windows Forms usando o designer

O recurso de agrupamento do controle de <xref:System.Windows.Forms.ListView> permite que você exiba conjuntos de itens relacionados em grupos. Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo. Você pode usar grupos de <xref:System.Windows.Forms.ListView> para facilitar a navegação de listas grandes ao agrupar itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico. A imagem a seguir mostra alguns itens agrupados:

![Números separados em grupos ímpares e pares.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.ListView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

Para habilitar o agrupamento, você deve primeiro criar um ou mais objetos <xref:System.Windows.Forms.ListViewGroup> no designer ou programaticamente. Depois que um grupo tiver sido definido, você poderá atribuir itens a ele.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Adicionar ou remover grupos no designer

1. Na janela **Propriedades** , clique nas **reticências** (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Groups%2A>.

     O **Editor de coleção de ListViewGroup** é exibido.

2. Para adicionar um grupo, clique no botão **Adicionar**. Em seguida, você pode definir as propriedades do novo grupo, como as propriedades <xref:System.Windows.Forms.ListViewGroup.Header%2A> e <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>. Para remover um grupo, selecione-o e clique no botão **Remover**.

## <a name="to-assign-items-to-groups-in-the-designer"></a>Atribuir itens aos grupos no designer

1. Na janela **Propriedades** , clique nas **reticências** (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Items%2A>.

     O **Editor de coleção de ListViewItem** é exibido.

2. Para adicionar um novo item, clique no botão **Adicionar**. Em seguida, você pode definir as propriedades do novo item, como as propriedades <xref:System.Windows.Forms.ListViewItem.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.

3. Selecione a propriedade <xref:System.Windows.Forms.ListViewItem.Group%2A> e escolha um grupo na lista suspensa.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Controle ListView](listview-control-windows-forms.md)
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
