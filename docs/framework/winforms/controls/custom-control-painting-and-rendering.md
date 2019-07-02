---
title: Pintura e renderização de controle personalizada
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 14abac5678bfffa3cdb61307fd3cb54681c82a99
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506088"
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="e26ec-102">Pintura e renderização de controle personalizada</span><span class="sxs-lookup"><span data-stu-id="e26ec-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="e26ec-103">A pintura personalizada de controles é uma das muitas tarefas complicadas que são facilitadas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e26ec-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="e26ec-104">Ao criar um controle personalizado, você tem muitas opções em relação à aparência gráfica dele.</span><span class="sxs-lookup"><span data-stu-id="e26ec-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="e26ec-105">Ao criar um controle que herda de `Control`, você deverá fornecer o código que permite ao controle renderizar sua representação gráfica.</span><span class="sxs-lookup"><span data-stu-id="e26ec-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="e26ec-106">Ao criar um controle de usuário herdando de `UserControl` ou herdando de um dos controles dos Windows Forms, você pode substituir a representação gráfica padrão e fornecer seu próprio código de elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="e26ec-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="e26ec-107">Se você deseja fornecer renderização personalizada para os controles membros de um `UserControl` que você está criando, suas opções tornam-se mais limitadas, mas ainda proporcionam uma ampla gama de possibilidades gráficas para seus aplicativos e controles.</span><span class="sxs-lookup"><span data-stu-id="e26ec-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e26ec-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e26ec-108">In This Section</span></span>  
 [<span data-ttu-id="e26ec-109">Renderizando um controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e26ec-109">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)  
 <span data-ttu-id="e26ec-110">Mostra como programar a lógica que exibe um controle.</span><span class="sxs-lookup"><span data-stu-id="e26ec-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="e26ec-111">Controles desenhados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e26ec-111">User-Drawn Controls</span></span>](user-drawn-controls.md)  
 <span data-ttu-id="e26ec-112">Fornece uma visão geral das etapas necessárias para escrever e substituir um código de renderização para o seu controle.</span><span class="sxs-lookup"><span data-stu-id="e26ec-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="e26ec-113">Controles constituintes</span><span class="sxs-lookup"><span data-stu-id="e26ec-113">Constituent Controls</span></span>](constituent-controls.md)  
 <span data-ttu-id="e26ec-114">Descreve como implementar o código de renderização personalizada para controles membros em seus formulários e controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="e26ec-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="e26ec-115">Como: Deixar o controle invisível em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e26ec-115">How to: Make Your Control Invisible at Run Time</span></span>](how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="e26ec-116">Mostra como usar o <xref:System.Windows.Forms.Control.Visible%2A> propriedade ocultar e mostrar um controle.</span><span class="sxs-lookup"><span data-stu-id="e26ec-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="e26ec-117">Como: Dar ao controle uma tela de fundo transparente</span><span class="sxs-lookup"><span data-stu-id="e26ec-117">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="e26ec-118">Mostra como usar o <xref:System.Windows.Forms.Control.SetStyle%2A> método para criar uma cor de plano de fundo opaca, transparente ou parcialmente transparente.</span><span class="sxs-lookup"><span data-stu-id="e26ec-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="e26ec-119">Renderizando controles com estilos visuais</span><span class="sxs-lookup"><span data-stu-id="e26ec-119">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="e26ec-120">Mostra como renderizar controles com estilos visuais em sistemas operacionais que dão suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="e26ec-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e26ec-121">Referência</span><span class="sxs-lookup"><span data-stu-id="e26ec-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="e26ec-122">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="e26ec-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="e26ec-123">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="e26ec-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="e26ec-124">Descreve esse método.</span><span class="sxs-lookup"><span data-stu-id="e26ec-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e26ec-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e26ec-125">Related Sections</span></span>  
 [<span data-ttu-id="e26ec-126">Como: Criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="e26ec-126">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="e26ec-127">Apresenta a funcionalidade de gráficos GDI+ da perspectiva do Visual Studio e fornece links para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e26ec-127">Introduces GDI+ graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="e26ec-128">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="e26ec-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="e26ec-129">Descreve os tipos de controles personalizados que você pode criar.</span><span class="sxs-lookup"><span data-stu-id="e26ec-129">Describes the kinds of custom controls you can author.</span></span>
