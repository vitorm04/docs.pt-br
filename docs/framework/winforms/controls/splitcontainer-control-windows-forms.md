---
title: Controle SplitContainer (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66eb0e8fc630696c86c8b85c85b67023bd568dc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="bf943-102">Controle SplitContainer (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bf943-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="bf943-103">O controle `SplitContainer` dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel.</span><span class="sxs-lookup"><span data-stu-id="bf943-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="bf943-104">Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.</span><span class="sxs-lookup"><span data-stu-id="bf943-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf943-105">No **caixa de ferramentas**, esse controle substitui o <xref:System.Windows.Forms.Splitter> controle que existia na versão anterior do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bf943-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="bf943-106">O `SplitContainer` controle é preferido sobre o <xref:System.Windows.Forms.Splitter> controle.</span><span class="sxs-lookup"><span data-stu-id="bf943-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="bf943-107">O <xref:System.Windows.Forms.Splitter> classe ainda está incluída no .NET Framework para compatibilidade com aplicativos existentes, mas recomendamos que você use o `SplitContainer` controle para novos projetos.</span><span class="sxs-lookup"><span data-stu-id="bf943-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="bf943-108">O controle `SplitContainer` permite que você crie interfaces do usuário complexas; muitas vezes, uma seleção em um painel determina quais objetos são mostrados no outro painel.</span><span class="sxs-lookup"><span data-stu-id="bf943-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="bf943-109">Essa disposição é muito eficiente para exibir e procurar informações.</span><span class="sxs-lookup"><span data-stu-id="bf943-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="bf943-110">Ter dois painéis permite que você agregue informações em áreas e a barra, ou "splitter", torna mais fácil para os usuários redimensionar os painéis.</span><span class="sxs-lookup"><span data-stu-id="bf943-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf943-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bf943-111">In This Section</span></span>  
 [<span data-ttu-id="bf943-112">Visão geral do controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="bf943-112">SplitContainer Control Overview</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="bf943-113">Apresenta o controle `SplitContainer` e descreve as propriedades, métodos e eventos mais usados.</span><span class="sxs-lookup"><span data-stu-id="bf943-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="bf943-114">Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida</span><span class="sxs-lookup"><span data-stu-id="bf943-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="bf943-115">Descreve como controlar o separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="bf943-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="bf943-116">Como dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="bf943-116">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="bf943-117">Descreve como controlar a orientação do separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="bf943-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="bf943-118">Como criar uma interface do usuário multipainel com o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf943-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="bf943-119">Cria uma interface do usuário em vários painéis que é semelhante à usada no Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="bf943-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="bf943-120">Consulte também [Como dividir uma janela horizontalmente usando o Designer](http://msdn.microsoft.com/library/ms233667\(v=vs.110\)), [Como criar uma Interface no estilo Windows Explorer em um Windows Form](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [Como criar uma Interface do usuário multipainéis com Windows Forms usando o Designer](http://msdn.microsoft.com/library/ms233661\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="bf943-120">Also see [How to: Split a Window Horizontally Using the Designer](http://msdn.microsoft.com/library/ms233667\(v=vs.110\)), [How to: Create a Windows Explorer–Style Interface on a Windows Form](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](http://msdn.microsoft.com/library/ms233661\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bf943-121">Referência</span><span class="sxs-lookup"><span data-stu-id="bf943-121">Reference</span></span>  
 <span data-ttu-id="bf943-122">Classe <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="bf943-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="bf943-123">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="bf943-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bf943-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="bf943-124">Related Sections</span></span>  
 [<span data-ttu-id="bf943-125">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf943-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="bf943-126">Fornece links para tópicos sobre os controles projetados especificamente para funcionar com o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bf943-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="bf943-127">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf943-127">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="bf943-128">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="bf943-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
