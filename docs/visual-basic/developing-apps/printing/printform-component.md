---
title: Componente PrintForm (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
ms.openlocfilehash: 6cb7cfe022b2b4d23f47a47ec70f08d5c0ccbc7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="printform-component-visual-basic"></a>Componente PrintForm (Visual Basic)
O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente do Visual Basic permite imprimir uma imagem de um formulário do Windows em tempo de execução. Substitui o seu comportamento do `PrintForm` método em versões anteriores do Visual Basic.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>Visão geral do componente PrintForm  
 Um cenário comum para formulários do Windows é criar um formulário que é formatado para se parecer com um formulário de papel ou um relatório, e, em seguida, para imprimir uma imagem do formulário. Embora você possa usar um <xref:System.Drawing.Printing.PrintDocument> componente para fazer isso, ela requer que um lote de código. O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente permite imprimir uma imagem de um formulário para uma impressora, uma janela de visualização de impressão ou um arquivo sem usar um <xref:System.Drawing.Printing.PrintDocument> componente.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente está localizado no **Visual Basic PowerPacks** guia do **caixa de ferramentas**. Quando ele é arrastado para um formulário é exibido na bandeja do componente, a área pequena na borda inferior do formulário. Quando o componente é selecionado, as propriedades que definem o comportamento podem ser definidas **propriedades** janela. Todas essas propriedades também podem ser definidas no código. Você também pode criar uma instância do <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente no código sem adicionar o componente em tempo de design.  
  
 Quando você imprime um formulário, tudo na área cliente do formulário é impresso. Isso inclui todos os controles e qualquer texto ou gráfico desenhado no formulário por métodos de elementos gráficos. Por padrão, borda, as barras de rolagem e barra de título do formulário não são impressos. Além disso, por padrão, o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente imprime somente a parte visível do formulário. Por exemplo, se o usuário o redimensiona o formulário em tempo de execução, somente os controles e elementos gráficos que estão visíveis no momento serão impressas.  
  
 A impressora padrão usada pelo <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é determinado pelas configurações do painel de controle do sistema operacional.  
  
 Depois de impressão é iniciada, um padrão <xref:System.Drawing.Printing.PrintDocument> caixa de diálogo de impressão é exibida. Essa caixa de diálogo permite aos usuários cancelar o trabalho de impressão.  
  
### <a name="key-methods-properties-and-events"></a>Métodos, propriedades e eventos de chave  
 O método de chave de <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> método, que imprime uma imagem do formulário para uma impressora, a janela de visualização de impressão ou o arquivo. Há duas versões do <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> método:  
  
-   Uma versão básica sem parâmetros: `Print()`  
  
-   Uma versão sobrecarregada com parâmetros que especificam o comportamento de impressão: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     O `PrintOption` parâmetro do método sobrecarregado determina a implementação base usada para imprimir o formulário, se a barra de título do formulário, barras de rolagem e borda são impressas e se rolável partes do formulário são impressas.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> propriedade é uma propriedade de chave de <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente. Essa propriedade determina se a saída é enviada para uma impressora, exibida em uma janela de visualização de impressão ou salvo como um arquivo EPS. Se o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> está definida como <xref:System.Drawing.Printing.PrintAction.PrintToFile>, o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> propriedade especifica o caminho e nome de arquivo.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> propriedade fornece acesso a uma base <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> objeto que permite que você especifique essas configurações como a impressora para uso e o número de cópias a serem impressas. Você também pode consultar as capacidades da impressora, como cor ou suporte duplex. Essa propriedade não aparece a **propriedades** janela; ele pode ser acessado somente de código.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> propriedade é usada para especificar o formato para imprimir quando você invoca o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente por meio de programação. Se o componente é adicionado a um formulário em tempo de design, o formulário é o padrão.  
  
 Chave de eventos para o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente incluem o seguinte:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> evento. Ocorre quando o método <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> é chamado antes da impressão da primeira página do documento.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> evento. Ocorre depois que a última página é impresso.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> evento. Ocorre imediatamente antes de cada página ser impressa.  
  
### <a name="remarks"></a>Comentários  
 Se um formulário contiver texto ou gráfico desenhado pelo <xref:System.Drawing.Graphics> métodos, use o basic <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) método imprimi-lo. Elementos gráficos talvez não sejam renderizadas em alguns sistemas operacionais quando sobrecarregados <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> método é usado.  
  
 Se a largura de um formulário é maior do que a largura do papel na impressora, à direita do formulário pode ser cortada. Ao criar formulários de impressão, certifique-se de que o formulário se ajuste na papel de tamanho padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um uso comum dos <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente.  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 [Como imprimir um formulário usando o componente PrintForm](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [Como imprimir a área de cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Como imprimir áreas cliente e não cliente de um formulário](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Como imprimir um formulário rolável](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
