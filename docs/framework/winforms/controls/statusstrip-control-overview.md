---
title: "Visão geral do controle StatusStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5f06d155972846b3c04a60d448b300d8cdc5d1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="8aea4-102">Visão geral do controle StatusStrip</span><span class="sxs-lookup"><span data-stu-id="8aea4-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="8aea4-103">Um <xref:System.Windows.Forms.StatusStrip> controle exibe informações sobre um objeto que está sendo visualizado em um <xref:System.Windows.Forms.Form>, componentes do objeto ou as informações contextuais relacionadas à operação do objeto dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8aea4-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="8aea4-104">Normalmente, um <xref:System.Windows.Forms.StatusStrip> consiste em controle <xref:System.Windows.Forms.ToolStripStatusLabel> objetos, cada um deles exibe o texto, um ícone ou ambos.</span><span class="sxs-lookup"><span data-stu-id="8aea4-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="8aea4-105">O <xref:System.Windows.Forms.StatusStrip> também podem conter <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, e <xref:System.Windows.Forms.ToolStripProgressBar> controles.</span><span class="sxs-lookup"><span data-stu-id="8aea4-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="8aea4-106">O padrão <xref:System.Windows.Forms.StatusStrip> não tem nenhum painéis.</span><span class="sxs-lookup"><span data-stu-id="8aea4-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="8aea4-107">Para adicionar painéis para um <xref:System.Windows.Forms.StatusStrip>, use o <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="8aea4-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="8aea4-108">Há suporte abrangente para manipulação <xref:System.Windows.Forms.StatusStrip> itens e comandos comuns no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8aea4-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="8aea4-109">Consulte também [Editor de coleção de itens StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [Caixa de diálogo de tarefas StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8aea4-109">Also see [StatusStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="8aea4-110">Embora o <xref:System.Windows.Forms.StatusStrip> substitua e estenda o controle <xref:System.Windows.Forms.StatusBar> de versões anteriores, <xref:System.Windows.Forms.StatusBar> é mantido para compatibilidade com versões anteriores e uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="8aea4-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="8aea4-111">Membros StatusStrip importantes</span><span class="sxs-lookup"><span data-stu-id="8aea4-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="8aea4-112">Nome</span><span class="sxs-lookup"><span data-stu-id="8aea4-112">Name</span></span>|<span data-ttu-id="8aea4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8aea4-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="8aea4-114">Obtém ou define um valor que indica se o <xref:System.Windows.Forms.StatusStrip> dá suporte à funcionalidade de estouro.</span><span class="sxs-lookup"><span data-stu-id="8aea4-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="8aea4-115">Obtém ou define um valor que indica se o <xref:System.Windows.Forms.StatusStrip> expande de ponta a ponta em seu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="8aea4-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="8aea4-116">Classes complementares importantes do StatusStrip</span><span class="sxs-lookup"><span data-stu-id="8aea4-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="8aea4-117">Nome</span><span class="sxs-lookup"><span data-stu-id="8aea4-117">Name</span></span>|<span data-ttu-id="8aea4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8aea4-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="8aea4-119">Representa um painel em um controle <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="8aea4-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="8aea4-120">Exibe um associado <xref:System.Windows.Forms.ToolStripDropDown> do qual o usuário pode selecionar um único item.</span><span class="sxs-lookup"><span data-stu-id="8aea4-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="8aea4-121">Representa um controle de duas partes que é um botão padrão e um menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="8aea4-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="8aea4-122">Exibe o estado de conclusão de um processo.</span><span class="sxs-lookup"><span data-stu-id="8aea4-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8aea4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8aea4-123">See Also</span></span>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
