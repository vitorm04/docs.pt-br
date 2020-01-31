---
title: Definir o formato para o controle NumericUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5ef1c801e96bef7b92e7e69dc36491144c456eeb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742180"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Como definir o formato para o controle NumericUpDown dos Windows Forms
Você pode configurar como os valores são exibidos no controle de <xref:System.Windows.Forms.NumericUpDown> de Windows Forms. A propriedade <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> determina quantos números aparecem após o ponto decimal; o padrão é 0. A propriedade <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> determina se um separador será inserido entre a cada três dígitos decimais; o padrão é `false`. O controle pode exibir valores em hexadecimal em vez de em formato decimal, se a propriedade <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> estiver definida como `true`; o padrão é `false`.  
  
### <a name="to-format-the-numeric-value"></a>Para formatar o valor numérico  
  
- Exiba um valor decimal definindo a propriedade <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> como um inteiro e definindo a propriedade <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> como `true` ou `false`.  
  
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
  
     - ou -  
  
- Exiba um valor hexadecimal definindo a propriedade <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> como `true`.  
  
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
    > Mesmo que o valor seja exibido no formulário como hexadecimal, todos os testes que você executar na propriedade <xref:System.Windows.Forms.NumericUpDown.Value%2A> testarão seu valor decimal.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.NumericUpDown>
- [Controle NumericUpDown](numericupdown-control-windows-forms.md)
- [Visão geral do controle NumericUpDown](numericupdown-control-overview-windows-forms.md)
