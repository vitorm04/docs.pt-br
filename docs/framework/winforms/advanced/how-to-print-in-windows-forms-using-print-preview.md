---
title: Imprimir usando a visualização de impressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 1975c902fdb56326c763f2e2fc11e381ffc7fbd3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740611"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Como imprimir no Windows Forms usando Visualizar Impressão
É muito comum na programação do Windows Forms oferecer a visualização de impressão além dos serviços de impressão. Uma maneira fácil de adicionar serviços de visualização de impressão ao seu aplicativo é usar um controle <xref:System.Windows.Forms.PrintPreviewDialog> em combinação com a lógica de manipulação de eventos <xref:System.Drawing.Printing.PrintDocument.PrintPage> para imprimir um arquivo.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Visualizar um documento de texto com um controle PrintPreviewDialog  
  
1. Adicione uma <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>e duas cadeias de caracteres ao formulário.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Defina a propriedade <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> como o documento que você deseja imprimir e abra e leia o conteúdo do documento para a cadeia de caracteres que você adicionou anteriormente.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Como você faria para imprimir o documento, no manipulador de eventos <xref:System.Drawing.Printing.PrintDocument.PrintPage>, use a propriedade <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> da classe <xref:System.Drawing.Printing.PrintPageEventArgs> e o conteúdo do arquivo para calcular as linhas por página e renderizar o conteúdo do documento. Depois que cada página for desenhada, verifique se ela é a última página e defina a propriedade <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> do <xref:System.Drawing.Printing.PrintPageEventArgs> de acordo. O evento <xref:System.Drawing.Printing.PrintDocument.PrintPage> é gerado até que <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> seja `false`. Após a renderização do documento ser concluída, redefina a cadeia de caracteres a ser renderizada. Além disso, verifique se o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage> está associado ao seu método de manipulação de eventos.  
  
    > [!NOTE]
    > Você poderá já ter concluído as etapas 2 e 3 se tiver implementado a impressão em seu aplicativo.  
  
     No exemplo de código a seguir, o manipulador de eventos é usado para imprimir o arquivo “testPage.txt” na mesma fonte usada no formulário.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. Defina a propriedade <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> do controle de <xref:System.Windows.Forms.PrintPreviewDialog> para o componente <xref:System.Drawing.Printing.PrintDocument> no formulário.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. Chame o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> no controle de <xref:System.Windows.Forms.PrintPreviewDialog>. Normalmente, você chamaria <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> do método de manipulação de eventos <xref:System.Windows.Forms.Control.Click> de um botão. Chamar <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> gera o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage> e renderiza a saída para o controle de <xref:System.Windows.Forms.PrintPreviewDialog>. Quando o usuário clica no ícone de impressão na caixa de diálogo, o evento de <xref:System.Drawing.Printing.PrintDocument.PrintPage> é gerado novamente, enviando a saída para a impressora em vez da caixa de diálogo de visualização. É por isso a cadeia de caracteres é redefinida no final do processo de renderização na etapa 3.  
  
     O exemplo de código a seguir mostra o <xref:System.Windows.Forms.Control.Click> método de manipulação de eventos para um botão no formulário. Esse método de manipulação de eventos chama os métodos para ler o documento e mostrar a caixa de diálogo de visualização de impressão.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
  
## <a name="see-also"></a>Veja também

- [Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Suporte à impressão nos Windows Forms](windows-forms-print-support.md)
- [Impressão mais segura no Windows Forms](../more-secure-printing-in-windows-forms.md)
