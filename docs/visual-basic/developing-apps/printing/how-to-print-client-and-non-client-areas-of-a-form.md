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
ms.openlocfilehash: 5109993146a8d53d5cbeebcc52c018a6f0f57ed5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408433"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a>Como imprimir áreas cliente e não cliente de um formulário (Visual Basic)
O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário, exatamente como ele aparece na tela sem usar um <xref:System.Drawing.Printing.PrintDocument> componente. O procedimento a seguir mostra como imprimir um formulário, incluindo a área de cliente e a área não cliente. A área de cliente não inclui a barra de título, bordas e rolagem barras.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los na [Centro de Download](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a>Para imprimir o cliente e as áreas não cliente de um formulário  
  
1.  No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja de componentes.  
  
2.  No **propriedades** janela, defina as <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, nos `Click` manipulador de eventos para impressão `Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  Em alguns sistemas operacionais, texto ou elementos gráficos desenhados pelo <xref:System.Drawing.Graphics> métodos podem não imprimir corretamente. In this case, use o método de impressão compatível: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Como imprimir um formulário rolável](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
