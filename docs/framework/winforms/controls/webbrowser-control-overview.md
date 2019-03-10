---
title: Visão geral do controle WebBrowser
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: cc998fd88f3487aa20f6cef73aacb6c07f92c7ad
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710089"
---
# <a name="webbrowser-control-overview"></a>Visão geral do controle WebBrowser
O <xref:System.Windows.Forms.WebBrowser> controle fornece um wrapper gerenciado para o controle WebBrowser ActiveX. O wrapper gerenciado permite exibir páginas da Web em seus aplicativos cliente dos Windows Forms. Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para duplicar a funcionalidade de navegação da Web Internet Explorer em seu aplicativo, ou você pode desabilitar a funcionalidade padrão do Internet Explorer e usar o controle como um visualizador de documentos HTML simple. Você também pode usar o controle para adicionar elementos da interface do usuário com base em DHTML ao seu formulário e ocultar o fato de que eles são hospedados no <xref:System.Windows.Forms.WebBrowser> controle. Essa abordagem permite combinar perfeitamente controles Web com controles dos Windows Forms em um único aplicativo.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Propriedades, métodos e eventos usados com frequência  
 O <xref:System.Windows.Forms.WebBrowser> controle tem várias propriedades, métodos e eventos que você pode usar para implementar controles encontrados no Internet Explorer. Por exemplo, você pode usar o método `Navigate` para implementar uma barra de endereços e os métodos `GoBack`, `GoForward`, `Stop` e `Refresh` para implementar os botões de navegação em uma barra de ferramentas. Você pode manipular o evento `Navigated` para atualizar a barra de endereços com o valor da propriedade `Url` e a barra de título com o valor da propriedade `DocumentTitle`.  
  
 Se você quiser gerar seu próprio conteúdo de página dentro de seu aplicativo, defina a propriedade `DocumentText`. Se você estiver familiarizado com o DOM (Modelo de Objeto do Documento) HTML, também poderá manipular o conteúdo da página da Web por meio da propriedade `Document`. Com essa propriedade, você pode armazenar e modificar documentos na memória, em vez de navegar entre arquivos.  
  
 A propriedade `Document` também permite que você chame os métodos implementados no código de script da página da Web do seu código de aplicativo cliente. Para acessar o código do aplicativo cliente do seu código de script, defina a propriedade `ObjectForScripting`. O objeto especificado pode ser acessado pelo seu código de script como o objeto `window.external`.  
  
|Nome|Descrição|  
|----------|-----------------|  
|Propriedade <xref:System.Windows.Forms.WebBrowser.Document%2A>|Obtém um objeto que fornece acesso gerenciado para DOM (Modelo de Objeto do Documento) HTML da página da Web atual.|  
|Evento <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>|Ocorre quando uma página da Web conclui o carregamento.|  
|Propriedade <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>|Obtém ou define o conteúdo HTML da página da Web atual.|  
|Propriedade <xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>|Obtém o título da página da Web atual.|  
|Método <xref:System.Windows.Forms.WebBrowser.GoBack%2A>|Navega para a página anterior no histórico.|  
|Método <xref:System.Windows.Forms.WebBrowser.GoForward%2A>|Navega para a próxima página no histórico.|  
|Método <xref:System.Windows.Forms.WebBrowser.Navigate%2A>|Navega para a URL especificada.|  
|Evento <xref:System.Windows.Forms.WebBrowser.Navigating>|Ocorre antes do início de navegação, permitindo que a ação seja cancelada.|  
|Propriedade <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>|Obtém ou define um objeto que o código de script da página da Web pode usar para se comunicar com o aplicativo.|  
|Método <xref:System.Windows.Forms.WebBrowser.Print%2A>|Imprime a página da Web atual.|  
|Método <xref:System.Windows.Forms.WebBrowser.Refresh%2A>|Recarrega a página da Web atual.|  
|Método <xref:System.Windows.Forms.WebBrowser.Stop%2A>|Interrompe a navegação atual e para elementos de página dinâmicos, como sons e animação.|  
|Propriedade <xref:System.Windows.Forms.WebBrowser.Url%2A>|Obtém ou define a URL da página da Web atual. Configurar essa propriedade leva o controle para a nova URL.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [Como: Navegue até uma URL com o controle WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Como: Imprimir com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md)
- [Como: Adicionar recursos do navegador da Web a um aplicativo do Windows Forms](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Como: Criar um visualizador de documento HTML em um aplicativo do Windows Forms](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Como: Implementar a comunicação bidirecional entre o código DHTML e o código do aplicativo cliente](implement-two-way-com-between-dhtml-and-client.md)
- [Segurança do WebBrowser](webbrowser-security.md)
