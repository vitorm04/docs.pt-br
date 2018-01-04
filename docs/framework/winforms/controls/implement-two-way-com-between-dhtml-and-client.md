---
title: "Como implementar a comunicação bidirecional entre o código DHTML e o código do aplicativo cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63291cddc294b6ad8003636d6d79169f2d0852e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Como implementar a comunicação bidirecional entre o código DHTML e o código do aplicativo cliente
Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para adicionar o código existente do aplicativo Web DHTML (HTML) dinâmico para seus aplicativos de cliente de formulários do Windows. Isso é útil quando você tiver investido tempo de desenvolvimento significativo na criação de controles com base em DHTML e quiser aproveitar os recursos de interface do usuário avançada dos Windows Forms sem reescrever o código existente.  
  
 O <xref:System.Windows.Forms.WebBrowser> controle permite que você implementar a comunicação bidirecional entre o código do aplicativo cliente e o código de script de página da Web por meio de <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> e <xref:System.Windows.Forms.WebBrowser.Document%2A> propriedades. Além disso, você pode configurar o <xref:System.Windows.Forms.WebBrowser> controlar de forma que os controles da Web do blend perfeitamente com outros controles do formulário de aplicativo, ocultando sua implementação DHTML. Para mesclar diretamente os controles, formatar a página exibida para que sua cor de plano de fundo e estilo visual coincidir com o restante do formulário e usam o <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, e <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> propriedades para desabilitar os recursos do navegador padrão.  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Para inserir DHTML em seu aplicativo dos Windows Forms  
  
1.  Definir o <xref:System.Windows.Forms.WebBrowser> do controle <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> propriedade `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle de abrir arquivos solto nele.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  Definir o controle <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> propriedade `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle de exibir o menu de atalho quando o usuário clica-lo.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  Definir o controle <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> propriedade `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle de responder às teclas de atalho.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  Definir o <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> propriedade no construtor do formulário ou uma <xref:System.Windows.Forms.Form.Load> manipulador de eventos.  
  
     O código a seguir usa a classe de formulário em si para o objeto de script.  
  
    > [!NOTE]
    >  O COM (Component Object Model) deve ser capaz de acessar o objeto de script. Para tornar o formulário visíveis no COM, adicione o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo à sua classe de formulário.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  Implemente métodos ou propriedades públicas no código do aplicativo que seu código de script usará.  
  
     Por exemplo, se você usar a classe de formulário para o objeto de script, adicione o código a seguir à sua classe de formulário.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  Use o objeto `window.external` no código de script para acessar propriedades públicas e métodos do objeto especificado.  
  
     O código HTML a seguir demonstra como chamar um método no objeto de script com um clique de botão. Copie este código no elemento BODY de um documento HTML que você carregar usando o controle <xref:System.Windows.Forms.WebBrowser.Navigate%2A> método ou que você atribua o controle <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> propriedade.  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  Implemente funções em seu código de script que seu código do aplicativo usará.  
  
     O seguinte elemento SCRIPT HTML apresenta uma função de exemplo. Copie este código para o elemento de cabeçalho de um documento HTML que você carregar usando o controle <xref:System.Windows.Forms.WebBrowser.Navigate%2A> método ou que você atribua o controle <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> propriedade.  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  Use o <xref:System.Windows.Forms.WebBrowser.Document%2A> propriedade para acessar o código de script do seu código do aplicativo cliente.  
  
     Por exemplo, adicione o seguinte código para um botão <xref:System.Windows.Forms.Control.Click> manipulador de eventos.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. Quando tiver terminado de depurar seu DHTML, definir o controle <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> propriedade `true` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle de exibição de mensagens de erro para problemas de código de script.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo a seguir fornece um aplicativo de demonstração que você pode usar para entender esse recurso. O código HTML é carregado no <xref:System.Windows.Forms.WebBrowser> controlar por meio de <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> propriedade em vez de sendo carregado a partir de um arquivo HTML separado.  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esse código requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [Controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
