---
title: "Como imprimir a &#225;rea cliente de um formul&#225;rio (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "área do cliente, imprimindo"
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como imprimir a &#225;rea cliente de um formul&#225;rio (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite que você imprimir rapidamente uma imagem de um formulário sem usar um <xref:System.Drawing.Printing.PrintDocument> componente. O procedimento a seguir mostra como imprimir apenas a área cliente de um formulário, sem a barra de título, bordas e barras de rolagem.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá\-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### Para imprimir a área cliente de um formulário  
  
1.  No **Toolbox**, clique o **Visual Basic PowerPacks** guia e, em seguida, arraste o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para o formulário.  
  
     O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é adicionado à bandeja de componentes.  
  
2.  No **propriedades** janela, defina o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade <xref:System.Drawing.Printing.PrintAction>.  
  
3.  Adicione o seguinte código no manipulador de eventos apropriado \(por exemplo, o `Click` manipulador de eventos para um **impressão**`Button`\).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  Em alguns sistemas operacionais, texto ou elementos gráficos desenhados pelo <xref:System.Drawing.Graphics> métodos podem não imprimir corretamente. Nesse caso, use o método de impressão compatível: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [Como imprimir áreas cliente e não cliente de um formulário](../Topic/How%20to:%20Print%20Client%20and%20Non-Client%20Areas%20of%20a%20Form%20\(Visual%20Basic\).md)   
 [Como imprimir um formulário rolável](../Topic/How%20to:%20Print%20a%20Scrollable%20Form%20\(Visual%20Basic\).md)