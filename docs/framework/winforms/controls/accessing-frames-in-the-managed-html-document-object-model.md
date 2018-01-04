---
title: Acessando quadros no Document Object Model HTML gerenciado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9355596982025bf9834924a0de8e79e7073fc0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a><span data-ttu-id="7fb9d-102">Acessando quadros no Document Object Model HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="7fb9d-102">Accessing Frames in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="7fb9d-103">Alguns documentos HTML são compostos de *quadros* ou janelas que podem manter seus próprios documentos HTML distintos.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-103">Some HTML documents are composed out of *frames*, or windows that can hold their own distinct HTML documents.</span></span> <span data-ttu-id="7fb9d-104">Usar quadros facilita a criação de páginas HTML na qual uma ou mais partes da página permanecem estáticas, como uma barra de navegação, enquanto outros quadros alterar seu conteúdo constantemente.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-104">Using frames makes it easy to create HTML pages in which one or more pieces of the page remain static, such as a navigation bar, while other frames constantly change their content.</span></span>  
  
 <span data-ttu-id="7fb9d-105">Criadores de HTML podem criar quadros de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="7fb9d-105">HTML authors can create frames in one of two ways:</span></span>  
  
-   <span data-ttu-id="7fb9d-106">Usando as marcas `FRAMESET` e `FRAME`, que criam janelas fixas.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-106">Using the `FRAMESET` and `FRAME` tags, which create fixed windows.</span></span>  
  
 <span data-ttu-id="7fb9d-107">-ou-</span><span class="sxs-lookup"><span data-stu-id="7fb9d-107">-or-</span></span>  
  
-   <span data-ttu-id="7fb9d-108">Usando a marca `IFRAME`, que cria uma janela flutuante que pode ser reposicionada em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-108">Using the `IFRAME` tag, which creates a floating window that can be repositioned at run time.</span></span>  
  
1.  <span data-ttu-id="7fb9d-109">Como os quadros contêm documentos HTML, eles são representados no Modelo de Objeto do Documento (DOM) como elementos de janela e de quadro.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-109">Because frames contain HTML documents, they are represented in the Document Object Model (DOM) as both window elements and frame elements.</span></span>  
  
2.  <span data-ttu-id="7fb9d-110">Quando você acessa um `FRAME` ou `IFRAME` marca usando a coleção de quadros de <xref:System.Windows.Forms.HtmlWindow>, você está recuperando o elemento correspondente ao quadro da janela.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-110">When you access a `FRAME` or `IFRAME` tag by using the Frames collection of <xref:System.Windows.Forms.HtmlWindow>, you are retrieving the window element corresponding to the frame.</span></span> <span data-ttu-id="7fb9d-111">Isso representa todas as propriedades dinâmicas do quadro, como sua URL, documento e tamanho atual.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-111">This represents all of the frame's dynamic properties, such as its current URL, document, and size.</span></span>  
  
3.  <span data-ttu-id="7fb9d-112">Quando você acessa um `FRAME` ou `IFRAME` marca usando o <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> propriedade <xref:System.Windows.Forms.HtmlWindow>, o <xref:System.Windows.Forms.HtmlElement.Children%2A> coleção ou métodos, como <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> ou <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, você está recuperando o elemento de quadro.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-112">When you access a `FRAME` or `IFRAME` tag by using the <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> property of <xref:System.Windows.Forms.HtmlWindow>, the <xref:System.Windows.Forms.HtmlElement.Children%2A> collection, or methods such as <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> or <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, you are retrieving the frame element.</span></span> <span data-ttu-id="7fb9d-113">Isso representa as propriedades estáticas do quadro, incluindo a URL especificada no arquivo HTML original.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-113">This represents the static properties of the frame, including the URL specified in the original HTML file.</span></span>  
  
## <a name="frames-and-security"></a><span data-ttu-id="7fb9d-114">Quadros e Segurança</span><span class="sxs-lookup"><span data-stu-id="7fb9d-114">Frames and Security</span></span>  
 <span data-ttu-id="7fb9d-115">O acesso aos quadros é complicado pelo fato de que o HTML DOM gerenciado implementa uma medida de segurança, conhecida como *segurança de scripts entre quadros*.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-115">Access to frames is complicated by the fact that the managed HTML DOM implements a security measure known as *cross-frame scripting security*.</span></span> <span data-ttu-id="7fb9d-116">Se um documento contiver um `FRAMESET` com duas ou mais `FRAME`s em domínios diferentes, esses `FRAME`s não poderão interagir entre si.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-116">If a document contains a `FRAMESET` with two or more `FRAME`s in different domains, these `FRAME`s cannot interact with one another.</span></span> <span data-ttu-id="7fb9d-117">Em outras palavras, um `FRAME` que exibe o conteúdo do site não pode acessar informações em um `FRAME` que hospeda um site de terceiros, como http://www.adatum.com/.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-117">In other words, a `FRAME` that displays content from your Web site cannot access information in a `FRAME` that hosts a third-party site such as http://www.adatum.com/.</span></span> <span data-ttu-id="7fb9d-118">Essa segurança é implementada no nível do <xref:System.Windows.Forms.HtmlWindow> classe.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-118">This security is implemented at the level of the <xref:System.Windows.Forms.HtmlWindow> class.</span></span> <span data-ttu-id="7fb9d-119">Você pode obter informações gerais sobre um `FRAME` hospedagem outro site da Web, como a URL, mas não poderão acessar seu <xref:System.Windows.Forms.HtmlWindow.Document%2A> ou alterar o tamanho ou local de sua hospedagem `FRAME` ou `IFRAME`.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-119">You can obtain general information about a `FRAME` hosting another Web site, such as its URL, but you will be unable to access its <xref:System.Windows.Forms.HtmlWindow.Document%2A> or change the size or location of its hosting `FRAME` or `IFRAME`.</span></span>  
  
 <span data-ttu-id="7fb9d-120">Esta regra também se aplica ao windows que você abre usando o <xref:System.Windows.Forms.HtmlWindow.Open%2A> e <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-120">This rule also applies to windows that you open using the <xref:System.Windows.Forms.HtmlWindow.Open%2A> and <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> methods.</span></span> <span data-ttu-id="7fb9d-121">Se a janela abrir está em um domínio diferente da página hospedada no <xref:System.Windows.Forms.WebBrowser> controle, você não poderá mover a janela ou examinar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-121">If the window you open is in a different domain from the page hosted in the <xref:System.Windows.Forms.WebBrowser> control, you will not be able to move that window or examine its contents.</span></span> <span data-ttu-id="7fb9d-122">Essas restrições são aplicadas também se você usar o <xref:System.Windows.Forms.WebBrowser> controle para exibir um site que é diferente do site da Web usado para implantar seu aplicativo com base em formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-122">These restrictions are also enforced if you use the <xref:System.Windows.Forms.WebBrowser> control to display a Web site that is different from the Web site used to deploy your Windows Forms-based application.</span></span> <span data-ttu-id="7fb9d-123">Se você usar [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] tecnologia de implantação para instalar o aplicativo do site da Web A e você usar o <xref:System.Windows.Forms.WebBrowser> para exibir o site da Web B, não será capaz de dados do site de acesso do B.</span><span class="sxs-lookup"><span data-stu-id="7fb9d-123">If you use [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] deployment technology to install your application from Web site A, and you use the <xref:System.Windows.Forms.WebBrowser> to display Web site B, you will not be able to access Web site B's data.</span></span>  
  
 <span data-ttu-id="7fb9d-124">Para obter mais informações sobre a segurança de scripts entre sites, consulte[Sobre Scripts Entre Quadros e Segurança](http://msdn.microsoft.com/library/ms533028.aspx).</span><span class="sxs-lookup"><span data-stu-id="7fb9d-124">For more information about cross-site scripting, see[About Cross-Frame Scripting and Security](http://msdn.microsoft.com/library/ms533028.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb9d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fb9d-125">See Also</span></span>  
 [<span data-ttu-id="7fb9d-126">Elemento de quadro &#124; quadro de objeto</span><span class="sxs-lookup"><span data-stu-id="7fb9d-126">FRAME Element &#124; frame Object</span></span>](http://msdn.microsoft.com/library/ms535250.aspx)  
 [<span data-ttu-id="7fb9d-127">Usando o Modelo de Objeto do Documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="7fb9d-127">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
