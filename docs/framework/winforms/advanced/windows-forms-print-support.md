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
ms.openlocfilehash: 4ea04d0b6bb8ffa7182d5166ebd66b809adeed34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528548"
---
# <a name="windows-forms-print-support"></a>Suporte à impressão no Windows Forms
A impressão nos Windows Forms consiste principalmente em usar o [Componente PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) para permitir que o usuário imprima e o [Controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md), o [Componente PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) e o [Componente PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) para fornecer uma interface gráfica familiar aos usuários acostumados com o sistema operacional Windows.  
  
 Normalmente, você cria uma nova instância do <xref:System.Drawing.Printing.PrintDocument> componente, definir as propriedades que descrevem o que imprimir usando o <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> classes e chame o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método realmente imprimir o documento.  
  
 Durante o curso da impressão de um aplicativo baseado no Windows, o <xref:System.Drawing.Printing.PrintDocument> componente mostrará uma caixa de diálogo de impressão Abortar para alertar os usuários para o fato de que a impressão está ocorrendo e permitir que o trabalho de impressão seja cancelado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como Criar Trabalhos de Impressão Padrão dos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 Explica como usar o <xref:System.Drawing.Printing.PrintDocument> componente para imprimir a partir de um formulário do Windows.  
  
 [Como Capturar a Entrada do Usuário de um PrintDialog em Tempo de Execução](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Explica como modificar as opções de impressão selecionadas programaticamente usando o <xref:System.Windows.Forms.PrintDialog> componente.  
  
 [Como Escolher as Impressoras Conectadas ao Computador de um Usuário nos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Descreve como alterar a impressora para imprimir usando o <xref:System.Windows.Forms.PrintDialog> componente em tempo de execução.  
  
 [Como Imprimir Elementos Gráficos nos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 Descreve o envio de elementos gráficos para a impressora.  
  
 [Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Descreve o envio de texto para a impressora.  
  
 [Como Concluir Trabalhos de Impressão dos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 Explica como alertar usuários para a conclusão de um trabalho de impressão.  
  
 [Como imprimir um Windows Form](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 Mostra como imprimir uma cópia do formulário atual.  
  
 [Como imprimir nos Windows Forms usando Visualização de Impressão](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 Mostra como usar um <xref:System.Windows.Forms.PrintPreviewDialog> para imprimir um documento.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Componente PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 Explica o uso do <xref:System.Drawing.Printing.PrintDocument> componente.  
  
 [Componente PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 Explica o uso do <xref:System.Windows.Forms.PrintDialog> componente.  
  
 [Controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 Explica o uso do <xref:System.Windows.Forms.PrintPreviewDialog> controle.  
  
 [Componente PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 Explica o uso do <xref:System.Windows.Forms.PageSetupDialog> componente.  
  
 <xref:System.Drawing.Printing>  
 Descreve as classes de <xref:System.Drawing.Printing> namespace.
