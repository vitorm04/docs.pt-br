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
ms.openlocfilehash: 5957a44c7b07aa1b8d8df32667f023c0873ec1de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186128"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Como: Definir o formato para o controle NumericUpDown do Windows Forms
Você pode configurar como os valores são exibidos nos formulários de Windows <xref:System.Windows.Forms.NumericUpDown> controle. O <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade determina quantos números aparecem após o ponto decimal; o padrão é 0. O <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade determina se um separador será inserido entre cada três dígitos decimais; o padrão é `false`. O controle pode exibir valores em hexadecimal, em vez de formato decimal, se o <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> estiver definida como `true`; o padrão é `false`.  
  
### <a name="to-format-the-numeric-value"></a>Para formatar o valor numérico  
  
-   Exibir um valor decimal, definindo o <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade a um número inteiro e definindo o <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade a ser `true` ou `false`.  
  
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
  
-   Exibir um valor hexadecimal, definindo o <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> propriedade para `true`.  
  
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
    >  Mesmo se o valor é exibido no formulário como hexadecimal, todos os testes que você executar no <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade testará seu valor decimal.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NumericUpDown>
- [Controle NumericUpDown](numericupdown-control-windows-forms.md)
- [Visão geral do controle NumericUpDown](numericupdown-control-overview-windows-forms.md)
