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
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="a4067-102">Como definir o formato para o controle NumericUpDown dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4067-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="a4067-103">Você pode configurar como os valores são exibidos no controle de <xref:System.Windows.Forms.NumericUpDown> de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a4067-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="a4067-104">A propriedade <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> determina quantos números aparecem após o ponto decimal; o padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="a4067-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="a4067-105">A propriedade <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> determina se um separador será inserido entre a cada três dígitos decimais; o padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a4067-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="a4067-106">O controle pode exibir valores em hexadecimal em vez de em formato decimal, se a propriedade <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> estiver definida como `true`; o padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a4067-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="a4067-107">Para formatar o valor numérico</span><span class="sxs-lookup"><span data-stu-id="a4067-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="a4067-108">Exiba um valor decimal definindo a propriedade <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> como um inteiro e definindo a propriedade <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="a4067-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="a4067-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="a4067-109">-or-</span></span>  
  
- <span data-ttu-id="a4067-110">Exiba um valor hexadecimal definindo a propriedade <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="a4067-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    > <span data-ttu-id="a4067-111">Mesmo que o valor seja exibido no formulário como hexadecimal, todos os testes que você executar na propriedade <xref:System.Windows.Forms.NumericUpDown.Value%2A> testarão seu valor decimal.</span><span class="sxs-lookup"><span data-stu-id="a4067-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4067-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="a4067-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="a4067-113">Controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="a4067-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="a4067-114">Visão geral do controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="a4067-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
