---
title: Visão geral do componente ColorDialog
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736970"
---
# <a name="colordialog-component-overview-windows-forms"></a>Visão geral do componente ColorDialog (Windows Forms)
O Windows Forms <xref:System.Windows.Forms.ColorDialog> componente é uma caixa de diálogo pré-configurada que permite ao usuário selecionar uma cor de uma paleta e adicionar cores personalizadas a essa paleta. É a mesma caixa de diálogo que você vê em outros aplicativos baseados no Windows para selecionar cores. Use-a em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.  
  
 A cor selecionada na caixa de diálogo é retornada na propriedade <xref:System.Windows.Forms.ColorDialog.Color%2A>. Se a propriedade <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> for definida como `false`, o botão "definir cores personalizadas" será desabilitado e o usuário será restrito às cores predefinidas na paleta. Se a propriedade <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> for definida como `true`, o usuário não poderá selecionar cores diquerdas. Para exibir a caixa de diálogo, você deve chamar seu método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ColorDialog>
- [Componente ColorDialog](colordialog-component-windows-forms.md)
- [Controles e componentes da caixa de diálogo](dialog-box-controls-and-components-windows-forms.md)
- [Como alterar a aparência do componente ColorDialog dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
