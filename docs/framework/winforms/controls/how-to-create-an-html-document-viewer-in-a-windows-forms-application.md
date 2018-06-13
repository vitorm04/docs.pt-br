---
title: Como criar um visualizador de documento HTML em um Aplicativo do Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 1330e20cc4fe7df86e51bebca28e4a71e3108673
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530537"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Como criar um visualizador de documento HTML em um Aplicativo do Windows Forms
Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para exibir e imprimir documentos HTML sem fornecer a funcionalidade completa do Internet Explorer. Isso é útil quando você quer aproveitar os recursos de formatação de HTML, mas não quer que os usuários carreguem páginas da Web arbitrárias que podem conter controles de Web não confiáveis ou código de script potencialmente mal-intencionado. Talvez você queira restringir a capacidade do <xref:System.Windows.Forms.WebBrowser> controlar dessa maneira, por exemplo, para usá-lo como um visualizador de email HTML ou para fornecer ajuda formatado em HTML em seu aplicativo.  
  
### <a name="to-create-an-html-document-viewer"></a>Para criar um visualizador de documentos HTML  
  
1.  Definir o <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> propriedade `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle de abrir arquivos solto nele.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Definir o <xref:System.Windows.Forms.WebBrowser.Url%2A> propriedade para o local do arquivo inicial para exibir.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.  
  
-   Referências aos assemblies `System` e `System.Windows.Forms`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [Visão geral do controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [Segurança do WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [Como navegar até uma URL com o controle WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Como imprimir com um controle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
