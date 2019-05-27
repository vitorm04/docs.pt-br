---
title: 'Como: Mostrar uma lista de fontes ao componente FontDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: 05e9b5e1280d0318354b0d47f4d78f7ec1c5f4e7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053442"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a><span data-ttu-id="fd7fd-102">Como: Mostrar uma lista de fontes ao componente FontDialog</span><span class="sxs-lookup"><span data-stu-id="fd7fd-102">How to: Show a Font List with the FontDialog Component</span></span>
<span data-ttu-id="fd7fd-103">O componente [FontDialog](fontdialog-component-windows-forms.md) permite aos usuários selecionar uma fonte, bem como alterar seus aspectos de exibição, como peso e tamanho.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-103">The [FontDialog](fontdialog-component-windows-forms.md) component allows users to select a font, as well as change its display aspects, such as its weight and size.</span></span>  
  
 <span data-ttu-id="fd7fd-104">A fonte selecionada na caixa de diálogo é retornada no <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-104">The font selected in the dialog box is returned in the <xref:System.Windows.Forms.FontDialog.Font%2A> property.</span></span> <span data-ttu-id="fd7fd-105">Assim, tirar proveito da fonte selecionada pelo usuário é tão fácil quanto ler uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-105">Thus, taking advantage of the font selected by the user is as easy as reading a property.</span></span>  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a><span data-ttu-id="fd7fd-106">Para selecionar as propriedades de fonte usando o componente FontDialog</span><span class="sxs-lookup"><span data-stu-id="fd7fd-106">To select font properties using the FontDialog Component</span></span>  
  
1. <span data-ttu-id="fd7fd-107">Exibir a caixa de diálogo usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-107">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="fd7fd-108">Use o <xref:System.Windows.Forms.DialogResult> propriedade para determinar como a caixa de diálogo foi fechada.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-108">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="fd7fd-109">Use o <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade para definir a fonte desejada.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-109">Use the <xref:System.Windows.Forms.FontDialog.Font%2A> property to set the desired font.</span></span>  
  
     <span data-ttu-id="fd7fd-110">No exemplo a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre um <xref:System.Windows.Forms.FontDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-110">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="fd7fd-111">Quando uma fonte é escolhido e o usuário clica **Okey**, o <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade de um <xref:System.Windows.Forms.TextBox> controle que está no formulário é definido como a fonte escolhida.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-111">When a font is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.FontDialog.Font%2A> property of a <xref:System.Windows.Forms.TextBox> control that is on the form is set to the chosen font.</span></span> <span data-ttu-id="fd7fd-112">O exemplo supõe que seu formulário tem um <xref:System.Windows.Forms.Button> controle, um <xref:System.Windows.Forms.TextBox> controle e um <xref:System.Windows.Forms.FontDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-112">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a  <xref:System.Windows.Forms.TextBox> control, and a <xref:System.Windows.Forms.FontDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     <span data-ttu-id="fd7fd-113">(Visual C# e o Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="fd7fd-113">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fd7fd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd7fd-114">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="fd7fd-115">Componente FontDialog</span><span class="sxs-lookup"><span data-stu-id="fd7fd-115">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
