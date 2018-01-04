---
title: Sistemas de Ajuda em aplicativos do Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b2f5d067d487bbd5b91576927aee21a9a44fde0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="085bd-102">Sistemas de Ajuda em aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="085bd-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="085bd-103">Uma das cortesias mais importantes que você, como desenvolvedor de aplicativos, pode fornecer aos seus usuários com é um sistema de Ajuda competente.</span><span class="sxs-lookup"><span data-stu-id="085bd-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="085bd-104">Esse é o local que eles procuram quando ficam confusos ou desorientados.</span><span class="sxs-lookup"><span data-stu-id="085bd-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="085bd-105">É fácil fornecer um sistema de Ajuda em um aplicativo baseado no Windows usando o [componente HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="085bd-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="085bd-106">Diferentes tipos de ajuda</span><span class="sxs-lookup"><span data-stu-id="085bd-106">Different Types of Help</span></span>  
 <span data-ttu-id="085bd-107">Windows Forms <xref:System.Windows.Forms.HelpProvider> componente é usado para associar um arquivo de ajuda HTML Help 1. x (um arquivo. chm, produzido com o HTML Help Workshop, ou um arquivo. htm) com seu aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="085bd-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="085bd-108">O <xref:System.Windows.Forms.HelpProvider> componente pode ser usado para fornecer ajuda contextual para controles de formulários do Windows ou controles específicos.</span><span class="sxs-lookup"><span data-stu-id="085bd-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="085bd-109">Além disso, o <xref:System.Windows.Forms.HelpProvider> componente pode abrir um arquivo de ajuda para áreas específicas, como a página principal de uma tabela de conteúdo, um índice ou uma função de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="085bd-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="085bd-110">Para obter informações gerais sobre o <xref:System.Windows.Forms.HelpProvider> componente, consulte [visão geral do componente HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="085bd-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="085bd-111">Para obter informações sobre como usar o <xref:System.Windows.Forms.HelpProvider> componente para exibir ajuda pop-up nos formulários do Windows, consulte [como: exibir ajuda pop-up](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="085bd-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="085bd-112">Para obter informações sobre como usar o <xref:System.Windows.Forms.ToolTip> componente para exibir a Ajuda de controle específicos, consulte [Control Help Using ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span><span class="sxs-lookup"><span data-stu-id="085bd-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="085bd-113">Você pode gerar arquivos da Ajuda HTML 1.x com o HTML Help Workshop.</span><span class="sxs-lookup"><span data-stu-id="085bd-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="085bd-114">Para obter mais informações sobre a Ajuda HTML, veja o "HTML Help Workshop" ou outros tópicos de "Ajuda HTML" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="085bd-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="085bd-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="085bd-115">See Also</span></span>  
 [<span data-ttu-id="085bd-116">Integrando a Ajuda do Usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="085bd-116">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="085bd-117">Componente HelpProvider</span><span class="sxs-lookup"><span data-stu-id="085bd-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 [<span data-ttu-id="085bd-118">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="085bd-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 [<span data-ttu-id="085bd-119">Visão geral dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="085bd-119">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 [<span data-ttu-id="085bd-120">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="085bd-120">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
