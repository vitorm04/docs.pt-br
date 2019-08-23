---
title: Controle ToolBar (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 13a56af0e52897a6fd4e11516fbf4c0b8f6d6b5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929561"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="df7d7-102">Controle ToolBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="df7d7-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="df7d7-103">O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle `ToolBar`, no entanto, o controle `ToolBar` é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="df7d7-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="df7d7-104">O controle `ToolBar` dos Windows Forms é usado em formulários como uma barra de controle que exibe uma linha de menus suspensos e botões de bitmap que ativam comandos.</span><span class="sxs-lookup"><span data-stu-id="df7d7-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="df7d7-105">Portanto, clicar em um botão de barra de ferramentas é equivalente a escolher um comando de menu.</span><span class="sxs-lookup"><span data-stu-id="df7d7-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="df7d7-106">Os botões podem ser configurados para parecer e se comportar como botões de push, menus suspensos ou separadores.</span><span class="sxs-lookup"><span data-stu-id="df7d7-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="df7d7-107">Normalmente, uma barra de ferramentas contém botões e menus que correspondem aos itens na estrutura do menu do aplicativo, fornecendo acesso rápido a funções e comandos usados com mais frequência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df7d7-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df7d7-108">A `ToolBar` Propriedade do <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> controle <xref:System.Windows.Forms.ContextMenu> usa uma instância da classe como uma referência.</span><span class="sxs-lookup"><span data-stu-id="df7d7-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="df7d7-109">Considere cuidadosamente a referência que você passa ao implementar esse tipo de botão em barras de ferramentas em seu aplicativo, pois a propriedade aceitará qualquer objeto herdado <xref:System.Windows.Forms.Menu> da classe.</span><span class="sxs-lookup"><span data-stu-id="df7d7-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df7d7-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="df7d7-110">In This Section</span></span>  
 [<span data-ttu-id="df7d7-111">Visão geral do controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="df7d7-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="df7d7-112">Apresenta os conceitos gerais do controle `ToolBar`, o que permite a criação de barras de ferramentas personalizadas com que seus usuários podem trabalhar.</span><span class="sxs-lookup"><span data-stu-id="df7d7-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="df7d7-113">Como: Adicionar botões a um controle ToolBar</span><span class="sxs-lookup"><span data-stu-id="df7d7-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="df7d7-114">Descreve como adicionar botões a um controle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="df7d7-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="df7d7-115">Como: Definir um ícone para um botão da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="df7d7-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="df7d7-116">Descreve como exibir ícones nos botões de um controle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="df7d7-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="df7d7-117">Como: Eventos do menu disparar para botões da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="df7d7-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="df7d7-118">Fornece instruções sobre como escrever o código para interpretar em qual botão o usuário clica em um controle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="df7d7-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="df7d7-119">Consulte [também como: Defina um ícone para um botão da barra de ferramentas](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md)usando [o designer, como: Adicione botões a um controle ToolBar usando o designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="df7d7-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="df7d7-120">Referência</span><span class="sxs-lookup"><span data-stu-id="df7d7-120">Reference</span></span>  
 <span data-ttu-id="df7d7-121">Classe <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="df7d7-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="df7d7-122">Fornece informações de referência sobre a classe e seus membros.</span><span class="sxs-lookup"><span data-stu-id="df7d7-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="df7d7-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="df7d7-123">Related Sections</span></span>  
 [<span data-ttu-id="df7d7-124">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="df7d7-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="df7d7-125">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="df7d7-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="df7d7-126">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="df7d7-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="df7d7-127">Descreve as barras de ferramentas que podem hospedar menus, controles e controles de usuário em aplicativos dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="df7d7-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
