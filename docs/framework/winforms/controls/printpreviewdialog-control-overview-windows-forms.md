---
title: "Visão geral do controle PrintPreviewDialog (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed071a4d38a0167ac9414ee7d383736dd38a62a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Visão geral do controle PrintPreviewDialog (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> controle é uma caixa de diálogo pré-configurada usada para exibir como um [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) aparecerá quando impresso. Use-o em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo. O controle contém botões para imprimir, aumentar o zoom, exibir uma ou várias páginas e fechar a caixa de diálogo.  
  
## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla  
 Propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, que define o documento a ser visualizado. O documento deve ser um <xref:System.Drawing.Printing.PrintDocument> objeto. Para exibir a caixa de diálogo, você deve chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A> método. A suavização pode fazer o texto pareça mais suave, mas ele também pode tornar a exibição mais lenta; para usá-lo, defina o <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> propriedade `true`.  
  
 Determinadas propriedades estão disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> que o <xref:System.Windows.Forms.PrintPreviewDialog> contém. (Você não precisa adicionar este <xref:System.Windows.Forms.PrintPreviewControl> para o formulário; ele é automaticamente incluído no <xref:System.Windows.Forms.PrintPreviewDialog> quando você adiciona a caixa de diálogo ao formulário.) Exemplos de propriedades disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> são o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriedades, que determina o número de páginas exibidas horizontalmente e verticalmente no controle. Você pode acessar o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a propriedade como `PrintPreviewDialog1.PrintPreviewControl.Columns` na [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` na [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], ou `printPreviewDialog1->PrintPreviewControl->Columns` em [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [Visão geral do controle PrintPreviewControl](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [Controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Controles e componentes da caixa de diálogo](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
