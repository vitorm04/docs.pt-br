---
title: Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 7479b486a0a130a95aa6dcecd5480e216bc13be2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms usando o designer
Às vezes você deseja impedir que usuários inserir novas linhas de dados ou excluir linhas existentes em seu <xref:System.Windows.Forms.DataGridView> controle. Novas linhas são inseridas na linha especial para novos registros na parte inferior do controle. Quando você desabilitar a adição de linha, a linha para novos registros não será exibida. Em seguida, você pode deixar o controle totalmente somente leitura desabilitando a exclusão de linha e a edição de célula.  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-prevent-row-addition-and-deletion"></a>Para evitar a exclusão e adição de linha  
  
-   Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, desmarque o **habilitar adicionando** e **Enable Deleting** caixas de seleção.  
  
    > [!NOTE]
    >  Para tornar o controle somente leitura inteiramente, desmarque também a caixa de seleção **Habilitar Edição**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 [Como: criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
