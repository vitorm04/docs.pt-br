---
title: Como adicionar colunas ao controle ListView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 4c696644e61004bcac48399ffc752e40675642fc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199862"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Como adicionar colunas ao controle ListView dos Windows Forms usando o designer
Os formulários do Windows <xref:System.Windows.Forms.ListView> controle pode exibir várias colunas para cada lista de itens na **detalhes** exibição. Você pode usar as colunas para exibir vários tipos de informações sobre cada item de lista. Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo. Para obter informações sobre como preencher as colunas depois que elas forem criadas, consulte [Como exibir subitens em colunas com o controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-columns-in-the-designer"></a>Para adicionar colunas no designer  
  
1.  No **propriedades** janela, defina o controle <xref:System.Windows.Forms.ListView.View%2A> propriedade <xref:System.Windows.Forms.View.Details>.  
  
2.  No **propriedades** janela, clique no **reticências** botão (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) próximo a o <xref:System.Windows.Forms.ListView.Columns%2A> propriedade.  
  
     O **Editor de coleção ColumnHeader** é exibido.  
  
3.  Use o botão **Adicionar** para adicionar novas colunas. Em seguida, você pode selecionar o cabeçalho da coluna e definir seu texto (a legenda da coluna), o alinhamento do texto e a largura.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Como Exibir Subitens em Colunas com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Como exibir ícones do controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
