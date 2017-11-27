---
title: "Como exibir várias linhas no controle TextBox dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8f39e031835275818504151e66834f0634b7f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="eaec3-102">Como exibir várias linhas no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eaec3-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="eaec3-103">Por padrão, o Windows Forms <xref:System.Windows.Forms.TextBox> controle exibe uma única linha de texto e não exibe barras de rolagem.</span><span class="sxs-lookup"><span data-stu-id="eaec3-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="eaec3-104">Se o texto for maior que o espaço disponível, apenas parte do texto ficará visível.</span><span class="sxs-lookup"><span data-stu-id="eaec3-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="eaec3-105">Você pode alterar esse comportamento padrão definindo o <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, e <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propriedades com valores apropriados.</span><span class="sxs-lookup"><span data-stu-id="eaec3-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="eaec3-106">Exibir um retorno de carro no controle TextBox</span><span class="sxs-lookup"><span data-stu-id="eaec3-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="eaec3-107">Para exibir um retorno de carro em uma multilinha <xref:System.Windows.Forms.TextBox>, use o <xref:System.Environment.NewLine%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="eaec3-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="eaec3-108">Lembre-se que a interpretação de caracteres de escape (\\) é específica a um idioma.</span><span class="sxs-lookup"><span data-stu-id="eaec3-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="eaec3-109">O Visual Basic usa `Chr$(13) & Chr$(10)` para a combinação de retorno de carro e caracteres de avanço de linha.</span><span class="sxs-lookup"><span data-stu-id="eaec3-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="eaec3-110">Exibir várias linhas no controle TextBox</span><span class="sxs-lookup"><span data-stu-id="eaec3-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="eaec3-111">Defina a propriedade <xref:System.Windows.Forms.TextBox.Multiline%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="eaec3-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="eaec3-112">Se <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> é `true` (o padrão), em seguida, o texto no controle aparecerá como um ou mais parágrafos; caso contrário, ele aparecerá como uma lista, no qual algumas linhas podem ser cortadas na borda do controle.</span><span class="sxs-lookup"><span data-stu-id="eaec3-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="eaec3-113">Definir o <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propriedade para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="eaec3-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="eaec3-114">Valor</span><span class="sxs-lookup"><span data-stu-id="eaec3-114">Value</span></span>|<span data-ttu-id="eaec3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="eaec3-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="eaec3-116">Use esse valor se o texto será um parágrafo que quase sempre se ajusta ao controle.</span><span class="sxs-lookup"><span data-stu-id="eaec3-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="eaec3-117">O usuário poderá usar o ponteiro do mouse para mover-se dentro do controle se o texto for grande demais para ser exibido totalmente ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="eaec3-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="eaec3-118">Use esse valor se você deseja exibir uma lista de linhas, algumas das quais podem ser maiores que a largura do <xref:System.Windows.Forms.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="eaec3-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="eaec3-119">Use esse valor se a lista pode ser maior que a altura do controle.</span><span class="sxs-lookup"><span data-stu-id="eaec3-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="eaec3-120">Definir o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="eaec3-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="eaec3-121">Valor</span><span class="sxs-lookup"><span data-stu-id="eaec3-121">Value</span></span>|<span data-ttu-id="eaec3-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="eaec3-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="eaec3-123">O texto no controle não será encapsulado automaticamente, portanto ele rolará para a direita até atingir uma quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="eaec3-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="eaec3-124">Use esse valor se você escolheu <xref:System.Windows.Forms.ScrollBars.Horizontal> barras de rolagem ou <xref:System.Windows.Forms.ScrollBars.Both>acima.</span><span class="sxs-lookup"><span data-stu-id="eaec3-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="eaec3-125">`true` (padrão)</span><span class="sxs-lookup"><span data-stu-id="eaec3-125">`true` (default)</span></span>|<span data-ttu-id="eaec3-126">A barra de rolagem horizontal não será exibida.</span><span class="sxs-lookup"><span data-stu-id="eaec3-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="eaec3-127">Use esse valor se você escolheu <xref:System.Windows.Forms.ScrollBars.Vertical> barras de rolagem ou <xref:System.Windows.Forms.ScrollBars.None>acima, para exibir um ou mais parágrafos.</span><span class="sxs-lookup"><span data-stu-id="eaec3-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eaec3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaec3-128">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="eaec3-129">Visão geral do controle TextBox</span><span class="sxs-lookup"><span data-stu-id="eaec3-129">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="eaec3-130">Como controlar o ponto de inserção em um controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eaec3-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="eaec3-131">Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eaec3-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="eaec3-132">Como criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="eaec3-132">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="eaec3-133">Como inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="eaec3-133">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="eaec3-134">Como selecionar texto no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eaec3-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="eaec3-135">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="eaec3-135">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
