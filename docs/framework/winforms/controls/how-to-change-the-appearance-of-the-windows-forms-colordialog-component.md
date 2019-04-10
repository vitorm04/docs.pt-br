---
title: 'Como: Alterar a aparência do componente ColorDialog do Windows Forms'
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
ms.openlocfilehash: d2bb9e06d9d84a9b61c67510e9c012066f69d55e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329226"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Como: Alterar a aparência do componente ColorDialog do Windows Forms
Você pode configurar a aparência dos formulários Windows <xref:System.Windows.Forms.ColorDialog> componente com um número de suas propriedades. A caixa de diálogo tem duas seções, uma que mostra as cores básicas e outra que permite que o usuário defina cores personalizadas.  
  
 A maioria das propriedades restringe quais cores o usuário pode selecionar da caixa de diálogo. Se o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> estiver definida como `true`, o usuário tem permissão para definir cores personalizadas. O <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> é de propriedade `true` se a caixa de diálogo é expandida para definir cores personalizadas; caso contrário, o usuário deve clicar em um botão "Definir cores personalizadas". Quando o <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> estiver definida como `true`, a caixa de diálogo exibe todas as cores disponíveis no conjunto de cores básicas. Se o <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> estiver definida como `true`, o usuário não poderá selecionar cores pontilhadas; apenas cores sólidas estarão disponíveis para seleção.  
  
 Se o <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> estiver definida como `true`, um botão Ajuda aparece na caixa de diálogo. Quando o usuário clica no botão de Ajuda, o <xref:System.Windows.Forms.ColorDialog> do componente <xref:System.Windows.Forms.CommonDialog.HelpRequest> é gerado.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Para configurar a aparência da caixa de diálogo de cor  
  
1. Defina as <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, e <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> propriedades com os valores desejados.  
  
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
