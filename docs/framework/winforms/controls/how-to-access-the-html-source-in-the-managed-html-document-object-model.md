---
title: 'Como: Acessar a fonte HTML no modelo de objeto do documento HTML gerenciado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: 310af03adf38339dd13a5095546391d4bfecac05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674944"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Como: Acessar a fonte HTML no modelo de objeto do documento HTML gerenciado
As propriedades <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> e <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> no controle <xref:System.Windows.Forms.WebBrowser> retornam o HTML do documento atual do modo que foi inicialmente exibido. No entanto, caso modificar a página usando chamadas de método e propriedade como <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> e <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, essas mudanças não aparecerão quando chamar <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> e <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. Para obter a fonte HTML mais atualizada do DOM, é necessário chamar a <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> propriedade no elemento HTML.  
  
 O procedimento a seguir mostra como recuperar a fonte dinâmica e exibi-la em um menu de atalho separado.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Recuperação de fonte dinâmica com a propriedade OuterHtml  
  
1.  Criar um novo aplicativo Windows Form. Iniciar com uma única <xref:System.Windows.Forms.Form>e chamá-lo `Form1`.  
  
2.  Host de <xref:System.Windows.Forms.WebBrowser> controlar em seu aplicativo do Windows Forms e nomeie- `WebBrowser1`. Para obter mais informações, confira [Como: Adicionar recursos do navegador da Web a um aplicativo do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  Crie um segundo <xref:System.Windows.Forms.Form> em seu aplicativo chamado `CodeForm`.  
  
4.  Adicionar um <xref:System.Windows.Forms.RichTextBox> o controle para `CodeForm` e defina seu <xref:System.Windows.Forms.Control.Dock%2A> propriedade `Fill`.  
  
5.  Crie uma propriedade pública em `CodeForm` chamada `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Adicionar um <xref:System.Windows.Forms.Button> controle chamado `Button1` para seu <xref:System.Windows.Forms.Form>e o monitoramento de <xref:System.Windows.Forms.Control.Click> eventos. Para obter detalhes sobre como monitorar eventos, consulte [Eventos](../../../../docs/standard/events/index.md).  
  
7.  Adicione o seguinte código ao manipulador de eventos do <xref:System.Windows.Forms.Control.Click>.  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Sempre teste o valor de <xref:System.Windows.Forms.WebBrowser.Document%2A> antes de tentar recuperá-lo. Se a página atual não tiver terminado de carregar, o <xref:System.Windows.Forms.WebBrowser.Document%2A> ou um ou mais de seus objetos filhos podem não ser inicializados.  
  
## <a name="see-also"></a>Consulte também
- [Usando o Modelo de Objeto do Documento HTML gerenciado](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
- [Visão geral do controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
