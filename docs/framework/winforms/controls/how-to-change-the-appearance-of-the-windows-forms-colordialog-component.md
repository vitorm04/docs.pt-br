---
title: Alterar a aparência do componente ColorDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746639"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Como alterar a aparência do componente ColorDialog dos Windows Forms
Você pode configurar a aparência do componente Windows Forms <xref:System.Windows.Forms.ColorDialog> com um número de suas propriedades. A caixa de diálogo tem duas seções, uma que mostra as cores básicas e outra que permite que o usuário defina cores personalizadas.  
  
 A maioria das propriedades restringe quais cores o usuário pode selecionar da caixa de diálogo. Se a propriedade <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> for definida como `true`, o usuário poderá definir cores personalizadas. A propriedade <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> será `true` se a caixa de diálogo for expandida para definir cores personalizadas; caso contrário, o usuário deverá clicar em um botão "definir cores personalizadas". Quando a propriedade <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> é definida como `true`, a caixa de diálogo exibe todas as cores disponíveis no conjunto de cores básicas. Se a propriedade <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> for definida como `true`, o usuário não poderá selecionar cores diquerdas; somente as cores sólidas estão disponíveis para seleção.  
  
 Se a propriedade <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> for definida como `true`, um botão ajuda aparecerá na caixa de diálogo. Quando o usuário clica no botão ajuda, o evento de <xref:System.Windows.Forms.CommonDialog.HelpRequest> do componente de <xref:System.Windows.Forms.ColorDialog> é gerado.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Para configurar a aparência da caixa de diálogo de cor  
  
1. Defina as propriedades <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>e <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> para os valores desejados.  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ColorDialog>
- [Componente ColorDialog](colordialog-component-windows-forms.md)
- [Visão geral do componente ColorDialog](colordialog-component-overview-windows-forms.md)
