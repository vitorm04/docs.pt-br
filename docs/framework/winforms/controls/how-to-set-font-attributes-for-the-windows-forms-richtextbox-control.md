---
title: 'Como: Definir atributos de fonte para o controle RichTextBox do Windows Forms'
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
ms.openlocfilehash: 4919e94c23b1a67680ea0f360304ee0f75c7f425
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963217"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="05efa-102">Como: Definir atributos de fonte para o controle RichTextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05efa-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="05efa-103">O controle <xref:System.Windows.Forms.RichTextBox> Windows Forms tem várias opções para formatar o texto exibido.</span><span class="sxs-lookup"><span data-stu-id="05efa-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="05efa-104">Você pode tornar os caracteres selecionados em negrito, sublinhados ou itálicos usando a <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="05efa-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="05efa-105">Você também pode usar essa propriedade para alterar o tamanho e a face de tipo dos caracteres selecionados.</span><span class="sxs-lookup"><span data-stu-id="05efa-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="05efa-106">A <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade permite que você altere a cor dos caracteres selecionados.</span><span class="sxs-lookup"><span data-stu-id="05efa-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="05efa-107">Para alterar a aparência dos caracteres</span><span class="sxs-lookup"><span data-stu-id="05efa-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="05efa-108">Defina a <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> Propriedade como uma fonte apropriada.</span><span class="sxs-lookup"><span data-stu-id="05efa-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="05efa-109">Para permitir que os usuários definam a família de fontes, o tamanho e a face de tipos em um aplicativo <xref:System.Windows.Forms.FontDialog> , você normalmente usaria o componente.</span><span class="sxs-lookup"><span data-stu-id="05efa-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="05efa-110">Para obter uma visão geral, consulte [Visão geral do componente FontDialog](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="05efa-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="05efa-111">Defina a <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Propriedade como uma cor apropriada.</span><span class="sxs-lookup"><span data-stu-id="05efa-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="05efa-112">Para permitir que os usuários definam a cor em um aplicativo, você normalmente usaria o <xref:System.Windows.Forms.ColorDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="05efa-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="05efa-113">Para obter uma visão geral, consulte [Visão geral do componente ColorDialog](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="05efa-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
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
    > <span data-ttu-id="05efa-114">Essas propriedades afetam apenas o texto selecionado ou, se nenhum texto estiver selecionado, o texto que é digitado no local atual do ponto de inserção.</span><span class="sxs-lookup"><span data-stu-id="05efa-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="05efa-115">Para obter informações sobre como selecionar texto programaticamente, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="05efa-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05efa-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05efa-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="05efa-117">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="05efa-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="05efa-118">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05efa-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
