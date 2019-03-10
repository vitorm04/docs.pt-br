---
title: Visão geral do controle PrintPreviewControl (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 045141fc1860cd194f96cea106ff1ff444587418
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708529"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>Visão geral do controle PrintPreviewControl (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.PrintPreviewControl> é usado para exibir um [PrintDocument](printdocument-component-windows-forms.md) como ele aparecerá quando impresso. Esse controle não tem botões nem outros elementos de interface do usuário, normalmente você usa o <xref:System.Windows.Forms.PrintPreviewControl> somente se você quiser escrever sua própria interface do usuário de visualização de impressão. Se você deseja que a interface de usuário padrão, use uma <xref:System.Windows.Forms.PrintPreviewDialog> controlar; consulte [visão geral do controle PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md) para uma visão geral.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, que define o documento a ser visualizado. O documento deve ser um <xref:System.Drawing.Printing.PrintDocument> objeto. Para obter uma visão geral da criação de documentos para impressão, confira [Visão geral do componente PrintDocument](printdocument-component-overview-windows-forms.md) e [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md). O <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriedades determinam o número de páginas exibidas horizontal e verticalmente no controle. A suavização pode tornar o texto mais suave, mas também pode tornar a exibição mais lenta; para usá-lo, defina as <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> propriedade para `true`.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.PrintPreviewControl>
- [Visão geral do controle PrintPreviewDialog](printpreviewdialog-control-overview-windows-forms.md)
- [Controle PrintPreviewControl](printpreviewcontrol-control-windows-forms.md)
- [Controles e componentes da caixa de diálogo](dialog-box-controls-and-components-windows-forms.md)
