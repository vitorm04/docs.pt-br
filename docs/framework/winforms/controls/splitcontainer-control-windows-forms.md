---
title: Controle SplitContainer
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: ac04f60847aa6f77c11637f37b5ec94b6f7ef341
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742910"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="41804-102">Controle SplitContainer (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="41804-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="41804-103">O controle `SplitContainer` dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel.</span><span class="sxs-lookup"><span data-stu-id="41804-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="41804-104">Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.</span><span class="sxs-lookup"><span data-stu-id="41804-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41804-105">Na **caixa de ferramentas**, esse controle substitui o controle de <xref:System.Windows.Forms.Splitter> que estava lá na versão anterior do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41804-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="41804-106">O controle de `SplitContainer` é muito preferível ao controle de <xref:System.Windows.Forms.Splitter>.</span><span class="sxs-lookup"><span data-stu-id="41804-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="41804-107">A classe <xref:System.Windows.Forms.Splitter> ainda está incluída no .NET Framework para compatibilidade com os aplicativos existentes, mas é altamente recomendável que você use o controle de `SplitContainer` para novos projetos.</span><span class="sxs-lookup"><span data-stu-id="41804-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="41804-108">O controle `SplitContainer` permite que você crie interfaces do usuário complexas; muitas vezes, uma seleção em um painel determina quais objetos são mostrados no outro painel.</span><span class="sxs-lookup"><span data-stu-id="41804-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="41804-109">Essa disposição é muito eficiente para exibir e procurar informações.</span><span class="sxs-lookup"><span data-stu-id="41804-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="41804-110">Ter dois painéis permite que você agregue informações em áreas e a barra, ou "splitter", torna mais fácil para os usuários redimensionar os painéis.</span><span class="sxs-lookup"><span data-stu-id="41804-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41804-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="41804-111">In This Section</span></span>  
 [<span data-ttu-id="41804-112">Visão geral do controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="41804-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="41804-113">Apresenta o controle `SplitContainer` e descreve as propriedades, métodos e eventos mais usados.</span><span class="sxs-lookup"><span data-stu-id="41804-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="41804-114">Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida</span><span class="sxs-lookup"><span data-stu-id="41804-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="41804-115">Descreve como controlar o separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="41804-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="41804-116">Como dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="41804-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="41804-117">Descreve como controlar a orientação do separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="41804-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="41804-118">Como criar uma interface do usuário multipainel com o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41804-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="41804-119">Cria uma interface do usuário em vários painéis que é semelhante à usada no Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="41804-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="41804-120">Consulte também [Como dividir uma janela horizontalmente usando o Designer](how-to-split-a-window-horizontally-using-the-designer.md), [Como criar uma Interface no estilo Windows Explorer em um Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [Como criar uma Interface do usuário multipainéis com Windows Forms usando o Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="41804-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="41804-121">Referência</span><span class="sxs-lookup"><span data-stu-id="41804-121">Reference</span></span>  
 <span data-ttu-id="41804-122">Classe <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="41804-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="41804-123">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="41804-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41804-124">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="41804-124">Related Sections</span></span>  
 [<span data-ttu-id="41804-125">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41804-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="41804-126">Fornece links para tópicos sobre os controles projetados especificamente para funcionar com o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="41804-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="41804-127">Controles a serem usados no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41804-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="41804-128">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="41804-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
