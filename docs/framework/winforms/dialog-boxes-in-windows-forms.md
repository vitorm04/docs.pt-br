---
title: "Caixas de diálogo no Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1660bf08f10a7d4e0db4b7ae8d58fd631986974c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="0da56-102">Caixas de diálogo no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0da56-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="0da56-103">Caixas de diálogo são usadas para interagir com o usuário e recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="0da56-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="0da56-104">Em termos simples, uma caixa de diálogo é um formulário com seus <xref:System.Windows.Forms.FormBorderStyle> propriedade de enumeração definida como `FixedDialog`.</span><span class="sxs-lookup"><span data-stu-id="0da56-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="0da56-105">Você pode construir sua própria caixa de diálogo personalizada usando o Designer de Formulários do Windows em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0da56-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="0da56-106">Adicione controles como `Label`, `Textbox` e `Button` para personalizar caixas de diálogo conforme suas necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="0da56-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="0da56-107">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] também inclui caixas de diálogo predefinidas, como **Abrir Arquivo** e caixas de mensagem, que você pode adaptar para seus próprios aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0da56-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="0da56-108">Para obter mais informações, confira [Controles e componentes da caixa de diálogo](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0da56-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0da56-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0da56-109">In This Section</span></span>  
 [<span data-ttu-id="0da56-110">Como exibir caixas de diálogo para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0da56-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="0da56-111">Fornece instruções para mostrar caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="0da56-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="0da56-112">[Como recuperar informações da caixa de diálogo de maneira seletiva usando propriedades múltiplas](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0da56-113">[Como recuperar informações do formulário pai de uma caixa de diálogo](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0da56-114">[Entrada de usuário em caixas de diálogo](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-114">[User Input to Dialog Boxes](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0da56-115">[Como recuperar o resultado para caixas de diálogo](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-115">[How to: Retrieve the Result for Dialog Boxes](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0da56-116">[Instruções passo a passo: recuperando informações da caixa de diálogo usando objetos de forma coletiva](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0da56-117">[Como fechar as caixas de diálogo e manter a entrada do usuário](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-117">[How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0da56-118">[Como criar caixas de diálogo em tempo de design](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-118">[How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0da56-119">[Como exibir caixas de mensagens](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0da56-119">[How to: Display Message Boxes](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0da56-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="0da56-120">Related Sections</span></span>  
 [<span data-ttu-id="0da56-121">Controles e componentes da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="0da56-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="0da56-122">Lista os controles da caixa de diálogo predefinida.</span><span class="sxs-lookup"><span data-stu-id="0da56-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="0da56-123">Alterando a aparência dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0da56-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="0da56-124">Contém links para tópicos que descrevem como alterar a aparência de aplicativos dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0da56-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="0da56-125">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="0da56-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="0da56-126">Explica como incorporar o controle guia em uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="0da56-126">Explains how you incorporate the tab control into a dialog box.</span></span>
