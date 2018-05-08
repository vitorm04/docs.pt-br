---
title: Como editar colunas e linhas em um controle TableLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 763d5df6c49d45f7ee305f4a3be0a1f0a2539872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Como editar colunas e linhas em um controle TableLayoutPanel
Você pode usar o editor de coleção do <xref:System.Windows.Forms.TableLayoutPanel> controle, chamado de **estilos de linha e coluna** caixa de diálogo para editar as linhas e colunas dos controles.  
  
> [!NOTE]
>  Se você quiser que um controle ocupe várias linhas ou colunas, defina as propriedades `RowSpan` e `ColumnSpan` do controle. Para obter mais informações, consulte [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Se você deseja alinhar um controle dentro de uma célula, ou se você desejar um controle se alongue em uma célula, use o controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade. Para obter mais informações, consulte [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-edit-rows-and-columns"></a>Editar linhas e colunas  
  
1.  Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2.  Clique o <xref:System.Windows.Forms.TableLayoutPanel> glifo de marca inteligente do controle (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e selecione **Editar linhas e colunas** para abrir o  **Estilos de linha e coluna** caixa de diálogo. Você pode também clique com botão direito do <xref:System.Windows.Forms.TableLayoutPanel> controle e selecione **Editar linhas e colunas** no menu de atalho.  
  
3.  Para adicionar ou remover colunas, selecione **Colunas** da caixa de listagem suspensa **Tipo de membro**.  
  
4.  Para adicionar ou remover linhas, selecione **Linhas** da caixa de listagem suspensa **Tipo de membro**.  
  
5.  Clique no botão **Adicionar** para adicionar uma linha ou coluna ao final da linha **Membro**.  
  
6.  Clique no botão **Inserir** para adicionar uma linha ou coluna antes do item atualmente selecionado na lista.  
  
7.  Se você estiver adicionando uma linha ou coluna, selecione o **Tipo de tamanho** para a nova linha ou coluna. Para obter mais informações, consulte <xref:System.Windows.Forms.SizeType>.  
  
8.  Para remover uma linha ou coluna, clique no botão **Remover** para excluir o item selecionado no momento na lista **Membro**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.SizeType>  
 [Controle TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
