---
title: 'Como: Editar colunas e linhas em um controle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 2149cac7fb15052c2602ef20a6684696730aae1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294453"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Como: Editar colunas e linhas em um controle TableLayoutPanel
Você pode usar o editor de coleção do <xref:System.Windows.Forms.TableLayoutPanel> controle, chamado de **estilos de linha e coluna** caixa de diálogo para editar as linhas e colunas dos controles.  
  
> [!NOTE]
>  Se você quiser que um controle ocupe várias linhas ou colunas, defina as propriedades `RowSpan` e `ColumnSpan` do controle. Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Se você deseja alinhar um controle dentro de uma célula, ou se você quiser um controle se alongue por uma célula, use o controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade. Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-edit-rows-and-columns"></a>Editar linhas e colunas  
  
1. Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
2. Clique o <xref:System.Windows.Forms.TableLayoutPanel> glifo de smart tag do controle (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e selecione **Editar linhas e colunas** para abrir o  **Estilos de linha e coluna** caixa de diálogo. Você pode também clique com botão direito do <xref:System.Windows.Forms.TableLayoutPanel> controle e selecione **Editar linhas e colunas** no menu de atalho.  
  
3. Para adicionar ou remover colunas, selecione **Colunas** da caixa de listagem suspensa **Tipo de membro**.  
  
4. Para adicionar ou remover linhas, selecione **Linhas** da caixa de listagem suspensa **Tipo de membro**.  
  
5. Clique no botão **Adicionar** para adicionar uma linha ou coluna ao final da linha **Membro**.  
  
6. Clique no botão **Inserir** para adicionar uma linha ou coluna antes do item atualmente selecionado na lista.  
  
7. Se você estiver adicionando uma linha ou coluna, selecione o **Tipo de tamanho** para a nova linha ou coluna. Para obter mais informações, consulte <xref:System.Windows.Forms.SizeType>.  
  
8. Para remover uma linha ou coluna, clique no botão **Remover** para excluir o item selecionado no momento na lista **Membro**.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SizeType>
- [Controle TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
