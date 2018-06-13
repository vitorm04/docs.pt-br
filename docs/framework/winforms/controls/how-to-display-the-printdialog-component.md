---
title: Como exibir o componente PrintDialog
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: d8765187522f8becf24b519434b7c170c1c755b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532181"
---
# <a name="how-to-display-the-printdialog-component"></a>Como exibir o componente PrintDialog
O <xref:System.Windows.Forms.PrintDialog> componente é a caixa de diálogo de impressão padrão do Windows que muitos dos seus usuários estarão familiarizados com. Como os usuários serão imediatamente confortáveis com ele, seria útil para você usar o <xref:System.Windows.Forms.PrintDialog> componente.  
  
### <a name="to-display-the-printdialog-component"></a>Para exibir o componente PrintDialog  
  
-   Chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A> método de dentro do código do seu aplicativo.  
  
     Assim que o componente for exibido, os usuários irá interagir com ele, definindo as propriedades do trabalho de impressão. Eles são salvos no <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` classe (e o <xref:System.Drawing.Printing.PageSettings> classe, se o usuário acessa o [componente PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) por meio de <xref:System.Windows.Forms.PrintDialog> componente) associado a esse trabalho de impressão. Em seguida, você pode fazer chamadas para as propriedades que eles definidos para determinar as especificações do trabalho de impressão.  
  
## <a name="see-also"></a>Consulte também  
 [Como Criar Trabalhos de Impressão Padrão dos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Como Capturar a Entrada do Usuário de um PrintDialog em Tempo de Execução](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [Controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Componente PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)
