---
title: Como criar um formulário MDI com mesclagem de menu e controles ToolStrip
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 645efb8069d56003038189add5bd430f6daf4a97
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Como criar um formulário MDI com mesclagem de menu e controles ToolStrip
O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace oferece suporte para vários aplicativos de interface (MDI) do documento e o <xref:System.Windows.Forms.MenuStrip> controle oferece suporte a mesclagem de menu. Formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.  
  
 Há suporte abrangente para este recurso em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Consulte também [passo a passo: Criando um formulário MDI com mesclagem de Menu e controles ToolStrip](http://msdn.microsoft.com/library/ms233676\(v=vs.110\)).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI. O formulário também dá suporte à mesclagem com menus filho.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer:  
  
-   Referências aos assemblies System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Também sssee [como: compilar e executar uma completa Windows Forms código de exemplo com o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
