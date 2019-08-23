---
title: 'Como: Definir o formato para o controle NumericUpDown do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949158"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Como: Definir o formato para o controle NumericUpDown do Windows Forms
Você pode configurar como os valores são exibidos no controle <xref:System.Windows.Forms.NumericUpDown> de Windows Forms. A <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade determina quantos números aparecem após o ponto decimal; o padrão é 0. A <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade determina se um separador será inserido entre cada três dígitos decimais; o padrão `false`é. O controle pode exibir valores em hexadecimal em vez de em formato decimal, <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> se a propriedade for `true`definida como; o `false`padrão é.  
  
### <a name="to-format-the-numeric-value"></a>Para formatar o valor numérico  
  
- Exiba um valor decimal definindo <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> a propriedade como um inteiro e definindo a <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Propriedade como `true` ou `false`.  
  
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
  
- Exiba um valor hexadecimal definindo a <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Propriedade como. `true`  
  
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
    > Mesmo que o valor seja exibido no formulário como hexadecimal, todos os testes que você executar na <xref:System.Windows.Forms.NumericUpDown.Value%2A> Propriedade testarão seu valor decimal.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NumericUpDown>
- [Controle NumericUpDown](numericupdown-control-windows-forms.md)
- [Visão geral do controle NumericUpDown](numericupdown-control-overview-windows-forms.md)
