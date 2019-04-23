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
ms.openlocfilehash: c73200eb1c373f1d723ba82f2e6be5b625496b59
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300496"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a><span data-ttu-id="84a35-102">Como: Definir e retornar valores numéricos com o controle NumericUpDown do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84a35-102">How to: Set and Return Numeric Values with the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="84a35-103">O valor numérico de formulários do Windows <xref:System.Windows.Forms.NumericUpDown> controle é determinado pelo seu <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="84a35-103">The numeric value of the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control is determined by its <xref:System.Windows.Forms.NumericUpDown.Value%2A> property.</span></span> <span data-ttu-id="84a35-104">Você pode escrever testes condicionais para o valor do controle, assim como ocorre com qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="84a35-104">You can write conditional tests for the control's value just as with any other property.</span></span> <span data-ttu-id="84a35-105">Uma vez a <xref:System.Windows.Forms.NumericUpDown.Value%2A> estiver definida, você pode ajustá-lo diretamente ao escrever código para executar operações nela ou você pode chamar o <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> e <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="84a35-105">Once the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property is set, you can adjust it directly by writing code to perform operations on it, or you can call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> methods.</span></span>  
  
### <a name="to-set-the-numeric-value"></a><span data-ttu-id="84a35-106">Para definir o valor numérico</span><span class="sxs-lookup"><span data-stu-id="84a35-106">To set the numeric value</span></span>  
  
1. <span data-ttu-id="84a35-107">Atribuir um valor para o <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade no código ou na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="84a35-107">Assign a value to the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code or in the Properties window.</span></span>  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     <span data-ttu-id="84a35-108">- ou -</span><span class="sxs-lookup"><span data-stu-id="84a35-108">-or-</span></span>  
  
2. <span data-ttu-id="84a35-109">Chame o <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ou <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> método para aumentar ou diminuir o valor, o valor especificado no <xref:System.Windows.Forms.NumericUpDown.Increment%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="84a35-109">Call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> or <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> method to increase or decrease the value by the amount specified in the <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property.</span></span>  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a><span data-ttu-id="84a35-110">Para retornar o valor numérico</span><span class="sxs-lookup"><span data-stu-id="84a35-110">To return the numeric value</span></span>  
  
-   <span data-ttu-id="84a35-111">Acesso a <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade no código.</span><span class="sxs-lookup"><span data-stu-id="84a35-111">Access the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84a35-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84a35-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [<span data-ttu-id="84a35-113">Controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="84a35-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="84a35-114">Visão geral do controle NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="84a35-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
