---
title: Visão geral do componente FolderBrowserDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: aae18167b29c71ad692cc6ba447457cd079374b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074125"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>Visão geral do componente FolderBrowserDialog (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.FolderBrowserDialog> componente é uma caixa de diálogo modal que é usada para procurar e selecionar pastas. Novas pastas também podem ser criadas de dentro do <xref:System.Windows.Forms.FolderBrowserDialog> componente.  
  
> [!NOTE]
>  Para selecionar arquivos, em vez de pastas, use o [OpenFileDialog](openfiledialog-component-windows-forms.md) componente.  
  
 O <xref:System.Windows.Forms.FolderBrowserDialog> componente é exibido em tempo de execução usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método. Defina o <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriedade para determinar a pasta principal e todas as subpastas que aparecerão na exibição de árvore da caixa de diálogo. Depois que a caixa de diálogo tenha sido mostrada, você pode usar o <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade para obter o caminho da pasta que foi selecionado.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.FolderBrowserDialog> componente aparece na bandeja na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Como: Escolher pastas com o componente FolderBrowserDialog do Windows Forms](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [Componente FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
