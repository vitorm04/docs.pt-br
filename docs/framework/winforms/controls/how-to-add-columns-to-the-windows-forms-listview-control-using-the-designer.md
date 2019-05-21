---
title: 'Como: Adicionar colunas ao controle ListView do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 252ed6a599ba3601344c6423385946c3dadfafaa
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960170"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Como: Adicionar colunas ao controle ListView do Windows Forms usando o Designer

Os formulários do Windows <xref:System.Windows.Forms.ListView> controle pode exibir várias colunas para cada lista de itens na **detalhes** exibição. Você pode usar as colunas para exibir vários tipos de informações sobre cada item de lista. Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo. Para obter informações sobre como popular as colunas depois que eles são criados, consulte [como: Exibir subitens em colunas com o Windows Forms controle ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).

O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-add-columns-in-the-designer"></a>Para adicionar colunas no designer

1. No **propriedades** janela, defina o controle <xref:System.Windows.Forms.ListView.View%2A> propriedade <xref:System.Windows.Forms.View.Details>.

2. No **propriedades** janela, clique no **reticências** botão (![botão do botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) lado a <xref:System.Windows.Forms.ListView.Columns%2A> propriedade .

     O **Editor de coleção ColumnHeader** é exibido.

3. Use o botão **Adicionar** para adicionar novas colunas. Em seguida, você pode selecionar o cabeçalho da coluna e definir seu texto (a legenda da coluna), o alinhamento do texto e a largura.

## <a name="see-also"></a>Consulte também

- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como: Adicionar e remover itens com o controle ListView do Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como: Exibir subitens em colunas com o controle ListView do Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Como: Exibir ícones para o controle ListView do Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
