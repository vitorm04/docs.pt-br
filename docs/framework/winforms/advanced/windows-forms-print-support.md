---
title: Suporte à impressão no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708126"
---
# <a name="windows-forms-print-support"></a>Suporte à impressão no Windows Forms
A impressão nos Windows Forms consiste principalmente em usar o [Componente PrintDocument](../controls/printdocument-component-windows-forms.md) para permitir que o usuário imprima e o [Controle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md), o [Componente PrintDialog](../controls/printdialog-component-windows-forms.md) e o [Componente PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) para fornecer uma interface gráfica familiar aos usuários acostumados com o sistema operacional Windows.  
  
 Normalmente, você cria uma nova instância dos <xref:System.Drawing.Printing.PrintDocument> componente, definir as propriedades que descrevem o que imprimir usando o <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> classes e chame o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para efetivamente imprimir o documento.  
  
 Durante o curso da impressão de um aplicativo baseado em Windows, o <xref:System.Drawing.Printing.PrintDocument> componente mostrará uma caixa de diálogo de impressão de anulação para alertar os usuários para o fato de que a impressão está ocorrendo e permitir que o trabalho de impressão seja cancelado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Criar trabalhos de impressão padrão do Windows Forms](how-to-create-standard-windows-forms-print-jobs.md)  
 Explica como usar o <xref:System.Drawing.Printing.PrintDocument> componente para imprimir a partir de um formulário do Windows.  
  
 [Como: Capturar a entrada do usuário de um PrintDialog em tempo de execução](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Explica como modificar opções de impressão selecionadas programaticamente usando o <xref:System.Windows.Forms.PrintDialog> componente.  
  
 [Como: Escolher as impressoras conectadas ao computador de um usuário nos Windows Forms](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Descreve como alterar a impressora para imprimir usando o <xref:System.Windows.Forms.PrintDialog> componente em tempo de execução.  
  
 [Como: Imprimir elementos gráficos nos Windows Forms](how-to-print-graphics-in-windows-forms.md)  
 Descreve o envio de elementos gráficos para a impressora.  
  
 [Como: Imprimir um arquivo de texto de várias páginas nos Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Descreve o envio de texto para a impressora.  
  
 [Como: Trabalhos de impressão de formulários do Windows completa](how-to-complete-windows-forms-print-jobs.md)  
 Explica como alertar usuários para a conclusão de um trabalho de impressão.  
  
 [Como: Imprimir um formulário do Windows](how-to-print-a-windows-form.md)  
 Mostra como imprimir uma cópia do formulário atual.  
  
 [Como: Imprimir no Windows Forms usando Visualizar impressão](how-to-print-in-windows-forms-using-print-preview.md)  
 Mostra como usar um <xref:System.Windows.Forms.PrintPreviewDialog> para imprimir um documento.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Componente PrintDocument](../controls/printdocument-component-windows-forms.md)  
 Explica o uso do <xref:System.Drawing.Printing.PrintDocument> componente.  
  
 [Componente PrintDialog](../controls/printdialog-component-windows-forms.md)  
 Explica o uso do <xref:System.Windows.Forms.PrintDialog> componente.  
  
 [Controle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md)  
 Explica o uso do <xref:System.Windows.Forms.PrintPreviewDialog> controle.  
  
 [Componente PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md)  
 Explica o uso do <xref:System.Windows.Forms.PageSetupDialog> componente.  
  
 <xref:System.Drawing.Printing>  
 Descreve as classes no <xref:System.Drawing.Printing> namespace.
