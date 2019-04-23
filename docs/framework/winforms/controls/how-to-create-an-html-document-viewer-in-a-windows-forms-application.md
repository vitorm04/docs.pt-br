---
title: 'Como: Criar um visualizador de documento HTML em um Aplicativo do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 99609e4bf5a352c436986e0773375d1c8e15e790
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340744"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="8a33d-102">Como: Criar um visualizador de documento HTML em um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a33d-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="8a33d-103">Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para exibir e imprimir documentos HTML sem fornecer a funcionalidade completa do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8a33d-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="8a33d-104">Isso é útil quando você quer aproveitar os recursos de formatação de HTML, mas não quer que os usuários carreguem páginas da Web arbitrárias que podem conter controles de Web não confiáveis ou código de script potencialmente mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="8a33d-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="8a33d-105">Você talvez queira restringir a capacidade do <xref:System.Windows.Forms.WebBrowser> controlar dessa maneira, por exemplo, para usá-lo como um visualizador de email HTML ou para fornecer ajuda formatado em HTML em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a33d-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="8a33d-106">Para criar um visualizador de documentos HTML</span><span class="sxs-lookup"><span data-stu-id="8a33d-106">To create an HTML document viewer</span></span>  
  
1. <span data-ttu-id="8a33d-107">Defina as <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> propriedade para `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle abra arquivos soltados nele.</span><span class="sxs-lookup"><span data-stu-id="8a33d-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. <span data-ttu-id="8a33d-108">Defina o <xref:System.Windows.Forms.WebBrowser.Url%2A> propriedade para o local do arquivo inicial a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="8a33d-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a33d-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8a33d-109">Compiling the Code</span></span>  
 <span data-ttu-id="8a33d-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8a33d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8a33d-111">Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="8a33d-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="8a33d-112">Referências aos assemblies `System` e `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="8a33d-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a33d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a33d-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="8a33d-114">Visão geral do controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8a33d-114">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="8a33d-115">Segurança do WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8a33d-115">WebBrowser Security</span></span>](webbrowser-security.md)
- [<span data-ttu-id="8a33d-116">Como: Navegue até uma URL com o controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8a33d-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="8a33d-117">Como: Imprimir com um controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8a33d-117">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
