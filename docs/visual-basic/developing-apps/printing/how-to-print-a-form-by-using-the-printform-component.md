---
title: Como imprimir um formulário usando o componente PrintForm (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5edad4f04b98dcf0dfa328f111db5dcb423036e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>Como imprimir um formulário usando o componente PrintForm (Visual Basic)
O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário exatamente como ele aparece na tela sem usar um <xref:System.Drawing.Printing.PrintDocument> componente. Os procedimentos a seguir mostram como imprimir um formulário para uma impressora, uma janela de visualização de impressão e um arquivo EPS.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-a-form-to-the-default-printer"></a>Para imprimir um formulário para a impressora padrão  
  
1.  No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.  
  
2.  No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>Para exibir um formulário em uma janela de visualização de impressão  
  
1.  No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.  
  
2.  No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.  
  
3.  Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>Para imprimir um formulário em um arquivo  
  
1.  No **caixa de ferramentas**, clique no **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja do componente.  
  
2.  No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction.PrintToFile>.  
  
3.  Opcionalmente, selecione o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> propriedade e digite o caminho completo e nome do arquivo para o arquivo de destino.  
  
     Se você ignorar essa etapa, o usuário será solicitado um nome de arquivo em tempo de execução.  
  
4.  Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [Como imprimir a área de cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Como imprimir áreas cliente e não cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Como imprimir um formulário rolável](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
