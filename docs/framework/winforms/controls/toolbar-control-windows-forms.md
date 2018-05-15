---
title: Controle ToolBar (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: e21b31805eb0b840866313f16cc85ea33c84e515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="29a7d-102">Controle ToolBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="29a7d-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="29a7d-103">O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle `ToolBar`, no entanto, o controle `ToolBar` é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="29a7d-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="29a7d-104">O controle `ToolBar` dos Windows Forms é usado em formulários como uma barra de controle que exibe uma linha de menus suspensos e botões de bitmap que ativam comandos.</span><span class="sxs-lookup"><span data-stu-id="29a7d-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="29a7d-105">Portanto, clicar em um botão de barra de ferramentas é equivalente a escolher um comando de menu.</span><span class="sxs-lookup"><span data-stu-id="29a7d-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="29a7d-106">Os botões podem ser configurados para parecer e se comportar como botões de push, menus suspensos ou separadores.</span><span class="sxs-lookup"><span data-stu-id="29a7d-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="29a7d-107">Normalmente, uma barra de ferramentas contém botões e menus que correspondem aos itens na estrutura do menu do aplicativo, fornecendo acesso rápido a funções e comandos usados com mais frequência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29a7d-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29a7d-108">O `ToolBar` do controle <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> propriedade tem uma instância do <xref:System.Windows.Forms.ContextMenu> classe como uma referência.</span><span class="sxs-lookup"><span data-stu-id="29a7d-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="29a7d-109">Considere cuidadosamente a referência de passar ao implementar esse tipo de botão na barra de ferramentas em seu aplicativo, como a propriedade aceitará qualquer objeto que herda de <xref:System.Windows.Forms.Menu> classe.</span><span class="sxs-lookup"><span data-stu-id="29a7d-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29a7d-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="29a7d-110">In This Section</span></span>  
 [<span data-ttu-id="29a7d-111">Visão geral do controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="29a7d-111">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="29a7d-112">Apresenta os conceitos gerais do controle `ToolBar`, o que permite a criação de barras de ferramentas personalizadas com que seus usuários podem trabalhar.</span><span class="sxs-lookup"><span data-stu-id="29a7d-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="29a7d-113">Como adicionar botões a um controle de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="29a7d-113">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="29a7d-114">Descreve como adicionar botões a um controle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="29a7d-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="29a7d-115">Como definir um ícone para um botão de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="29a7d-115">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="29a7d-116">Descreve como exibir ícones nos botões de um controle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="29a7d-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="29a7d-117">Como disparar eventos de menu para botões da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="29a7d-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="29a7d-118">Fornece instruções sobre como escrever o código para interpretar em qual botão o usuário clica em um controle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="29a7d-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="29a7d-119">Consulte também [Como definir um ícone para um botão de barra de ferramentas usando o Designer](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [Como adicionar botões a um controle de barra de ferramentas usando o Designer](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="29a7d-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [How to: Add Buttons to a ToolBar Control Using the Designer](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="29a7d-120">Referência</span><span class="sxs-lookup"><span data-stu-id="29a7d-120">Reference</span></span>  
 <span data-ttu-id="29a7d-121">Classe <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="29a7d-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="29a7d-122">Fornece informações de referência sobre a classe e seus membros.</span><span class="sxs-lookup"><span data-stu-id="29a7d-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="29a7d-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="29a7d-123">Related Sections</span></span>  
 [<span data-ttu-id="29a7d-124">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29a7d-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="29a7d-125">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="29a7d-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="29a7d-126">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="29a7d-126">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 <span data-ttu-id="29a7d-127">Descreve as barras de ferramentas que podem hospedar menus, controles e controles de usuário em aplicativos dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="29a7d-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
