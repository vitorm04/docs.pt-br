---
title: Como criar uma caixa de texto somente leitura
description: Saiba como transformar uma caixa de texto editável Windows Forms em uma caixa de texto de Windows Forms somente leitura.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619358"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="c37c8-103">Como criar uma caixa de texto somente leitura (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c37c8-103">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="c37c8-104">Você pode transformar uma caixa de texto Windows Forms editável em um controle somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c37c8-104">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="c37c8-105">Por exemplo, a caixa de texto pode exibir um valor que geralmente é editado, mas pode não estar no momento, devido ao estado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c37c8-105">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="c37c8-106">Para criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="c37c8-106">To create a read-only text box</span></span>

1. <span data-ttu-id="c37c8-107">Defina a <xref:System.Windows.Forms.TextBox> Propriedade do controle <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> como `true` .</span><span class="sxs-lookup"><span data-stu-id="c37c8-107">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="c37c8-108">Com a propriedade definida como `true` , os usuários ainda podem rolar e realçar o texto em uma caixa de texto sem permitir alterações.</span><span class="sxs-lookup"><span data-stu-id="c37c8-108">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="c37c8-109">Um comando de **cópia** é funcional em uma caixa de texto, mas os comandos **recortar** e **colar** não são.</span><span class="sxs-lookup"><span data-stu-id="c37c8-109">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c37c8-110">A <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade afeta apenas a interação do usuário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c37c8-110">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="c37c8-111">Você ainda pode alterar o conteúdo da caixa de texto programaticamente em tempo de execução alterando a <xref:System.Windows.Forms.TextBox.Text%2A> propriedade da caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="c37c8-111">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="c37c8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c37c8-112">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="c37c8-113">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="c37c8-113">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="c37c8-114">Como controlar o ponto de inserção em um controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c37c8-114">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="c37c8-115">Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c37c8-115">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c37c8-116">Como inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c37c8-116">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="c37c8-117">Como selecionar texto no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c37c8-117">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c37c8-118">Como exibir várias linhas no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c37c8-118">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c37c8-119">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="c37c8-119">TextBox Control</span></span>](textbox-control-windows-forms.md)
