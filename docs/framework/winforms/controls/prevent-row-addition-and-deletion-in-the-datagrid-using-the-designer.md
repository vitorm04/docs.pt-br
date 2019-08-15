---
title: 'Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 20f9b85dc48ccd634468d0fed000120723f8ee5c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038198"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms usando o designer
Às vezes, você desejará impedir que os usuários insiram novas linhas de dados ou exclua linhas existentes no seu <xref:System.Windows.Forms.DataGridView> controle. Novas linhas são inseridas na linha especial para novos registros na parte inferior do controle. Quando você desabilitar a adição de linha, a linha para novos registros não será exibida. Em seguida, você pode deixar o controle totalmente somente leitura desabilitando a exclusão de linha e a edição de célula.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-prevent-row-addition-and-deletion"></a>Para evitar a exclusão e adição de linha

- Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e desmarque as caixas de seleção **habilitar adição** e **Habilitar exclusão** .

    > [!NOTE]
    >  Para tornar o controle somente leitura inteiramente, desmarque também a caixa de seleção **Habilitar Edição**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)
