---
title: "Visão geral do componente FolderBrowserDialog (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7fab1dbe01c5b21e510841b1541150f6152ab0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>Visão geral do componente FolderBrowserDialog (Windows Forms)
Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> componente é uma caixa de diálogo modal que é usada para navegar e selecionar pastas. Novas pastas também podem ser criadas de dentro do <xref:System.Windows.Forms.FolderBrowserDialog> componente.  
  
> [!NOTE]
>  Para selecionar arquivos, em vez de pastas, use o [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md) componente.  
  
 O <xref:System.Windows.Forms.FolderBrowserDialog> componente é exibido em tempo de execução usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método. Definir o <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriedade para determinar a pasta principal e todas as subpastas que aparecerão na exibição de árvore da caixa de diálogo. Quando a caixa de diálogo foi mostrada, você pode usar o <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade para obter o caminho da pasta que foi selecionado.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.FolderBrowserDialog> componente aparece na bandeja de na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)  
 [Componente FolderBrowserDialog](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
