---
title: 'Como: Alterar o tipo de uma coluna de DataGridView dos Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 12e6e15dd3b4e7941be198a526e8145ceb126e8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544608"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Como: Alterar o tipo de uma coluna de DataGridView dos Windows Forms usando o Designer
Às vezes, você desejará alterar o tipo de uma coluna que já foi adicionado a um Windows Forms <xref:System.Windows.Forms.DataGridView> controle. Por exemplo, talvez deseje modificar os tipos de algumas das colunas que são geradas automaticamente quando você associa o controle a uma fonte de dados. Isso é útil quando a tabela exibida contém colunas com chaves estrangeiras para linhas em uma tabela relacionada. Nesse caso, talvez você queira substituir as colunas da caixa de texto que exibem essas chaves estrangeiras com colunas de caixa de combinação que exibem os valores mais significativos da tabela relacionada.  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [como: Adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Para alterar o tipo de uma coluna usando o designer  
  
1.  Clique no glifo de marca inteligente (![glifo de Smart Tag](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito dos <xref:System.Windows.Forms.DataGridView> controle e, em seguida, selecione **Editar colunas**.  
  
2.  Selecione uma coluna na lista **Colunas Selecionadas**.  
  
3.  Na grade **Propriedades da coluna** grade, defina a propriedade `ColumnType` como o novo tipo de coluna.  
  
    > [!NOTE]
    >  A propriedade `ColumnType` é uma propriedade somente em tempo de design que indica a classe que representa o tipo de coluna. Não é uma propriedade real definida em uma classe de coluna.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Como: Criar um projeto de aplicativo do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [Como: Adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
