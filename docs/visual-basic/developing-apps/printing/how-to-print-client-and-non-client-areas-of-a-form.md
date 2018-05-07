---
title: Como imprimir áreas cliente e não cliente de um formulário (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 566cf295462945a6bc90bc96f8907de34646bd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a>Como imprimir áreas cliente e não cliente de um formulário (Visual Basic)
O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário exatamente como ele aparece na tela sem usar um <xref:System.Drawing.Printing.PrintDocument> componente. O procedimento a seguir mostra como imprimir um formulário, incluindo a área do cliente e a área não cliente. A área do cliente não inclui a barra de título, bordas e rolagem barras.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a>Para imprimir o cliente e as áreas de cliente não de um formulário  
  
1.  No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.  
  
2.  No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para impressão `Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  Em alguns sistemas operacionais, texto ou gráfico desenhado pelo <xref:System.Drawing.Graphics> métodos podem não imprimir corretamente. In this case, use o método de impressão compatível: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Como imprimir um formulário rolável](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
