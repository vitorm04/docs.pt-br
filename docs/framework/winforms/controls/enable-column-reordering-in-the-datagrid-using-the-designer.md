---
title: Habilitar reordenação de coluna no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 14dc1081a8608c6e6add67f641c4b55825d2fc81
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626965"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como habilitar a reorganização da coluna no controle DataGridView dos Windows Forms usando o designer
Ao exibir os dados exibidos em um controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms, os usuários às vezes desejam comparar os valores em colunas específicas. Isso pode ser inconveniente se as colunas forem amplamente separadas no controle, especialmente se os usuários precisarem rolar para frente e para trás horizontalmente para ver todas as colunas nas quais estão interessadas. Você pode tornar a tarefa de comparar valores de coluna mais fácil, permitindo que os usuários reordenem as colunas. Quando você habilita a reordenação de coluna, os usuários podem mover uma coluna para uma nova posição arrastando o cabeçalho da coluna com o mouse.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-enable-column-reordering"></a>Para habilitar a reordenação de coluna

- Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e selecione **habilitar reordenação de coluna**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Como congelar colunas no controle DataGridView dos Windows Forms usando o designer](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)
