---
title: Controle SplitContainer (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: 504a2396902fecf2ac17c2db434fef68ff2ece45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009715"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="9a229-102">Controle SplitContainer (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9a229-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="9a229-103">O controle `SplitContainer` dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel.</span><span class="sxs-lookup"><span data-stu-id="9a229-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="9a229-104">Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.</span><span class="sxs-lookup"><span data-stu-id="9a229-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a229-105">No **caixa de ferramentas**, esse controle substitui o <xref:System.Windows.Forms.Splitter> controle que existia na versão anterior do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9a229-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="9a229-106">O `SplitContainer` controle é preferida em relação a <xref:System.Windows.Forms.Splitter> controle.</span><span class="sxs-lookup"><span data-stu-id="9a229-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="9a229-107">O <xref:System.Windows.Forms.Splitter> classe ainda está incluída no .NET Framework para compatibilidade com aplicativos existentes, mas recomendamos que você use o `SplitContainer` controle para novos projetos.</span><span class="sxs-lookup"><span data-stu-id="9a229-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="9a229-108">O controle `SplitContainer` permite que você crie interfaces do usuário complexas; muitas vezes, uma seleção em um painel determina quais objetos são mostrados no outro painel.</span><span class="sxs-lookup"><span data-stu-id="9a229-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="9a229-109">Essa disposição é muito eficiente para exibir e procurar informações.</span><span class="sxs-lookup"><span data-stu-id="9a229-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="9a229-110">Ter dois painéis permite que você agregue informações em áreas e a barra, ou "splitter", torna mais fácil para os usuários redimensionar os painéis.</span><span class="sxs-lookup"><span data-stu-id="9a229-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a229-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9a229-111">In This Section</span></span>  
 [<span data-ttu-id="9a229-112">Visão geral do controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="9a229-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="9a229-113">Apresenta o controle `SplitContainer` e descreve as propriedades, métodos e eventos mais usados.</span><span class="sxs-lookup"><span data-stu-id="9a229-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="9a229-114">Como: Definir redimensionamento e posicionamento de comportamento em uma janela dividida</span><span class="sxs-lookup"><span data-stu-id="9a229-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="9a229-115">Descreve como controlar o separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="9a229-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="9a229-116">Como: Dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="9a229-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="9a229-117">Descreve como controlar a orientação do separador dentro do controle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="9a229-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="9a229-118">Como: Criar uma Interface do usuário Multipainel com Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a229-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="9a229-119">Cria uma interface do usuário em vários painéis que é semelhante à usada no Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="9a229-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="9a229-120">Consulte também [como: Dividir uma janela horizontalmente usando o Designer](how-to-split-a-window-horizontally-using-the-designer.md), [como: Criar uma Interface no estilo Explorer do Windows em um Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [como: Criar uma Interface do usuário Multipainel com Windows Forms usando o Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="9a229-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9a229-121">Referência</span><span class="sxs-lookup"><span data-stu-id="9a229-121">Reference</span></span>  
 <span data-ttu-id="9a229-122">Classe <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="9a229-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="9a229-123">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="9a229-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a229-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9a229-124">Related Sections</span></span>  
 [<span data-ttu-id="9a229-125">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a229-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="9a229-126">Fornece links para tópicos sobre os controles projetados especificamente para funcionar com o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9a229-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="9a229-127">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a229-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="9a229-128">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="9a229-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
