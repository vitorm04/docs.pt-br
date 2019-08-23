---
title: Visão geral do componente PrintDocument (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928983"
---
# <a name="printdocument-component-overview-windows-forms"></a>Visão geral do componente PrintDocument (Windows Forms)

O componente [PrintDocument](printdocument-component-windows-forms.md) dos Windows Forms é usado para definir as propriedades que descrevem o que imprimir e a capacidade de imprimir o documento em aplicativos baseados no Windows. Pode ser usado junto com o componente [PrintDialog](printdialog-component-windows-forms.md) para controlar todos os aspectos da impressão de documentos.

## <a name="working-with-the-printdocument-component"></a>Trabalhando com o componente PrintDocument

Dois dos principais cenários que envolvem o <xref:System.Drawing.Printing.PrintDocument> componente são:

- Trabalhos de impressão simples, como a impressão de um único arquivo de texto. Nesse caso, você adicionaria o <xref:System.Drawing.Printing.PrintDocument> componente a um Windows Form e adicionaria a lógica de programação que imprime um arquivo no manipulador de <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos. A lógica de programação deve culminar com <xref:System.Drawing.Printing.PrintDocument.Print%2A> o método para imprimir o documento. Esse método envia um <xref:System.Drawing.Graphics> objeto, contido <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> na propriedade da <xref:System.Drawing.Printing.PrintPageEventArgs> classe, para a impressora. Para obter um exemplo que mostra como imprimir um documento de texto usando <xref:System.Drawing.Printing.PrintDocument> o componente, [consulte Como: Imprima um arquivo de texto de várias páginas em](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)Windows Forms.

- Trabalhos de impressão mais complexos, como quando é preciso reutilizar lógica de impressão já escrita. Nesse caso, você deve derivar um novo componente <xref:System.Drawing.Printing.PrintDocument> do componente e substituir (consulte [substituições](../../../visual-basic/language-reference/modifiers/overrides.md) para Visual Basic ou [substituir](../../../csharp/language-reference/keywords/override.md) para C#) o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento.

Quando ele é adicionado a um formulário, o <xref:System.Drawing.Printing.PrintDocument> componente aparece na bandeja na parte inferior da designer de formulários do Windows no Visual Studio.

## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md)
- [Componente PrintDocument](printdocument-component-windows-forms.md)
