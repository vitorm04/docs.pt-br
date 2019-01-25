---
title: 'Como: Criar um visualizador de documento HTML em um aplicativo do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 83a29af28f5e58b75377805e443eb92cee39e272
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643696"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="af666-102">Como: Criar um visualizador de documento HTML em um aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="af666-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="af666-103">Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para exibir e imprimir documentos HTML sem fornecer a funcionalidade completa do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="af666-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="af666-104">Isso é útil quando você quer aproveitar os recursos de formatação de HTML, mas não quer que os usuários carreguem páginas da Web arbitrárias que podem conter controles de Web não confiáveis ou código de script potencialmente mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="af666-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="af666-105">Você talvez queira restringir a capacidade do <xref:System.Windows.Forms.WebBrowser> controlar dessa maneira, por exemplo, para usá-lo como um visualizador de email HTML ou para fornecer ajuda formatado em HTML em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af666-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="af666-106">Para criar um visualizador de documentos HTML</span><span class="sxs-lookup"><span data-stu-id="af666-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="af666-107">Defina as <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> propriedade para `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle abra arquivos soltados nele.</span><span class="sxs-lookup"><span data-stu-id="af666-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="af666-108">Defina o <xref:System.Windows.Forms.WebBrowser.Url%2A> propriedade para o local do arquivo inicial a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="af666-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af666-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="af666-109">Compiling the Code</span></span>  
 <span data-ttu-id="af666-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="af666-110">This example requires:</span></span>  
  
-   <span data-ttu-id="af666-111">Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="af666-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="af666-112">Referências aos assemblies `System` e `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="af666-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af666-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af666-113">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="af666-114">Visão geral do controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="af666-114">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [<span data-ttu-id="af666-115">Segurança do WebBrowser</span><span class="sxs-lookup"><span data-stu-id="af666-115">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)
- [<span data-ttu-id="af666-116">Como: Navegue até uma URL com o controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="af666-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="af666-117">Como: Imprimir com um controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="af666-117">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
