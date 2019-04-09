---
title: 'Como: Criar uma caixa de texto somente leitura (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: be85eedf272e596ceb10e7510b8c99ce6aed0727
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130722"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="40d61-102">Como: Criar uma caixa de texto somente leitura (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="40d61-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="40d61-103">Você pode transformar uma caixa de texto editável do Windows Forms em um controle somente leitura.</span><span class="sxs-lookup"><span data-stu-id="40d61-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="40d61-104">Por exemplo, a caixa de texto pode exibir um valor que geralmente é editado, mas pode não ser no momento, devido ao estado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40d61-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="40d61-105">Para criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="40d61-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="40d61-106">Defina as <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="40d61-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="40d61-107">Com a propriedade definida como `true`, os usuários ainda podem rolar e realçar o texto em uma caixa de texto sem permitir alterações.</span><span class="sxs-lookup"><span data-stu-id="40d61-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="40d61-108">Um **cópia** comando é funcional em uma caixa de texto, mas **Recortar** e **colar** comandos não são.</span><span class="sxs-lookup"><span data-stu-id="40d61-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40d61-109">O <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade afeta somente a interação do usuário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="40d61-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="40d61-110">Você ainda pode alterar conteúdo da caixa de texto por meio de programação em tempo de execução, alterando o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade da caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="40d61-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d61-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40d61-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="40d61-112">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="40d61-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="40d61-113">Como: Controlar o ponto de inserção em um controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40d61-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="40d61-114">Como: Criar uma caixa de texto de senha com o controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40d61-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="40d61-115">Como: Inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="40d61-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="40d61-116">Como: Selecionar texto no controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40d61-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="40d61-117">Como: Exibir várias linhas no controle TextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40d61-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="40d61-118">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="40d61-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
