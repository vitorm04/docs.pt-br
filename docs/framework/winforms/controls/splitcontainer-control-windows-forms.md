---
title: Controle SplitContainer (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: d860763e935c88619e3355661038757d00247dfd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963584"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="ac7d4-102">Controle SplitContainer (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ac7d4-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="ac7d4-103">O controle `SplitContainer` dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="ac7d4-104">Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac7d4-105">Na **caixa de ferramentas**, esse controle substitui <xref:System.Windows.Forms.Splitter> o controle que estava lá na versão anterior do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="ac7d4-106">O `SplitContainer` controle é muito preferido sobre o <xref:System.Windows.Forms.Splitter> controle.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="ac7d4-107">A <xref:System.Windows.Forms.Splitter> classe ainda está incluída no .NET Framework para compatibilidade com os aplicativos existentes, mas é altamente recomendável que você use `SplitContainer` o controle para novos projetos.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="ac7d4-108">O controle `SplitContainer` permite que você crie interfaces do usuário complexas; muitas vezes, uma seleção em um painel determina quais objetos são mostrados no outro painel.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="ac7d4-109">Essa disposição é muito eficiente para exibir e procurar informações.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="ac7d4-110">Ter dois painéis permite que você agregue informações em áreas e a barra, ou "splitter", torna mais fácil para os usuários redimensionar os painéis.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac7d4-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ac7d4-111">In This Section</span></span>  
 [<span data-ttu-id="ac7d4-112">Visão geral do controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="ac7d4-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="ac7d4-113">Apresenta o controle `SplitContainer` e descreve as propriedades, métodos e eventos mais usados.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="ac7d4-114">Como: Definir o comportamento de redimensionamento e posicionamento em uma janela de divisão</span><span class="sxs-lookup"><span data-stu-id="ac7d4-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="ac7d4-115">Descreve como controlar o separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="ac7d4-116">Como: Dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="ac7d4-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="ac7d4-117">Descreve como controlar a orientação do separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="ac7d4-118">Como: Criar uma interface do usuário multipainel com Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac7d4-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="ac7d4-119">Cria uma interface do usuário em vários painéis que é semelhante à usada no Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="ac7d4-120">Consulte [também como: Dividir uma janela horizontalmente usando o designer](how-to-split-a-window-horizontally-using-the-designer.md), [como: Criar uma interface de estilo do Windows Explorer em um Windows](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md)Form [, como: Crie uma interface do usuário multipainel com Windows Forms usando o](create-a-multipane-user-interface-with-wf-using-the-designer.md)designer.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ac7d4-121">Referência</span><span class="sxs-lookup"><span data-stu-id="ac7d4-121">Reference</span></span>  
 <span data-ttu-id="ac7d4-122">Classe <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="ac7d4-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="ac7d4-123">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac7d4-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ac7d4-124">Related Sections</span></span>  
 [<span data-ttu-id="ac7d4-125">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac7d4-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="ac7d4-126">Fornece links para tópicos sobre os controles projetados especificamente para funcionar com o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="ac7d4-127">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac7d4-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="ac7d4-128">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="ac7d4-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
