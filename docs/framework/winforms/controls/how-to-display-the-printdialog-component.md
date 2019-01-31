---
title: Como exibir o componente PrintDialog
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 198ae75d407bd1837033a1cc186d84ff972fdc2f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285149"
---
# <a name="how-to-display-the-printdialog-component"></a>Como exibir o componente PrintDialog

O <xref:System.Windows.Forms.PrintDialog> componente é a caixa de diálogo de impressão padrão do Windows que muitos dos seus usuários estarão familiarizados com. Como os usuários serão imediatamente à vontade com ele, seria vantajoso para você usar o <xref:System.Windows.Forms.PrintDialog> componente.

## <a name="to-display-the-printdialog-component"></a>Para exibir o componente PrintDialog

- Chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A> método de dentro do código do seu aplicativo.

     Quando o componente é exibido, os usuários interagirão com ele, definindo as propriedades do trabalho de impressão. Eles são salvos na <xref:System.Drawing.Printing.PrinterSettings> classe (e o <xref:System.Drawing.Printing.PageSettings> classe, se o usuário acessa o [componente PageSetupDialog](pagesetupdialog-component-windows-forms.md) por meio do <xref:System.Windows.Forms.PrintDialog> componente) associado a esse trabalho de impressão. Em seguida, você pode fazer chamadas para as propriedades que eles definidos para determinar as especificações do trabalho de impressão.

## <a name="see-also"></a>Consulte também

- [Como: Criar trabalhos de impressão padrão do Windows Forms](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Como: Capturar a entrada do usuário de um PrintDialog em tempo de execução](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [Controle PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Componente PrintDialog](printdialog-component-windows-forms.md)
- [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md)
- [Controles dos Windows Forms](index.md)