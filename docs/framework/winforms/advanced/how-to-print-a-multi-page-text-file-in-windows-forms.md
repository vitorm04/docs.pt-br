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
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931786"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Como: imprimir um arquivo de texto de várias páginas nos Windows Forms
É muito comum aplicativos do Windows imprimirem texto. A <xref:System.Drawing.Graphics> classe fornece métodos para desenhar objetos (gráficos ou texto) em um dispositivo, como uma tela ou impressora.  
  
> [!NOTE]
> Os <xref:System.Windows.Forms.TextRenderer.DrawText%2A> métodos do <xref:System.Windows.Forms.TextRenderer> não têm suporte para impressão. Você sempre deve usar os <xref:System.Drawing.Graphics.DrawString%2A> métodos de <xref:System.Drawing.Graphics>, conforme mostrado no exemplo de código a seguir, para desenhar texto para fins de impressão.  
  
### <a name="to-print-text"></a>Imprimir texto  
  
1. Adicione um <xref:System.Drawing.Printing.PrintDocument> componente e uma cadeia de caracteres ao formulário.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Se estiver imprimindo um documento, <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> defina a propriedade para o documento que você deseja imprimir e abra e leia o conteúdo dos documentos para a cadeia de caracteres que você adicionou anteriormente.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. No manipulador de <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> eventos, use a propriedade da classe e o conteúdo do documento para calcular o comprimento e as linhas de linha por página. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Depois que cada página for desenhada, verifique se ela é a última página e defina a <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> propriedade <xref:System.Drawing.Printing.PrintPageEventArgs> de adequadamente. O <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento é gerado até <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> que `false`seja. Além disso, verifique se <xref:System.Drawing.Printing.PrintDocument.PrintPage> o evento está associado ao seu método de manipulação de eventos.  
  
     No exemplo de código a seguir, o manipulador de eventos é usado para imprimir o conteúdo do arquivo “testPage.txt” na mesma fonte usada no formulário.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Chame o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para gerar o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um arquivo de texto chamado testPage.txt que contém o texto a ser impresso, localizado na raiz da unidade C:\\. Edite o código para imprimir um arquivo diferente.  
  
- Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
  
- Para obter informações sobre como criar este exemplo a partir da linha de comando C#para Visual Basic ou Visual, consulte [criando a linha de comando ou a](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) criação de linha de comando [com CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Suporte à impressão nos Windows Forms](windows-forms-print-support.md)
