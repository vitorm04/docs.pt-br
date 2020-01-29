---
title: Suporte de impressão
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732496"
---
# <a name="windows-forms-print-support"></a>Suporte à impressão no Windows Forms
A impressão nos Windows Forms consiste principalmente em usar o [Componente PrintDocument](../controls/printdocument-component-windows-forms.md) para permitir que o usuário imprima e o [Controle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md), o [Componente PrintDialog](../controls/printdialog-component-windows-forms.md) e o [Componente PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) para fornecer uma interface gráfica familiar aos usuários acostumados com o sistema operacional Windows.  
  
 Normalmente, você cria uma nova instância do componente <xref:System.Drawing.Printing.PrintDocument>, define as propriedades que descrevem o que imprimir usando as classes <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> e chama o método <xref:System.Drawing.Printing.PrintDocument.Print%2A> para realmente imprimir o documento.  
  
 Durante a impressão de um aplicativo baseado no Windows, o componente <xref:System.Drawing.Printing.PrintDocument> mostrará uma caixa de diálogo anular impressão para alertar os usuários sobre o fato de que a impressão está ocorrendo e para permitir que o trabalho de impressão seja cancelado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como Criar Trabalhos de Impressão Padrão dos Windows Forms](how-to-create-standard-windows-forms-print-jobs.md)  
 Explica como usar o componente <xref:System.Drawing.Printing.PrintDocument> para imprimir de um formulário do Windows.  
  
 [Como Capturar a Entrada do Usuário de um PrintDialog em Tempo de Execução](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Explica como modificar as opções de impressão selecionadas programaticamente usando o componente <xref:System.Windows.Forms.PrintDialog>.  
  
 [Como Escolher as Impressoras Conectadas ao Computador de um Usuário nos Windows Forms](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Descreve como alterar a impressora para imprimir usando o componente <xref:System.Windows.Forms.PrintDialog> em tempo de execução.  
  
 [Como Imprimir Elementos Gráficos nos Windows Forms](how-to-print-graphics-in-windows-forms.md)  
 Descreve o envio de elementos gráficos para a impressora.  
  
 [Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Descreve o envio de texto para a impressora.  
  
 [Como Concluir Trabalhos de Impressão dos Windows Forms](how-to-complete-windows-forms-print-jobs.md)  
 Explica como alertar usuários para a conclusão de um trabalho de impressão.  
  
 [Como imprimir um Windows Form](how-to-print-a-windows-form.md)  
 Mostra como imprimir uma cópia do formulário atual.  
  
 [Como imprimir nos Windows Forms usando Visualização de Impressão](how-to-print-in-windows-forms-using-print-preview.md)  
 Mostra como usar um <xref:System.Windows.Forms.PrintPreviewDialog> para imprimir um documento.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Componente PrintDocument](../controls/printdocument-component-windows-forms.md)  
 Explica o uso do componente <xref:System.Drawing.Printing.PrintDocument>.  
  
 [Componente PrintDialog](../controls/printdialog-component-windows-forms.md)  
 Explica o uso do componente <xref:System.Windows.Forms.PrintDialog>.  
  
 [Controle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md)  
 Explica o uso do controle de <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
 [Componente PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md)  
 Explica o uso do componente <xref:System.Windows.Forms.PageSetupDialog>.  
  
 <xref:System.Drawing.Printing>  
 Descreve as classes no namespace <xref:System.Drawing.Printing>.
