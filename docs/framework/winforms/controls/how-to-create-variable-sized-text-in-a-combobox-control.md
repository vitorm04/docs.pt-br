---
title: Como criar texto dimensionado da variável em um controle ComboBox
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: a76e1d78cd9fade550fa846488e8bf4a93a21c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="d8bb3-102">Como criar texto dimensionado da variável em um controle ComboBox</span><span class="sxs-lookup"><span data-stu-id="d8bb3-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="d8bb3-103">Este exemplo demonstra o desenho personalizado de texto em uma <xref:System.Windows.Forms.ComboBox> controle.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="d8bb3-104">Quando um item atende a certos critérios, ele é desenhado em uma fonte maior e ativado vermelho.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8bb3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8bb3-105">Example</span></span>  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8bb3-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d8bb3-106">Compiling the Code</span></span>  
 <span data-ttu-id="d8bb3-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d8bb3-107">This example requires:</span></span>  
  
-   <span data-ttu-id="d8bb3-108">Um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-108">A Windows form.</span></span>  
  
-   <span data-ttu-id="d8bb3-109">Um <xref:System.Windows.Forms.ComboBox> controle chamado `ListBox1` com três itens no <xref:System.Windows.Forms.ComboBox.Items%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="d8bb3-110">Neste exemplo, três itens são nomeados `"One", Two", and Three"`.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="d8bb3-111">O <xref:System.Windows.Forms.ComboBox.DrawMode%2A> propriedade `ComboBox1` deve ser definido como <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d8bb3-112">Essa técnica também é aplicável para o <xref:System.Windows.Forms.ListBox> controle — você pode substituir um <xref:System.Windows.Forms.ListBox> para o <xref:System.Windows.Forms.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>  
  
-   <span data-ttu-id="d8bb3-113">Referências aos namespaces <xref:System.Windows.Forms?displayProperty=nameWithType> e <xref:System.Drawing?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8bb3-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bb3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8bb3-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [<span data-ttu-id="d8bb3-115">Controles com suporte para desenho do proprietário interno</span><span class="sxs-lookup"><span data-stu-id="d8bb3-115">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [<span data-ttu-id="d8bb3-116">Controle ListBox</span><span class="sxs-lookup"><span data-stu-id="d8bb3-116">ListBox Control</span></span>](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [<span data-ttu-id="d8bb3-117">Controle ComboBox</span><span class="sxs-lookup"><span data-stu-id="d8bb3-117">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
