---
title: 'Como: Definir e retornar valores numéricos com o controle NumericUpDown do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: 281fbbd4459230056fcac2e6c684422c91dc0817
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119880"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Como: Definir e retornar valores numéricos com o controle NumericUpDown do Windows Forms
O valor numérico de formulários do Windows <xref:System.Windows.Forms.NumericUpDown> controle é determinado pelo seu <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade. Você pode escrever testes condicionais para o valor do controle, assim como ocorre com qualquer outra propriedade. Uma vez a <xref:System.Windows.Forms.NumericUpDown.Value%2A> estiver definida, você pode ajustá-lo diretamente ao escrever código para executar operações nela ou você pode chamar o <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> e <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> métodos.  
  
### <a name="to-set-the-numeric-value"></a>Para definir o valor numérico  
  
1.  Atribuir um valor para o <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade no código ou na janela Propriedades.  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     - ou -  
  
2.  Chame o <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ou <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> método para aumentar ou diminuir o valor, o valor especificado no <xref:System.Windows.Forms.NumericUpDown.Increment%2A> propriedade.  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>Para retornar o valor numérico  
  
-   Acesso a <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade no código.  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [Controle NumericUpDown](numericupdown-control-windows-forms.md)
- [Visão geral do controle NumericUpDown](numericupdown-control-overview-windows-forms.md)
