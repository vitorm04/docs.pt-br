---
title: "Visão geral do componente HelpProvider (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42a788e44fde80662748e19a7244ce77bb26118f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="c8a38-102">Visão geral do componente HelpProvider (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c8a38-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="c8a38-103">O componente [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) dos Windows Forms é usado para associar um arquivo da Ajuda HTML 1.x (um arquivo .chm, produzido com o Workshop de Ajuda HTML ou um arquivo .htm) ao seu aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="c8a38-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="c8a38-104">É possível fornecer ajuda de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="c8a38-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="c8a38-105">Fornece Ajuda contextual para controles nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8a38-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="c8a38-106">Fornece Ajuda contextual em uma caixa de diálogo específica ou controles específicos em uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c8a38-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="c8a38-107">Abra um arquivo de Ajuda para áreas específicas, como a página principal de um sumário, índice ou uma função de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c8a38-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="c8a38-108">Usando o provedor de ajuda</span><span class="sxs-lookup"><span data-stu-id="c8a38-108">Using the Help Provider</span></span>  
 <span data-ttu-id="c8a38-109">Adicionando um <xref:System.Windows.Forms.HelpProvider> componente para o formulário do Windows permite que os outros controles no formulário para expor as propriedades de Ajuda do <xref:System.Windows.Forms.HelpProvider> componente.</span><span class="sxs-lookup"><span data-stu-id="c8a38-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="c8a38-110">Isso habilita você a fornecer ajuda para os controles no seu Windows Form.</span><span class="sxs-lookup"><span data-stu-id="c8a38-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="c8a38-111">Você pode associar um arquivo de ajuda com o <xref:System.Windows.Forms.HelpProvider> componente usando o <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c8a38-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="c8a38-112">Especifique o tipo de ajuda fornecidos chamando <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> e fornecendo um valor da <xref:System.Windows.Forms.HelpNavigator> enumeração para o controle especificado.</span><span class="sxs-lookup"><span data-stu-id="c8a38-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="c8a38-113">Forneça a palavra-chave ou um tópico para obter ajuda ao chamar o <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c8a38-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="c8a38-114">Opcionalmente, para associar uma cadeia de caracteres de ajuda específica com outro controle, use o <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c8a38-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="c8a38-115">A cadeia de caracteres associada a um controle usando esse método é exibida em uma janela pop-up quando o usuário pressiona a tecla F1 enquanto o controle tem o foco.</span><span class="sxs-lookup"><span data-stu-id="c8a38-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="c8a38-116">Se <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> não tiver sido definido, você deve usar <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> para fornecer o texto de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="c8a38-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="c8a38-117">Se você tiver definido as <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> e a cadeia de caracteres de Ajuda, ajuda baseada em <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> terá precedência.</span><span class="sxs-lookup"><span data-stu-id="c8a38-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8a38-118">Você pode encontrar problemas ao usar o caminho relativo ao especificar o caminho para o arquivo de Ajuda no <xref:System.Windows.Forms.Help.ShowHelp%2A> método ou <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade do <xref:System.Windows.Forms.HelpProvider> controle.</span><span class="sxs-lookup"><span data-stu-id="c8a38-118">You may encounter problems using the relative path when specifiying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="c8a38-119">Por isso, verifique se você usou o caminho de arquivo absoluto para especificar o arquivo de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="c8a38-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a38-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8a38-120">See Also</span></span>  
 [<span data-ttu-id="c8a38-121">Sistemas de Ajuda em Aplicativos dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8a38-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
