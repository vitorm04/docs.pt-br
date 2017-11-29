---
title: Como exibir o componente PrintDialog
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e1162a4e926d5be35f8f7bb7cdeb92264f293aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
