---
title: 'Como: Deixar as colunas somente leitura no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: a735b9bef9f9e3488941e05b2aa9444e6ecdc4b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012874"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Deixar as colunas somente leitura no controle DataGridView do Windows Forms usando o designer
Por padrão, os usuários podem modificar o texto e dados numéricos exibidos nos formulários de Windows <xref:System.Windows.Forms.DataGridView> controle. Se quiser exibir os dados que não são destinados para modificação, você deverá tornar somente leitura as colunas que contêm os dados. Para obter informações sobre como fazer o controle totalmente somente leitura, consulte [como: Evitar a adição de linha e exclusão no Windows Forms usando o Designer de controle de DataGridView](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a>Para tornar a coluna somente leitura usando o designer  
  
1. Clique no glifo de marca inteligente (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito dos <xref:System.Windows.Forms.DataGridView> controle e, em seguida, selecione **Editar colunas**.  
  
2. Selecione uma coluna na lista **Colunas Selecionadas**.  
  
3. No **propriedades da coluna** grade, defina o <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> propriedade `true`.  
  
    > [!NOTE]
    >  Você também pode tornar uma coluna somente leitura ao adicioná-la marcando a caixa de seleção **Somente Leitura** na caixa de diálogo **Adicionar Coluna**.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como: Evitar a adição de linha e exclusão no controle DataGridView do Windows Forms usando o Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)
