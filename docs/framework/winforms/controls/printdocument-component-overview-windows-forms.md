---
title: Visão geral do componente PrintDocument
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728545"
---
# <a name="printdocument-component-overview-windows-forms"></a>Visão geral do componente PrintDocument (Windows Forms)

O componente [PrintDocument](printdocument-component-windows-forms.md) dos Windows Forms é usado para definir as propriedades que descrevem o que imprimir e a capacidade de imprimir o documento em aplicativos baseados no Windows. Pode ser usado junto com o componente [PrintDialog](printdialog-component-windows-forms.md) para controlar todos os aspectos da impressão de documentos.

## <a name="working-with-the-printdocument-component"></a>Trabalhando com o componente PrintDocument

Dois dos principais cenários que envolvem o componente <xref:System.Drawing.Printing.PrintDocument> são:

- Trabalhos de impressão simples, como a impressão de um único arquivo de texto. Nesse caso, você adicionaria o componente <xref:System.Drawing.Printing.PrintDocument> a um Windows Form e adicionaria a lógica de programação que imprime um arquivo no manipulador de eventos <xref:System.Drawing.Printing.PrintDocument.PrintPage>. A lógica de programação deve culminar com o método <xref:System.Drawing.Printing.PrintDocument.Print%2A> para imprimir o documento. Esse método envia um objeto <xref:System.Drawing.Graphics>, contido na propriedade <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> da classe <xref:System.Drawing.Printing.PrintPageEventArgs>, para a impressora. Para obter um exemplo que mostra como imprimir um documento de texto usando o componente <xref:System.Drawing.Printing.PrintDocument>, consulte [como imprimir um arquivo de texto de várias páginas em Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).

- Trabalhos de impressão mais complexos, como quando é preciso reutilizar lógica de impressão já escrita. Nesse caso, você deve derivar um novo componente do componente <xref:System.Drawing.Printing.PrintDocument> e substituir (consulte [substituições](../../../visual-basic/language-reference/modifiers/overrides.md) para Visual Basic ou [substituir](../../../csharp/language-reference/keywords/override.md) para C#) o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage>.

Quando ele é adicionado a um formulário, o componente <xref:System.Drawing.Printing.PrintDocument> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.

## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md)
- [Componente PrintDocument](printdocument-component-windows-forms.md)
