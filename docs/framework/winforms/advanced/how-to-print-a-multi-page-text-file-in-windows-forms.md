---
title: 'Como: imprimir um arquivo de texto de várias páginas nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 69fe58292eda2bb283488252f571d3c3691f6392
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192167"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Como: imprimir um arquivo de texto de várias páginas nos Windows Forms
É muito comum aplicativos do Windows imprimirem texto. O <xref:System.Drawing.Graphics> classe fornece métodos para desenhar objetos (elementos gráficos ou texto) em um dispositivo, como uma tela ou impressora.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos de <xref:System.Windows.Forms.TextRenderer> não têm suporte para impressão. Você sempre deve usar o <xref:System.Drawing.Graphics.DrawString%2A> métodos de <xref:System.Drawing.Graphics>, conforme mostrado no exemplo de código a seguir, para desenhar o texto para fins de impressão.  
  
### <a name="to-print-text"></a>Imprimir texto  
  
1.  Adicionar um <xref:System.Drawing.Printing.PrintDocument> componente e uma cadeia de caracteres ao seu formulário.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  Se a impressão de um documento, defina o <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> propriedade para o documento que você deseja imprimir e abrir e ler o conteúdo de documentos para a cadeia de caracteres que você adicionou anteriormente.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  No <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos, use o <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> classe e o conteúdo do documento para calcular o comprimento da linha e linhas por página. Depois de cada página é desenhada, verifique se ele é a última página e defina as <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> adequadamente. O <xref:System.Drawing.Printing.PrintDocument.PrintPage> é gerado até <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> é `false`. Além disso, verifique se o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento está associado a seu método de manipulação de eventos.  
  
     No exemplo de código a seguir, o manipulador de eventos é usado para imprimir o conteúdo do arquivo “testPage.txt” na mesma fonte usada no formulário.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  Chame o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para gerar o <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um arquivo de texto chamado testPage.txt que contém o texto a ser impresso, localizado na raiz da unidade C:\\. Edite o código para imprimir um arquivo diferente.  
  
-   Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
  
-   Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Suporte à impressão no Windows Forms](windows-forms-print-support.md)
