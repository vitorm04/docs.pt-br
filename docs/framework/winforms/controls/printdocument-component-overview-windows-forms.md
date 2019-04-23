---
title: Visão geral do componente PrintDocument (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a3f08aa4bd5b63769cef35dbea2209d5d83261be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198628"
---
# <a name="printdocument-component-overview-windows-forms"></a>Visão geral do componente PrintDocument (Windows Forms)
O componente [PrintDocument](printdocument-component-windows-forms.md) dos Windows Forms é usado para definir as propriedades que descrevem o que imprimir e a capacidade de imprimir o documento em aplicativos baseados no Windows. Pode ser usado junto com o componente [PrintDialog](printdialog-component-windows-forms.md) para controlar todos os aspectos da impressão de documentos.  
  
## <a name="working-with-the-printdocument-component"></a>Trabalhando com o componente PrintDocument  
 Dois dos principais cenários que envolvem o <xref:System.Drawing.Printing.PrintDocument> componente são:  
  
-   Trabalhos de impressão simples, como a impressão de um único arquivo de texto. Nesse caso, você adicionaria o <xref:System.Drawing.Printing.PrintDocument> componente a um formulário do Windows, em seguida, adicione lógica de programação que imprime um arquivo no <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos. A lógica de programação deve culminar com o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para imprimir o documento. Esse método envia uma <xref:System.Drawing.Graphics> contido no objeto a <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> classe, para a impressora. Para obter um exemplo que mostra como imprimir um documento de texto usando o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: Imprimir um arquivo de texto de várias páginas nos Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
-   Trabalhos de impressão mais complexos, como quando é preciso reutilizar lógica de impressão já escrita. Nesse caso, você deve derivar um novo componente dos <xref:System.Drawing.Printing.PrintDocument> componente e substituição (consulte [substitui](~/docs/visual-basic/language-reference/modifiers/overrides.md) para o Visual Basic ou [substituir](~/docs/csharp/language-reference/keywords/override.md) para C#) a <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Drawing.Printing.PrintDocument> componente aparece na bandeja na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md)
- [Componente PrintDocument](printdocument-component-windows-forms.md)
