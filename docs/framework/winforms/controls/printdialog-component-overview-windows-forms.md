---
title: Visão geral do componente PrintDialog
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728674"
---
# <a name="printdialog-component-overview-windows-forms"></a>Visão geral do componente PrintDialog (Windows Forms)

O componente [PrintDialog](printdialog-component-windows-forms.md) dos Windows Forms é uma caixa de diálogo pré-configurada usada para selecionar uma impressora, escolher as páginas a serem impressas e determinar outras configurações relacionadas à impressão em aplicativos baseados no Windows. Use-o como uma solução simples para seleção de impressora e de configurações relacionadas à impressão em vez de configurar sua própria caixa de diálogo. Você pode habilitar os usuários a imprimir muitas partes de seus documentos: imprimir tudo, imprimir um intervalo de páginas selecionadas ou uma seleção. Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários. O componente <xref:System.Windows.Forms.PrintDialog> herda da classe <xref:System.Windows.Forms.CommonDialog>.

## <a name="working-with-the-component"></a>Como trabalhar com o componente

Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução. Esse componente tem propriedades relacionadas a um único trabalho de impressão (<xref:System.Drawing.Printing.PrintDocument> classe) ou às configurações de uma impressora individual (<xref:System.Drawing.Printing.PrinterSettings> classe). Um deles, por sua vez, pode ser compartilhado por várias impressoras.

Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.PrintDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PrintDialog>
- [Componente PrintDialog](printdialog-component-windows-forms.md)
