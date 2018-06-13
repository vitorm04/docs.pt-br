---
title: Visão geral do componente PrintDocument (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: b02133321624d27b9c1e8faae9cac1b4fe8f76c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538259"
---
# <a name="printdocument-component-overview-windows-forms"></a>Visão geral do componente PrintDocument (Windows Forms)
O componente [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) dos Windows Forms é usado para definir as propriedades que descrevem o que imprimir e a capacidade de imprimir o documento em aplicativos baseados no Windows. Pode ser usado junto com o componente [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) para controlar todos os aspectos da impressão de documentos.  
  
## <a name="working-with-the-printdocument-component"></a>Trabalhando com o componente PrintDocument  
 Dois dos principais cenários que envolvem o <xref:System.Drawing.Printing.PrintDocument> componente são:  
  
-   Trabalhos de impressão simples, como a impressão de um único arquivo de texto. Nesse caso, você poderia adicionar o <xref:System.Drawing.Printing.PrintDocument> componente a um formulário do Windows, em seguida, adicione a lógica de programação que imprime um arquivo de <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos. A lógica de programação deve culminar com o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para imprimir o documento. Esse método envia uma <xref:System.Drawing.Graphics> contido no objeto de <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> classe para a impressora. Para obter um exemplo que mostra como imprimir um documento de texto usando o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: imprimir um arquivo de texto com várias páginas no Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
-   Trabalhos de impressão mais complexos, como quando é preciso reutilizar lógica de impressão já escrita. Nesse caso, você deve derivar um novo componente do <xref:System.Drawing.Printing.PrintDocument> componente e substituir (consulte [substitui](~/docs/visual-basic/language-reference/modifiers/overrides.md) do Visual Basic ou [substituir](~/docs/csharp/language-reference/keywords/override.md) para c#) o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Drawing.Printing.PrintDocument> componente aparece na bandeja de na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Componente PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
