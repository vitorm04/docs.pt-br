---
title: 'Como: Definir a máscara de entrada'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: ac747bf46c4dd1451e58615b1ec0311d75c899e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760483"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="55916-102">Como: Definir a máscara de entrada</span><span class="sxs-lookup"><span data-stu-id="55916-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="55916-103">O controle de caixa de texto mascarado é um controle de caixa de texto avançado que dá suporte a uma sintaxe declarativa para aceitar ou rejeitar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="55916-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="55916-104">Definindo a propriedade Máscara, você pode especificar a entrada do usuário permitida sem escrever qualquer lógica de validação personalizada no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55916-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="55916-105">Para obter mais informações, consulte a seção comentários do <xref:System.Windows.Forms.MaskedTextBox> classe.</span><span class="sxs-lookup"><span data-stu-id="55916-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="55916-106">Definindo definir a propriedade Máscara manualmente</span><span class="sxs-lookup"><span data-stu-id="55916-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="55916-107">Se estiver familiarizado com os caracteres que a propriedade Máscara dá suporte, você poderá inseri-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="55916-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="55916-108">Para obter um resumo dos caracteres que a propriedade máscara dá suporte, consulte a seção de comentários do <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="55916-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="55916-109">Definir a propriedade Mask manualmente</span><span class="sxs-lookup"><span data-stu-id="55916-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="55916-110">Na **Design** exibição, selecione um <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="55916-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="55916-111">No **propriedades** janela, localize o <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="55916-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="55916-112">Digite a máscara desejada.</span><span class="sxs-lookup"><span data-stu-id="55916-112">Type the mask that you want.</span></span> <span data-ttu-id="55916-113">Por exemplo, digite `###`.</span><span class="sxs-lookup"><span data-stu-id="55916-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="55916-114">Usando a caixa de diálogo Máscara de Entrada</span><span class="sxs-lookup"><span data-stu-id="55916-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="55916-115">A caixa de diálogo Máscara de Entrada fornece algumas máscaras de entrada predefinidas.</span><span class="sxs-lookup"><span data-stu-id="55916-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="55916-116">Você também pode alterar as máscaras predefinidas ou inserir sua própria máscara manualmente.</span><span class="sxs-lookup"><span data-stu-id="55916-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="55916-117">Abrir a caixa de diálogo Máscara de Entrada</span><span class="sxs-lookup"><span data-stu-id="55916-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="55916-118">Na **Design** exibição, selecione um <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="55916-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="55916-119">Clique na marca inteligente para abrir o painel **Tarefas de MaskedTextBox**.</span><span class="sxs-lookup"><span data-stu-id="55916-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="55916-120">Clique em **Definir Máscara**.</span><span class="sxs-lookup"><span data-stu-id="55916-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="55916-121">\- ou -</span><span class="sxs-lookup"><span data-stu-id="55916-121">\- or -</span></span>  
  
    1. <span data-ttu-id="55916-122">No **propriedades** janela, selecione o <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="55916-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="55916-123">Clique no botão de reticências na coluna do valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="55916-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="55916-124">A caixa de diálogo **Máscara de Entrada** é exibida.</span><span class="sxs-lookup"><span data-stu-id="55916-124">The **Input Mask** dialog box appears.</span></span>  
  
### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="55916-125">Usar a caixa de diálogo Máscara de Entrada</span><span class="sxs-lookup"><span data-stu-id="55916-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="55916-126">(Opcional) Clique em uma das máscaras predefinidas na lista.</span><span class="sxs-lookup"><span data-stu-id="55916-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="55916-127">(Opcional) Edite a máscara predefinida na caixa **Máscara**.</span><span class="sxs-lookup"><span data-stu-id="55916-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="55916-128">(Opcional) Digite uma nova máscara na caixa **Máscara**.</span><span class="sxs-lookup"><span data-stu-id="55916-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="55916-129">Ou seja, não é necessário usar uma das máscaras predefinidas.</span><span class="sxs-lookup"><span data-stu-id="55916-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55916-130">A caixa visualização exibe os caracteres que o usuário vê no <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="55916-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="55916-131">Esses caracteres são um guia para ajudar o usuário a inserir os dados corretamente.</span><span class="sxs-lookup"><span data-stu-id="55916-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="55916-132">Selecione ou desmarque a caixa de seleção **Usar ValidatingType**.</span><span class="sxs-lookup"><span data-stu-id="55916-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="55916-133">A caixa de seleção **Usar ValidatingType** especifica se um tipo de dados é usado para verificar a entrada de dados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="55916-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="55916-134">Para obter mais informações, consulte a propriedade <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.</span><span class="sxs-lookup"><span data-stu-id="55916-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="55916-135">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="55916-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="55916-136">A máscara é inserida na propriedade **Máscara** na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="55916-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55916-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55916-137">See also</span></span>

- [<span data-ttu-id="55916-138">Passo a passo: Trabalhando com o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="55916-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
