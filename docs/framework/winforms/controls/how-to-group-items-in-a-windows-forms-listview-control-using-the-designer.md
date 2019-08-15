---
title: 'Como: Agrupar itens em um controle ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039406"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Como: Agrupar itens em um controle ListView do Windows Forms usando o Designer

O recurso de agrupamento do <xref:System.Windows.Forms.ListView> controle permite que você exiba conjuntos de itens relacionados em grupos. Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo. Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação de listas grandes ao agrupar itens em ordem alfabética, por data ou por qualquer outro agrupamento lógico. A imagem a seguir mostra alguns itens agrupados:

![Números separados em grupos ímpares e pares.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ListView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

Para habilitar o agrupamento, você deve primeiro criar um ou <xref:System.Windows.Forms.ListViewGroup> mais objetos no designer ou programaticamente. Depois que um grupo tiver sido definido, você poderá atribuir itens a ele.

> [!NOTE]
> <xref:System.Windows.Forms.ListView>os grupos estão disponíveis somente [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] em quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> o método. Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Adicionar ou remover grupos no designer

1. Na janela **Propriedades** , clique nas **reticências** (![o botão de reticências (...) no janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) botão ao lado <xref:System.Windows.Forms.ListView.Groups%2A> da propriedade.

     O **Editor de coleção de ListViewGroup** é exibido.

2. Para adicionar um grupo, clique no botão **Adicionar**. Em seguida, você pode definir as propriedades do novo grupo, como <xref:System.Windows.Forms.ListViewGroup.Header%2A> as <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> Propriedades e. Para remover um grupo, selecione-o e clique no botão **Remover**.

## <a name="to-assign-items-to-groups-in-the-designer"></a>Atribuir itens aos grupos no designer

1. Na janela **Propriedades** , clique nas **reticências** (![o botão de reticências (...) no janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) botão ao lado <xref:System.Windows.Forms.ListView.Items%2A> da propriedade.

     O **Editor de coleção de ListViewItem** é exibido.

2. Para adicionar um novo item, clique no botão **Adicionar**. Em seguida, você pode definir as propriedades do novo item, como <xref:System.Windows.Forms.ListViewItem.Text%2A> as <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> Propriedades e.

3. Selecione a <xref:System.Windows.Forms.ListViewItem.Group%2A> Propriedade e escolha um grupo na lista suspensa.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Controle ListView](listview-control-windows-forms.md)
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como: Adicionar e remover itens com o controle Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
