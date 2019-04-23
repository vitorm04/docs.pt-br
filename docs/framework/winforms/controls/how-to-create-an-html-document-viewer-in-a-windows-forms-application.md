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
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Como: Criar um visualizador de documento HTML em um Aplicativo do Windows Forms
Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para exibir e imprimir documentos HTML sem fornecer a funcionalidade completa do Internet Explorer. Isso é útil quando você quer aproveitar os recursos de formatação de HTML, mas não quer que os usuários carreguem páginas da Web arbitrárias que podem conter controles de Web não confiáveis ou código de script potencialmente mal-intencionado. Você talvez queira restringir a capacidade do <xref:System.Windows.Forms.WebBrowser> controlar dessa maneira, por exemplo, para usá-lo como um visualizador de email HTML ou para fornecer ajuda formatado em HTML em seu aplicativo.  
  
### <a name="to-create-an-html-document-viewer"></a>Para criar um visualizador de documentos HTML  
  
1. Defina as <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> propriedade para `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle abra arquivos soltados nele.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. Defina o <xref:System.Windows.Forms.WebBrowser.Url%2A> propriedade para o local do arquivo inicial a ser exibida.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.  
  
-   Referências aos assemblies `System` e `System.Windows.Forms`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [Visão geral do controle WebBrowser](webbrowser-control-overview.md)
- [Segurança do WebBrowser](webbrowser-security.md)
- [Como: Navegue até uma URL com o controle WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Como: Imprimir com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md)
