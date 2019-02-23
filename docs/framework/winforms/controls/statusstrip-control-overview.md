---
title: Visão geral do controle StatusStrip
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: 2558c9c89bc296a3a92512a7d1a0ee7110dbcc21
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745231"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="cd0a1-102">Visão geral do controle StatusStrip</span><span class="sxs-lookup"><span data-stu-id="cd0a1-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="cd0a1-103">Um <xref:System.Windows.Forms.StatusStrip> controle exibe informações sobre um objeto que está sendo visualizado em um <xref:System.Windows.Forms.Form>, componentes do objeto ou informações contextuais relacionadas à operação do objeto dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="cd0a1-104">Normalmente, uma <xref:System.Windows.Forms.StatusStrip> controle consiste em <xref:System.Windows.Forms.ToolStripStatusLabel> objetos, cada um deles exibindo texto, um ícone ou ambos.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="cd0a1-105">O <xref:System.Windows.Forms.StatusStrip> também pode conter <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, e <xref:System.Windows.Forms.ToolStripProgressBar> controles.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="cd0a1-106">O padrão <xref:System.Windows.Forms.StatusStrip> não tem nenhum painel.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="cd0a1-107">Para adicionar painéis a um <xref:System.Windows.Forms.StatusStrip>, use o <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="cd0a1-108">Há suporte abrangente para manipulação <xref:System.Windows.Forms.StatusStrip> itens e comandos comuns no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="cd0a1-109">Consulte também [Editor de coleção de itens StatusStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100)) e [caixa de diálogo de tarefas StatusStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cd0a1-109">Also see [StatusStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100)) and [StatusStrip Tasks Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100)).</span></span>  
  
 <span data-ttu-id="cd0a1-110">Embora o <xref:System.Windows.Forms.StatusStrip> substitua e estenda o controle <xref:System.Windows.Forms.StatusBar> de versões anteriores, <xref:System.Windows.Forms.StatusBar> é mantido para compatibilidade com versões anteriores e uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="cd0a1-111">Membros StatusStrip importantes</span><span class="sxs-lookup"><span data-stu-id="cd0a1-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="cd0a1-112">Nome</span><span class="sxs-lookup"><span data-stu-id="cd0a1-112">Name</span></span>|<span data-ttu-id="cd0a1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd0a1-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="cd0a1-114">Obtém ou define um valor que indica se o <xref:System.Windows.Forms.StatusStrip> dá suporte à funcionalidade de estouro.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="cd0a1-115">Obtém ou define um valor que indica se o <xref:System.Windows.Forms.StatusStrip> se amplia de ponta a ponta em seu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="cd0a1-116">Classes complementares importantes do StatusStrip</span><span class="sxs-lookup"><span data-stu-id="cd0a1-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="cd0a1-117">Nome</span><span class="sxs-lookup"><span data-stu-id="cd0a1-117">Name</span></span>|<span data-ttu-id="cd0a1-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd0a1-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="cd0a1-119">Representa um painel em um controle <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="cd0a1-120">Exibe um associado <xref:System.Windows.Forms.ToolStripDropDown> do qual o usuário pode selecionar um único item.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="cd0a1-121">Representa um controle de duas partes que é um botão padrão e um menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="cd0a1-122">Exibe o estado de conclusão de um processo.</span><span class="sxs-lookup"><span data-stu-id="cd0a1-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd0a1-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd0a1-123">See also</span></span>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
