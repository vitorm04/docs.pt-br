---
title: Como mostrar uma paleta de cores com o componente ColorDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141777"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="a7a17-102">Como mostrar uma paleta de cores com o componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="a7a17-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="a7a17-103">O componente [ColorDialog](colordialog-component-windows-forms.md) exibe uma paleta de cores e retorna uma propriedade contendo a cor que o usuário selecionou.</span><span class="sxs-lookup"><span data-stu-id="a7a17-103">The [ColorDialog](colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="a7a17-104">Para escolher uma cor usando o componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="a7a17-104">To choose a color using the ColorDialog component</span></span>  
  
1. <span data-ttu-id="a7a17-105">Exibir a caixa <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> de diálogo usando o método.</span><span class="sxs-lookup"><span data-stu-id="a7a17-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="a7a17-106">Use <xref:System.Windows.Forms.DialogResult> a propriedade para determinar como a caixa de diálogo foi fechada.</span><span class="sxs-lookup"><span data-stu-id="a7a17-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="a7a17-107">Use <xref:System.Windows.Forms.ColorDialog.Color%2A> a propriedade <xref:System.Windows.Forms.ColorDialog> do componente para definir a cor escolhida.</span><span class="sxs-lookup"><span data-stu-id="a7a17-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="a7a17-108">No exemplo abaixo, <xref:System.Windows.Forms.Button> o <xref:System.Windows.Forms.Control.Click> manipulador de <xref:System.Windows.Forms.ColorDialog> eventos do controle abre um componente.</span><span class="sxs-lookup"><span data-stu-id="a7a17-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="a7a17-109">Quando uma cor é escolhida e o <xref:System.Windows.Forms.Button> usuário clica **em OK,** a cor de fundo do controle é definida como a cor escolhida.</span><span class="sxs-lookup"><span data-stu-id="a7a17-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="a7a17-110">O exemplo pressupõe <xref:System.Windows.Forms.Button> que seu <xref:System.Windows.Forms.ColorDialog> formulário tenha um controle e um componente.</span><span class="sxs-lookup"><span data-stu-id="a7a17-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     <span data-ttu-id="a7a17-111">(Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a7a17-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a7a17-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="a7a17-112">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="a7a17-113">Componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="a7a17-113">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
