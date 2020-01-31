---
title: Visão geral do controle PrintPreviewControl
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 8dfe5802a24d5ec85ed908fd04c5550e1fbec012
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741443"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>Visão geral do controle PrintPreviewControl (Windows Forms)
O <xref:System.Windows.Forms.PrintPreviewControl> de Windows Forms é usado para exibir um [documento](printdocument-component-windows-forms.md) impresso, pois ele será exibido quando impressa. Esse controle não tem botões ou outros elementos de interface do usuário, portanto, normalmente, você usa o <xref:System.Windows.Forms.PrintPreviewControl> apenas se desejar escrever sua própria interface do usuário de visualização de impressão. Se você quiser a interface do usuário padrão, use um controle de <xref:System.Windows.Forms.PrintPreviewDialog>; consulte [visão geral do controle PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md) para obter uma visão geral.  
  
## <a name="key-properties"></a>Propriedades da chave  
 A propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, que define o documento a ser visualizado. O documento deve ser um objeto <xref:System.Drawing.Printing.PrintDocument>. Para obter uma visão geral da criação de documentos para impressão, confira [Visão geral do componente PrintDocument](printdocument-component-overview-windows-forms.md) e [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md). As propriedades <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> determinam o número de páginas exibidas horizontal e verticalmente no controle. A suavização pode fazer com que o texto pareça mais suave, mas também pode tornar a tela mais lenta; para usá-lo, defina a propriedade <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> como `true`.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.PrintPreviewControl>
- [Visão geral do controle PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md)
- [Controle PrintPreviewControl](printpreviewcontrol-control-windows-forms.md)
- [Controles e componentes da caixa de diálogo](dialog-box-controls-and-components-windows-forms.md)
