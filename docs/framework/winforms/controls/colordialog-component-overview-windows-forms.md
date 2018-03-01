---
title: "Visão geral do componente ColorDialog (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5df0d7ddd16de5bd8bb052c09731df6583ca4903
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="colordialog-component-overview-windows-forms"></a>Visão geral do componente ColorDialog (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> componente é uma caixa de diálogo pré-configurado que permite ao usuário selecionar uma cor de uma paleta de e para adicionar cores personalizadas para essa paleta. É a mesma caixa de diálogo que você vê em outros aplicativos baseados no Windows para selecionar cores. Use-a em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.  
  
 A cor selecionada na caixa de diálogo é retornada no <xref:System.Windows.Forms.ColorDialog.Color%2A> propriedade. Se o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> está definida como `false`, o botão "Definir cores personalizadas" está desabilitado e o usuário é restrito às cores na paleta predefinidas. Se o <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> está definida como `true`, o usuário não é possível selecionar cores pontilhadas. Para exibir a caixa de diálogo, você deve chamar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ColorDialog>  
 [Componente ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [Controles e componentes da caixa de diálogo](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [Como alterar a aparência do componente ColorDialog dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
