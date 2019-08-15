---
title: 'Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: d88d658b31c87e7ae89bfb4a11fe794bfbb0e848
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040105"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o designer
O controle <xref:System.Windows.Forms.DataGridView> de Windows Forms deve conter colunas para exibir dados. Para preencher o controle manualmente é preciso adicionar as colunas. De forma alternativa, é possível associar o controle a uma fonte de dados, que gera e preenche as colunas automaticamente. Se a fonte de dados contém mais colunas do que se deseja exibir, remova as colunas indesejadas.

 Os procedimentos a seguir exigem um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-add-a-column-using-the-designer"></a>Para adicionar uma coluna usando o designer

1. Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **adicionar coluna**.

2. Na caixa de diálogo **Adicionar Coluna**, escolha a opção **Coluna de Associação de Dados** e selecione uma coluna da fonte de dados, ou escolha a opção **Coluna Não Associada** e defina a coluna usando os campos fornecidos.

3. Clique no botão **Adicionar** para adicionar a coluna, fazendo com que ela apareça no designer se as colunas existentes não preencherem ainda o controle da área de exibição.

    > [!NOTE]
    >  É possível modificar propriedades da coluna na caixa de diálogo **Editar Colunas**, que pode ser acessada na marca inteligente do controle.

## <a name="to-remove-a-column-using-the-designer"></a>Para remover uma coluna usando o designer

1. Escolha **Editar Colunas** na marca inteligente do controle.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Clique no botão **Remover** para excluir a coluna, fazendo com que ela desapareça do designer.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)
