---
title: Usando controles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 8dcf79d449a8f8443774b133904e819dfd925288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526598"
---
# <a name="using-wpf-controls"></a><span data-ttu-id="53449-102">Usando controles WPF</span><span class="sxs-lookup"><span data-stu-id="53449-102">Using WPF Controls</span></span>
<span data-ttu-id="53449-103">Você pode usar controles do WPF (Windows Presentation Foundation) em seus aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="53449-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="53449-104">Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.</span><span class="sxs-lookup"><span data-stu-id="53449-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="53449-105">O Designer de Formulários do Windows fornece um ambiente de design visual para hospedar controles do Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="53449-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="53449-106">Um controle WPF é hospedado por um controle de formulários do Windows especial chamado <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="53449-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="53449-107">Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="53449-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="53449-108">Em tempo de design, você pode organizar o <xref:System.Windows.Forms.Integration.ElementHost> controlar exatamente como faria com qualquer controle de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="53449-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="53449-109">Você também pode usar controles do Windows Forms em seus aplicativos do WPF.</span><span class="sxs-lookup"><span data-stu-id="53449-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="53449-110">Para obter mais informações, consulte [Designer de WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).</span><span class="sxs-lookup"><span data-stu-id="53449-110">For more information, see [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53449-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="53449-111">In This Section</span></span>  
 [<span data-ttu-id="53449-112">Como copiar e colar um controle ElementHost no tempo de design</span><span class="sxs-lookup"><span data-stu-id="53449-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="53449-113">Mostra como copiar um controle Windows Presentation Foundation em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="53449-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="53449-114">Instruções passo a passo: organizando conteúdo WPF no Windows Forms no tempo de design</span><span class="sxs-lookup"><span data-stu-id="53449-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="53449-115">Mostra como usar os recursos de layout do Windows Forms, como ancoragem e guias de alinhamento para organizar controles do Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="53449-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>  
  
 [<span data-ttu-id="53449-116">Instruções passo a passo: alterando propriedades de um elemento WPF hospedado no tempo de design</span><span class="sxs-lookup"><span data-stu-id="53449-116">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 <span data-ttu-id="53449-117">Mostra o fluxo de trabalho entre o Designer de Formulários do Windows e o [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] para alterar as propriedades de controles WPF.</span><span class="sxs-lookup"><span data-stu-id="53449-117">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] for changing properties on WPF controls.</span></span>  
  
 [<span data-ttu-id="53449-118">Instruções passo a passo: criando novo conteúdo WPF no Windows Forms no tempo de design</span><span class="sxs-lookup"><span data-stu-id="53449-118">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="53449-119">Mostra como criar um controle do Windows Presentation Foundation para uso em aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="53449-119">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>  
  
 [<span data-ttu-id="53449-120">Instruções passo a passo: copiando e colando um controle ElementHost em Windows Forms separados</span><span class="sxs-lookup"><span data-stu-id="53449-120">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 <span data-ttu-id="53449-121">Mostra como copiar um controle do Windows Presentation Foundation de um Windows Form para outro.</span><span class="sxs-lookup"><span data-stu-id="53449-121">Shows how to copy a Windows Presentation Foundation control from one Windows Form to another.</span></span>  
  
 [<span data-ttu-id="53449-122">Instruções passo a passo: atribuindo conteúdo WPF no Windows Forms no tempo de design</span><span class="sxs-lookup"><span data-stu-id="53449-122">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="53449-123">Mostra como selecionar os tipos de controle do Windows Presentation Foundation que você deseja exibir em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="53449-123">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="53449-124">Instruções passo a passo: estilos de conteúdo WPF</span><span class="sxs-lookup"><span data-stu-id="53449-124">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="53449-125">Mostra o fluxo de trabalho entre o Designer de Formulários do Windows e o [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] para aplicar estilos aos controles do Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="53449-125">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="53449-126">Referência</span><span class="sxs-lookup"><span data-stu-id="53449-126">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="53449-127">Descreve uma classe que você pode usar para hospedar os controles do Windows Presentation Foundation em seus aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="53449-127">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="53449-128">Descreve uma classe que você pode usar para hospedar controles do Windows Forms no seu aplicativo do Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="53449-128">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53449-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="53449-129">Related Sections</span></span>  
 [<span data-ttu-id="53449-130">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="53449-130">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="53449-131">Descreve a interoperação entre as tecnologias Windows Presentation Foundation e Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="53449-131">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="53449-132">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="53449-132">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 <span data-ttu-id="53449-133">Descreve como criar controles de Windows Presentation Foundation no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53449-133">Describes how to design Windows Presentation Foundation controls in Visual Studio.</span></span>
