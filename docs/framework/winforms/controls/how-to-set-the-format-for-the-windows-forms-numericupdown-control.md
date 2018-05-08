---
title: Como definir o formato para o controle NumericUpDown dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 1cb8f8b7d2f86125736c08cd9eadf4eee30063bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Como definir o formato para o controle NumericUpDown dos Windows Forms
Você pode configurar como os valores são exibidos no Windows Forms <xref:System.Windows.Forms.NumericUpDown> controle. O <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade determina quantos números são exibidos após o ponto decimal; o padrão é 0. O <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade determina se um separador será inserido a cada três dígitos; o padrão é `false`. O controle pode exibir valores em hexadecimal em vez de formato decimal, se o <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> está definida como `true`; o padrão é `false`.  
  
### <a name="to-format-the-numeric-value"></a>Para formatar o valor numérico  
  
-   Exibir um valor decimal, definindo o <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade para um número inteiro e a configuração de <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade `true` ou `false`.  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     -ou-  
  
-   Exibir um valor hexadecimal, definindo o <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> propriedade `true`.  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  Mesmo se o valor é exibido no formulário como hexadecimal, quaisquer testes que você executar no <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade testará seu valor decimal.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.NumericUpDown>  
 [Controle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [Visão geral do controle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
