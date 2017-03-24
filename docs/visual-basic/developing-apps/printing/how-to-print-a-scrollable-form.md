---
title: "Como: imprimir um formulário rolável (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- entire form, printing
- scrollable form, printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4ccb6ce03577d5cecd8cf29eddc5ca9f1859f043
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a>Como imprimir um formulário rolável (Visual Basic)
O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente permite que você imprimir rapidamente uma imagem de um formulário sem usar um <xref:System.Drawing.Printing.PrintDocument>componente.</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Por padrão, somente a parte visível do formulário é impresso; Se um usuário tiver redimensionado o formulário em tempo de execução, a imagem não pode imprimir conforme o esperado. O procedimento a seguir mostra como imprimir a área cliente completo de um formulário rolável, mesmo se o formulário for redimensionado.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a>Para imprimir a área cliente completo de um formulário rolável  
  
1.  No **Toolbox**, clique o **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente para o formulário.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente será adicionado à bandeja de componentes.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
2.  No **propriedades** janela, defina a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>propriedade <xref:System.Drawing.Printing.PrintAction>.</xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
  
3.  Adicione o seguinte código no manipulador de eventos apropriado (por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  Em alguns sistemas operacionais, texto ou elementos gráficos desenhados pelo <xref:System.Drawing.Graphics>métodos podem não imprimir corretamente.</xref:System.Drawing.Graphics> Nesse caso, você não poderá imprimir com o `Scrollable` parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [Como: imprimir a área cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [Como imprimir áreas cliente e não cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
