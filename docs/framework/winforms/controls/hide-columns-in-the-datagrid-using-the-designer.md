---
title: Como ocultar colunas no controle DataGridView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: c7362b503f16dd184be3bd04ba21a4d1eb55a390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527050"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como ocultar colunas no controle DataGridView dos Windows Forms usando o designer
Às vezes, você desejará exibir somente algumas das colunas que estão disponíveis em um Windows Forms <xref:System.Windows.Forms.DataGridView> controle. Por exemplo, talvez você queira mostrar uma coluna de salário de funcionários para usuários com credenciais de gerenciamento enquanto a oculta de outros usuários. Como alternativa, talvez você queira associar o controle a uma fonte de dados que contém várias colunas, sendo que você deseja exibir apenas algumas delas. Nesse caso, você normalmente removerá as colunas que não está interessado em exibir em vez de ocultá-las. Para saber mais, veja [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-hide-a-column-using-the-designer"></a>Para ocultar uma coluna usando o designer  
  
1.  Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, selecione **Editar colunas**.  
  
2.  Selecione uma coluna na lista **Colunas Selecionadas**.  
  
3.  No **propriedades de coluna** grade, defina o <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> propriedade `false`.  
  
    > [!NOTE]
    >  Você também pode ocultar uma coluna ao adicioná-la desmarcando a caixa de seleção **Visível** na caixa de diálogo **Adicionar Coluna**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Como: criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
