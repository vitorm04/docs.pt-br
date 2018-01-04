---
title: "Visão geral do controle LinkLabel (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73bbd04b9ef5d2d0c5457dafb794435b3a4db380
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="678f2-102">Visão geral do controle LinkLabel (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="678f2-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="678f2-103">Windows Forms <xref:System.Windows.Forms.LinkLabel> controle permite que você adicionar links de estilo da Web para aplicativos de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="678f2-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="678f2-104">Você pode usar o <xref:System.Windows.Forms.LinkLabel> controle tudo o que você pode usar o <xref:System.Windows.Forms.Label> controlar para; você também pode definir a parte do texto como um link para um arquivo, pasta ou página da Web.</span><span class="sxs-lookup"><span data-stu-id="678f2-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you also can set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="678f2-105">O que você pode fazer com o Controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="678f2-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="678f2-106">Além de todos os métodos, propriedades e eventos de <xref:System.Windows.Forms.Label> controle, o <xref:System.Windows.Forms.LinkLabel> controle tem propriedades de hiperlinks e cores de link.</span><span class="sxs-lookup"><span data-stu-id="678f2-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="678f2-107">O <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade define a área do texto que ativa o link.</span><span class="sxs-lookup"><span data-stu-id="678f2-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="678f2-108">O <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, e <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> propriedades definidas as cores do link.</span><span class="sxs-lookup"><span data-stu-id="678f2-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="678f2-109">O <xref:System.Windows.Forms.LinkLabel.LinkClicked> evento determina o que acontece quando o texto do link é selecionado.</span><span class="sxs-lookup"><span data-stu-id="678f2-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="678f2-110">O uso mais simples do <xref:System.Windows.Forms.LinkLabel> é de controle exibir um link único usando o <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriedade, mas você também pode exibir vários hiperlinks usando o <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="678f2-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="678f2-111">O <xref:System.Windows.Forms.LinkLabel.Links%2A> propriedade permite que você acesse uma coleção de links.</span><span class="sxs-lookup"><span data-stu-id="678f2-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="678f2-112">Você também pode especificar dados de <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriedade de cada indivíduo <xref:System.Windows.Forms.LinkLabel.Link> objeto.</span><span class="sxs-lookup"><span data-stu-id="678f2-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="678f2-113">O valor de <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriedade pode ser usada para armazenar o local de um arquivo de vídeo ou o endereço de um site da Web.</span><span class="sxs-lookup"><span data-stu-id="678f2-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678f2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="678f2-114">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="678f2-115">Visão geral do controle Label</span><span class="sxs-lookup"><span data-stu-id="678f2-115">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="678f2-116">Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="678f2-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="678f2-117">Como alterar a aparência do controle LinkLabel dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="678f2-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
