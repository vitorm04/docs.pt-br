---
title: 'Como: Alterar a ordem de colunas no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039626"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Alterar a ordem de colunas no controle DataGridView do Windows Forms usando o designer

Quando você associa um controle <xref:System.Windows.Forms.DataGridView> de Windows Forms a uma fonte de dados, a ordem de exibição das colunas geradas automaticamente é determinada pela fonte de dados. Se essa ordem não for a que preferir, você poderá alterar a ordem das colunas usando o designer. Talvez deseje adicionar colunas não associadas ao controle e alterar a ordem de exibição. Para obter informações sobre como alterar a ordem de colunas programaticamente, consulte [como: Altere a ordem das colunas no controle](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Para alterar a ordem das colunas usando o designer

1. Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Clique na seta para cima ou para baixo à direita da lista **Colunas selecionadas** até que a coluna selecionada esteja na posição desejada.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Como: Adicionar e remover colunas no controle Windows Forms DataGridView usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)
