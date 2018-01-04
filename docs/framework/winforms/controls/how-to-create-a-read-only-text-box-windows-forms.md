---
title: Como criar uma caixa de texto somente leitura (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 264ef1a7c1f121f889d57dcb0e36e216610418fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="5d231-102">Como criar uma caixa de texto somente leitura (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5d231-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="5d231-103">Você pode transformar uma caixa de texto Windows Forms editável em um controle somente leitura.</span><span class="sxs-lookup"><span data-stu-id="5d231-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="5d231-104">Por exemplo, a caixa de texto pode exibir um valor que não estejam no momento, devido ao estado do aplicativo, mas geralmente é editado.</span><span class="sxs-lookup"><span data-stu-id="5d231-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="5d231-105">Para criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d231-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="5d231-106">Definir o <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="5d231-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="5d231-107">Com a propriedade definida como `true`, os usuários ainda podem rolar e realce o texto em uma caixa de texto sem permitir alterações.</span><span class="sxs-lookup"><span data-stu-id="5d231-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="5d231-108">Um **cópia** comando está funcionando em uma caixa de texto, mas **Recortar** e **colar** comandos não são.</span><span class="sxs-lookup"><span data-stu-id="5d231-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d231-109">O <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade afeta apenas a interação do usuário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5d231-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="5d231-110">Você ainda pode alterar conteúdo da caixa de texto programaticamente no tempo de execução alterando o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade da caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="5d231-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d231-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d231-111">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="5d231-112">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="5d231-112">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="5d231-113">Como controlar o ponto de inserção em um controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d231-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="5d231-114">Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d231-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="5d231-115">Como inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d231-115">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="5d231-116">Como selecionar texto no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d231-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="5d231-117">Como exibir várias linhas no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d231-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="5d231-118">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="5d231-118">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
