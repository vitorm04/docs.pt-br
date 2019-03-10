---
title: 'Como: Definir atributos de fonte para o controle RichTextBox dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 92578bd267230f5878bda9533bd117e8f98d8f13
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714678"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="0f2fe-102">Como: Definir atributos de fonte para o controle RichTextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f2fe-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="0f2fe-103">Os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle tem várias opções para formatar o texto que ele exibe.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="0f2fe-104">Você pode fazer os caracteres selecionados em negrito, sublinhado ou itálico, usando o <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="0f2fe-105">Você também pode usar essa propriedade para alterar o tamanho e a face de tipo dos caracteres selecionados.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="0f2fe-106">O <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade permite que você alterar a cor dos caracteres selecionados.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="0f2fe-107">Para alterar a aparência dos caracteres</span><span class="sxs-lookup"><span data-stu-id="0f2fe-107">To change the appearance of characters</span></span>  
  
1.  <span data-ttu-id="0f2fe-108">Defina o <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade para uma fonte apropriada.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="0f2fe-109">Para permitir que os usuários definam a família de fontes, tamanho e face de tipos em um aplicativo, você normalmente usaria o <xref:System.Windows.Forms.FontDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="0f2fe-110">Para obter uma visão geral, consulte [Visão geral do componente FontDialog](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0f2fe-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="0f2fe-111">Defina o <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade como uma cor apropriada.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="0f2fe-112">Para permitir que os usuários definam a cor em um aplicativo, você normalmente usaria o <xref:System.Windows.Forms.ColorDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="0f2fe-113">Para obter uma visão geral, consulte [Visão geral do componente ColorDialog](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0f2fe-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0f2fe-114">Essas propriedades afetam apenas o texto selecionado ou, se nenhum texto estiver selecionado, o texto que é digitado no local atual do ponto de inserção.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="0f2fe-115">Para obter informações sobre como selecionar texto de forma programática, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f2fe-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f2fe-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f2fe-116">See also</span></span>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="0f2fe-117">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0f2fe-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="0f2fe-118">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f2fe-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
