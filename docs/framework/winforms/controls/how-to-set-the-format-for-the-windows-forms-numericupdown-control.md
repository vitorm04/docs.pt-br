---
title: 'Como: Defina o formato para o controle do Windows Forms NumericUpDown'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5574faf858c32752cfa99b6bf339ddf06cb6b345
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631003"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="134b5-102">Como: Defina o formato para o controle do Windows Forms NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="134b5-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="134b5-103">Você pode configurar como os valores são exibidos nos formulários de Windows <xref:System.Windows.Forms.NumericUpDown> controle.</span><span class="sxs-lookup"><span data-stu-id="134b5-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="134b5-104">O <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade determina quantos números aparecem após o ponto decimal; o padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="134b5-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="134b5-105">O <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade determina se um separador será inserido entre cada três dígitos decimais; o padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="134b5-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="134b5-106">O controle pode exibir valores em hexadecimal, em vez de formato decimal, se o <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> estiver definida como `true`; o padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="134b5-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="134b5-107">Para formatar o valor numérico</span><span class="sxs-lookup"><span data-stu-id="134b5-107">To format the numeric value</span></span>  
  
-   <span data-ttu-id="134b5-108">Exibir um valor decimal, definindo o <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade a um número inteiro e definindo o <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade a ser `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="134b5-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="134b5-109">-ou-</span><span class="sxs-lookup"><span data-stu-id="134b5-109">-or-</span></span>  
  
-   <span data-ttu-id="134b5-110">Exibir um valor hexadecimal, definindo o <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="134b5-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    >  <span data-ttu-id="134b5-111">Mesmo se o valor é exibido no formulário como hexadecimal, todos os testes que você executar no <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade testará seu valor decimal.</span><span class="sxs-lookup"><span data-stu-id="134b5-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134b5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="134b5-112">See also</span></span>
- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="134b5-113">Controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="134b5-113">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)
- [<span data-ttu-id="134b5-114">Visão geral do controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="134b5-114">NumericUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
