---
title: "PrintForm Component (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "PrintForm component [Visual Basic]"
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# PrintForm Component (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente para [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite imprimir uma imagem de um formulário do Windows em tempo de execução. Substitui o seu comportamento do `PrintForm` método nas versões anteriores do Visual Basic.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá\-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## Visão geral do componente PrintForm  
 Um cenário comum para formulários do Windows é criar um formulário que é formatado para se parecer com um formulário de papel ou um relatório, e, em seguida, para imprimir uma imagem do formulário. Embora você possa usar um <xref:System.Drawing.Printing.PrintDocument> componente para fazer isso, seria necessário muito código. O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite imprimir uma imagem de um formulário para uma impressora, uma janela de visualização de impressão ou um arquivo sem usar um <xref:System.Drawing.Printing.PrintDocument> componente.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente está localizado no **Visual Basic PowerPacks** guia o **ferramentas**. Quando ele é arrastado para um formulário é exibido na bandeja de componentes, a pequena área sob a borda inferior do formulário. Quando o componente for selecionado, as propriedades que definem seu comportamento podem ser definidas **propriedades** janela. Todas essas propriedades também podem ser definidas no código. Você também pode criar uma instância do <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> em código sem adicionar o componente em tempo de design.  
  
 Quando você imprime um formulário, tudo na área do cliente do formulário é impresso. Isso inclui todos os controles e os textos ou gráficos desenhados no formulário por métodos gráficos. Por padrão, borda, as barras de rolagem e barra de título do formulário não são impressos. Também por padrão, o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente imprime somente a parte visível do formulário. Por exemplo, se o usuário redimensiona o formulário em tempo de execução, somente os controles e elementos gráficos que estão visíveis no momento serão impressas.  
  
 A impressora padrão usada pelo <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é determinado pelas configurações do painel de controle do sistema operacional.  
  
 Depois que a impressão é iniciada, um padrão <xref:System.Drawing.Printing.PrintDocument> caixa de diálogo de impressão é exibida. Essa caixa de diálogo permite aos usuários cancelar o trabalho de impressão.  
  
### Chave de métodos, propriedades e eventos  
 O método de chave de <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> método, que imprime uma imagem do formulário para uma impressora, uma janela de visualização de impressão ou um arquivo. Há duas versões do <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> método:  
  
-   Uma versão básica sem parâmetros: `Print()`  
  
-   Uma versão sobrecarregada com parâmetros que especificam o comportamento de impressão: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     O `PrintOption` parâmetro do método sobrecarregado determina a implementação subjacente usada para imprimir o formulário, se a barra de título do formulário, barras de rolagem e borda são impressos e se rolável partes do formulário são impressas.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade é uma propriedade de chave de <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente. Essa propriedade determina se a saída é enviada para uma impressora, exibida em uma janela de visualização de impressão ou salvo como um arquivo EPS. Se o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> está definida como <xref:System.Drawing.Printing.PrintAction>, o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> propriedade especifica o caminho e nome de arquivo.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> propriedade fornece acesso a uma base <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> objeto que permite que você especifique essas configurações como a impressora para uso e o número de cópias a serem impressas. Você também pode consultar as capacidades da impressora, como cor ou o suporte duplex. Essa propriedade não aparece no **propriedades** janela; ele pode ser acessado apenas do código.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> propriedade é usada para especificar o formulário imprimir quando você chama o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente por meio de programação. Se o componente é adicionado a um formulário em tempo de design, o formulário é o padrão.  
  
 Principais eventos para o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componentes incluem o seguinte:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> evento. Ocorre quando o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> método é chamado e antes da primeira página do documento será impresso.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> evento. Ocorre depois que a última página é impresso.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> evento. Ocorre imediatamente antes de cada página é impresso.  
  
### Comentários  
 Se um formulário contiver texto ou elementos gráficos desenhados pelo <xref:System.Drawing.Graphics> métodos, use o basic <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> \(`Print()`\) método imprimi\-lo. Gráficos podem não ser renderizados em alguns sistemas operacionais quando sobrecarregados <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> método é usado.  
  
 Se a largura de um formulário for maior do que a largura do papel na impressora, à direita do formulário pode ser cortada. Ao criar formulários para impressão, certifique\-se de que o formulário se encaixa no papel de tamanho padrão.  
  
## Exemplo  
 O exemplo a seguir mostra um uso comum de <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente.  
  
```  
' Visual Basic. Dim pf As New PrintForm pf.Form = Me pf.PrintAction = PrintToPrinter pf.Print()  
```  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 [Como imprimir um formulário usando o componente PrintForm](../Topic/How%20to:%20Print%20a%20Form%20by%20Using%20the%20PrintForm%20Component%20\(Visual%20Basic\).md)   
 [Como imprimir a área cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [Como imprimir áreas cliente e não cliente de um formulário](../Topic/How%20to:%20Print%20Client%20and%20Non-Client%20Areas%20of%20a%20Form%20\(Visual%20Basic\).md)   
 [Como imprimir um formulário rolável](../Topic/How%20to:%20Print%20a%20Scrollable%20Form%20\(Visual%20Basic\).md)