---
title: 'Como: capturar a entrada do usuário de um PrintDialog em tempo de execução'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
ms.openlocfilehash: 2aaf988f362baf9cd80eb16e4a08f7f65a5077bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311416"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Como: capturar a entrada do usuário de um PrintDialog em tempo de execução
Embora você possa definir as opções relacionadas à impressão em tempo de design, às vezes, convém alterar essas opções em tempo de execução, provavelmente devido a escolhas feitas pelo usuário. Você pode capturar a entrada do usuário para imprimir um documento usando o <xref:System.Windows.Forms.PrintDialog> e o <xref:System.Drawing.Printing.PrintDocument> componentes.  
  
### <a name="to-change-print-options-programmatically"></a>Para alterar as opções de impressão de forma programática  
  
1. Adicionar um <xref:System.Windows.Forms.PrintDialog> e um <xref:System.Drawing.Printing.PrintDocument> ao seu formulário.  
  
2. Defina a <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade do <xref:System.Windows.Forms.PrintDialog> para o <xref:System.Drawing.Printing.PrintDocument> adicionado ao formulário.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3. Exibição de <xref:System.Windows.Forms.PrintDialog> componente usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4. Opções de impressão do usuário na caixa de diálogo serão copiadas para o <xref:System.Drawing.Printing.PrinterSettings> propriedade do <xref:System.Drawing.Printing.PrintDocument> componente.  
  
## <a name="see-also"></a>Consulte também

- [Como: Imprimir um arquivo de texto de várias páginas nos Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Suporte à impressão nos Windows Forms](windows-forms-print-support.md)
