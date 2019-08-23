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
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="7d956-102">Como: Definir o formato para o controle NumericUpDown do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d956-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="7d956-103">Você pode configurar como os valores são exibidos no controle <xref:System.Windows.Forms.NumericUpDown> de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d956-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="7d956-104">A <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriedade determina quantos números aparecem após o ponto decimal; o padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="7d956-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="7d956-105">A <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriedade determina se um separador será inserido entre cada três dígitos decimais; o padrão `false`é.</span><span class="sxs-lookup"><span data-stu-id="7d956-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="7d956-106">O controle pode exibir valores em hexadecimal em vez de em formato decimal, <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> se a propriedade for `true`definida como; o `false`padrão é.</span><span class="sxs-lookup"><span data-stu-id="7d956-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="7d956-107">Para formatar o valor numérico</span><span class="sxs-lookup"><span data-stu-id="7d956-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="7d956-108">Exiba um valor decimal definindo <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> a propriedade como um inteiro e definindo a <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Propriedade como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="7d956-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="7d956-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="7d956-109">-or-</span></span>  
  
- <span data-ttu-id="7d956-110">Exiba um valor hexadecimal definindo a <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Propriedade como. `true`</span><span class="sxs-lookup"><span data-stu-id="7d956-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    > <span data-ttu-id="7d956-111">Mesmo que o valor seja exibido no formulário como hexadecimal, todos os testes que você executar na <xref:System.Windows.Forms.NumericUpDown.Value%2A> Propriedade testarão seu valor decimal.</span><span class="sxs-lookup"><span data-stu-id="7d956-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d956-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d956-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="7d956-113">Controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="7d956-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="7d956-114">Visão geral do controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="7d956-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
