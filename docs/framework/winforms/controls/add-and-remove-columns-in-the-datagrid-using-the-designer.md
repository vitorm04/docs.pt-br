---
title: 'Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o Designer'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 444faafcdf284d000be5daf8e97081bbfb5bb38a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716381"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o Designer
Os formulários do Windows <xref:System.Windows.Forms.DataGridView> controle deve conter colunas para exibir dados. Para preencher o controle manualmente é preciso adicionar as colunas. De forma alternativa, é possível associar o controle a uma fonte de dados, que gera e preenche as colunas automaticamente. Se a fonte de dados contém mais colunas do que se deseja exibir, remova as colunas indesejadas.  
  
 Os procedimentos a seguir exigem uma **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-column-using-the-designer"></a>Para adicionar uma coluna usando o designer  
  
1.  Clique no glifo de marca inteligente (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito dos <xref:System.Windows.Forms.DataGridView> controle e, em seguida, selecione **adicionar coluna**.  
  
2.  Na caixa de diálogo **Adicionar Coluna**, escolha a opção **Coluna de Associação de Dados** e selecione uma coluna da fonte de dados, ou escolha a opção **Coluna Não Associada** e defina a coluna usando os campos fornecidos.  
  
3.  Clique no botão **Adicionar** para adicionar a coluna, fazendo com que ela apareça no designer se as colunas existentes não preencherem ainda o controle da área de exibição.  
  
    > [!NOTE]
    >  É possível modificar propriedades da coluna na caixa de diálogo **Editar Colunas**, que pode ser acessada na marca inteligente do controle.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Para remover uma coluna usando o designer  
  
1.  Escolha **Editar Colunas** na marca inteligente do controle.  
  
2.  Selecione uma coluna na lista **Colunas Selecionadas**.  
  
3.  Clique no botão **Remover** para excluir a coluna, fazendo com que ela desapareça do designer.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGridView>
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)
