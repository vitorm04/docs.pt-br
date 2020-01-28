---
title: Criar um visualizador de documentos HTML em um aplicativo Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 913bc86af034645b4b8cf3d69da4c9def58fc19c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732837"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Como criar um visualizador de documento HTML em um Aplicativo do Windows Forms
Você pode usar o controle de <xref:System.Windows.Forms.WebBrowser> para exibir e imprimir documentos HTML sem fornecer a funcionalidade completa de um navegador da Web da Internet. Isso é útil quando você quer aproveitar os recursos de formatação de HTML, mas não quer que os usuários carreguem páginas da Web arbitrárias que podem conter controles de Web não confiáveis ou código de script potencialmente mal-intencionado. Talvez você queira restringir a capacidade do controle de <xref:System.Windows.Forms.WebBrowser> dessa maneira, por exemplo, para usá-lo como um visualizador de email HTML ou para fornecer ajuda formatada em HTML em seu aplicativo.  
  
### <a name="to-create-an-html-document-viewer"></a>Para criar um visualizador de documentos HTML  
  
1. Defina a propriedade <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> como `false` para impedir que o controle de <xref:System.Windows.Forms.WebBrowser> Abra arquivos soltos nela.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. Defina a propriedade <xref:System.Windows.Forms.WebBrowser.Url%2A> como o local do arquivo inicial a ser exibido.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.  
  
- Referências aos assemblies `System` e `System.Windows.Forms`.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [Visão geral do controle WebBrowser](webbrowser-control-overview.md)
- [Segurança do WebBrowser](webbrowser-security.md)
- [Como navegar até uma URL com o controle WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Como imprimir com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md)
