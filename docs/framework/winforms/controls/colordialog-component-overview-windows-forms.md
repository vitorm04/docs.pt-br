---
title: Visão geral do componente ColorDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 284d42218fb4fbce873325b1e45c883d51eefab8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956332"
---
# <a name="colordialog-component-overview-windows-forms"></a>Visão geral do componente ColorDialog (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.ColorDialog> componente é uma caixa de diálogo pré-configurada que permite ao usuário selecionar uma cor de uma paleta e adicione cores personalizadas a essa paleta. É a mesma caixa de diálogo que você vê em outros aplicativos baseados no Windows para selecionar cores. Use-a em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.  
  
 A cor selecionada na caixa de diálogo é retornada no <xref:System.Windows.Forms.ColorDialog.Color%2A> propriedade. Se o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> estiver definida como `false`, o botão "Definir cores personalizadas" estará desabilitado e o usuário está restrito a cores predefinidas na paleta. Se o <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> estiver definida como `true`, o usuário não poderá selecionar cores pontilhadas. Para exibir a caixa de diálogo, você deve chamar seu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ColorDialog>
- [Componente ColorDialog](colordialog-component-windows-forms.md)
- [Controles e componentes da caixa de diálogo](dialog-box-controls-and-components-windows-forms.md)
- [Como: Alterar a aparência do componente ColorDialog dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
