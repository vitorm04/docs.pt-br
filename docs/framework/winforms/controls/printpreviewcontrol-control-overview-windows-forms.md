---
title: "Visão geral do controle PrintPreviewControl (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d50e772cf870d47314a25347f4909367062ffb94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>Visão geral do controle PrintPreviewControl (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> é usado para exibir um [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) como ele aparecerá quando impresso. Este controle tem botões não ou outros elementos de interface do usuário, normalmente você usar o <xref:System.Windows.Forms.PrintPreviewControl> apenas se você quiser escrever sua própria interface de usuário de visualização de impressão. Se quiser que a interface de usuário padrão, use um <xref:System.Windows.Forms.PrintPreviewDialog> controlar; consulte [visão geral do controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) para obter uma visão geral.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, que define o documento a ser visualizado. O documento deve ser um <xref:System.Drawing.Printing.PrintDocument> objeto. Para obter uma visão geral da criação de documentos para impressão, confira [Visão geral do componente PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) e [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md). O <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriedades determinam o número de páginas exibidas horizontalmente e verticalmente no controle. Suavização pode fazer o texto pareça mais suave, mas ele também pode tornar a exibição mais lenta; para usá-lo, defina o <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> propriedade `true`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [Visão geral do controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [Controle PrintPreviewControl](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [Controles e componentes da caixa de diálogo](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
