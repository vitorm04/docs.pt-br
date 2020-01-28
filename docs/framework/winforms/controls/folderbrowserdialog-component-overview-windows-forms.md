---
title: Visão geral do componente FolderBrowserDialog
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745728"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>Visão geral do componente FolderBrowserDialog (Windows Forms)

O componente Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> é uma caixa de diálogo modal que é usada para procurar e selecionar pastas. Novas pastas também podem ser criadas de dentro do componente <xref:System.Windows.Forms.FolderBrowserDialog>.

> [!NOTE]
> Para selecionar arquivos, em vez de pastas, use o componente [OpenFileDialog](openfiledialog-component-windows-forms.md) .

O componente <xref:System.Windows.Forms.FolderBrowserDialog> é exibido em tempo de execução usando o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>. Defina a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> para determinar a pasta superior e todas as subpastas que aparecerão dentro do modo de exibição de árvore da caixa de diálogo. Depois que a caixa de diálogo for exibida, você poderá usar a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> para obter o caminho da pasta que foi selecionada.

Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.FolderBrowserDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [Componente FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
