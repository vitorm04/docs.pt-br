---
title: 'Como: Acessar a fonte HTML no Modelo de Objeto do Documento HTML gerenciado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: 98341270ffdb7788aa5c2713682d7d836bde220e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203256"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="2ce68-102">Como: Acessar a fonte HTML no Modelo de Objeto do Documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="2ce68-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="2ce68-103">As propriedades <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> e <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> no controle <xref:System.Windows.Forms.WebBrowser> retornam o HTML do documento atual do modo que foi inicialmente exibido.</span><span class="sxs-lookup"><span data-stu-id="2ce68-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="2ce68-104">No entanto, caso modificar a página usando chamadas de método e propriedade como <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> e <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, essas mudanças não aparecerão quando chamar <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> e <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ce68-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="2ce68-105">Para obter a fonte HTML mais atualizada do DOM, é necessário chamar a <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> propriedade no elemento HTML.</span><span class="sxs-lookup"><span data-stu-id="2ce68-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="2ce68-106">O procedimento a seguir mostra como recuperar a fonte dinâmica e exibi-la em um menu de atalho separado.</span><span class="sxs-lookup"><span data-stu-id="2ce68-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="2ce68-107">Recuperação de fonte dinâmica com a propriedade OuterHtml</span><span class="sxs-lookup"><span data-stu-id="2ce68-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1.  <span data-ttu-id="2ce68-108">Criar um novo aplicativo Windows Form.</span><span class="sxs-lookup"><span data-stu-id="2ce68-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="2ce68-109">Iniciar com uma única <xref:System.Windows.Forms.Form>e chamá-lo `Form1`.</span><span class="sxs-lookup"><span data-stu-id="2ce68-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2.  <span data-ttu-id="2ce68-110">Host de <xref:System.Windows.Forms.WebBrowser> controlar em seu aplicativo do Windows Forms e nomeie- `WebBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="2ce68-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="2ce68-111">Para obter mais informações, confira [Como: Adicionar recursos do navegador da Web a um aplicativo do Windows Forms](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="2ce68-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3.  <span data-ttu-id="2ce68-112">Crie um segundo <xref:System.Windows.Forms.Form> em seu aplicativo chamado `CodeForm`.</span><span class="sxs-lookup"><span data-stu-id="2ce68-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4.  <span data-ttu-id="2ce68-113">Adicionar um <xref:System.Windows.Forms.RichTextBox> o controle para `CodeForm` e defina seu <xref:System.Windows.Forms.Control.Dock%2A> propriedade `Fill`.</span><span class="sxs-lookup"><span data-stu-id="2ce68-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5.  <span data-ttu-id="2ce68-114">Crie uma propriedade pública em `CodeForm` chamada `Code`.</span><span class="sxs-lookup"><span data-stu-id="2ce68-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  <span data-ttu-id="2ce68-115">Adicionar um <xref:System.Windows.Forms.Button> controle chamado `Button1` para seu <xref:System.Windows.Forms.Form>e o monitoramento de <xref:System.Windows.Forms.Control.Click> eventos.</span><span class="sxs-lookup"><span data-stu-id="2ce68-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="2ce68-116">Para obter detalhes sobre como monitorar eventos, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="2ce68-116">For details on monitoring events, see [Events](../../../standard/events/index.md).</span></span>  
  
7.  <span data-ttu-id="2ce68-117">Adicione o seguinte código ao manipulador de eventos do <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="2ce68-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2ce68-118">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="2ce68-118">Robust Programming</span></span>  
 <span data-ttu-id="2ce68-119">Sempre teste o valor de <xref:System.Windows.Forms.WebBrowser.Document%2A> antes de tentar recuperá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ce68-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="2ce68-120">Se a página atual não tiver terminado de carregar, o <xref:System.Windows.Forms.WebBrowser.Document%2A> ou um ou mais de seus objetos filhos podem não ser inicializados.</span><span class="sxs-lookup"><span data-stu-id="2ce68-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce68-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ce68-121">See also</span></span>

- [<span data-ttu-id="2ce68-122">Usando o Document Object Model HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="2ce68-122">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
- [<span data-ttu-id="2ce68-123">Visão geral do controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="2ce68-123">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
