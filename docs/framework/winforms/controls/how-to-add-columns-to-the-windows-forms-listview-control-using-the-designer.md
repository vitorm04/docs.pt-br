---
title: 'Como: Adicionar colunas ao controle ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: e82fbcf63047873ebc6e5c40b8b9fbeb14a672e5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038175"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Como: Adicionar colunas ao controle ListView do Windows Forms usando o Designer

O controle <xref:System.Windows.Forms.ListView> Windows Forms pode exibir várias colunas para cada item de lista quando estiver na exibição de **detalhes** . Você pode usar as colunas para exibir vários tipos de informações sobre cada item de lista. Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo. Para obter informações sobre como preencher as colunas depois que elas são [criadas, consulte Como: Exibir subitens em colunas com o controle](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)ListView Windows Forms.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ListView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).


### <a name="to-add-columns-in-the-designer"></a>Para adicionar colunas no designer

1. Na janela **Propriedades** , defina a propriedade do <xref:System.Windows.Forms.ListView.View%2A> controle como. <xref:System.Windows.Forms.View.Details>

2. Na janela **Propriedades** , clique no botão de reticências![(o botão de reticências (...) na janela Propriedades do Visual](./media/visual-studio-ellipsis-button.png)Studio.) ao <xref:System.Windows.Forms.ListView.Columns%2A> lado da propriedade.

     O **Editor de coleção ColumnHeader** é exibido.

3. Use o botão **Adicionar** para adicionar novas colunas. Em seguida, você pode selecionar o cabeçalho da coluna e definir seu texto (a legenda da coluna), o alinhamento do texto e a largura.

## <a name="see-also"></a>Consulte também

- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como: Adicionar e remover itens com o controle Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como: Exibir subitens em colunas com o controle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Como: Exibir ícones para o controle Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
