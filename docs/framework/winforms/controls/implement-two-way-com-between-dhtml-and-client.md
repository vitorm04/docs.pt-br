---
title: 'Como: Implementar a comunicação bidirecional entre o código DHTML e o código do aplicativo cliente'
ms.date: 03/30/2017
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
ms.openlocfilehash: 26cbc995a749c4c129729be700dee588d1033a05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953430"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Como: Implementar a comunicação bidirecional entre o código DHTML e o código do aplicativo cliente

Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para adicionar o código do aplicativo Web HTML dinâmico (DHTML) existente à sua Windows Forms aplicativos cliente. Isso é útil quando você tiver investido tempo de desenvolvimento significativo na criação de controles com base em DHTML e quiser aproveitar os recursos de interface do usuário avançada dos Windows Forms sem reescrever o código existente.

O <xref:System.Windows.Forms.WebBrowser> controle permite que você implemente a comunicação bidirecional entre o código do aplicativo cliente e o código de script da página <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> da <xref:System.Windows.Forms.WebBrowser.Document%2A> Web por meio das propriedades e. Além disso, você pode configurar <xref:System.Windows.Forms.WebBrowser> o controle para que os controles da Web se misturem diretamente com outros controles em seu formulário de aplicativo, ocultando sua implementação DHTML. Para misturar os controles diretamente, formate a página exibida para que sua cor e estilo visual do plano de fundo correspondam ao restante do formulário <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>e <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>use as <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> Propriedades, e para desabilitar os recursos padrão do navegador.

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Para inserir DHTML em seu aplicativo dos Windows Forms

1. Defina a <xref:System.Windows.Forms.WebBrowser> Propriedade do <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> controle como `false` para impedir que <xref:System.Windows.Forms.WebBrowser> o controle Abra arquivos soltos nele.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. Defina a propriedade do <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> controle como `false` para impedir que <xref:System.Windows.Forms.WebBrowser> o controle exiba o menu de atalho quando o usuário clicar com o botão direito do mouse nele.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. Defina a propriedade do <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> controle como `false` para impedir que <xref:System.Windows.Forms.WebBrowser> o controle responda às teclas de atalho.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. Defina a <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> Propriedade no construtor do formulário ou em um <xref:System.Windows.Forms.Form.Load> manipulador de eventos.

     O código a seguir usa a classe de formulário em si para o objeto de script.

    > [!NOTE]
    > O COM (Component Object Model) deve ser capaz de acessar o objeto de script. Para tornar seu formulário visível para com, adicione o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo à sua classe de formulário.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. Implemente métodos ou propriedades públicas no código do aplicativo que seu código de script usará.

     Por exemplo, se você usar a classe de formulário para o objeto de script, adicione o código a seguir à sua classe de formulário.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. Use o objeto `window.external` no código de script para acessar propriedades públicas e métodos do objeto especificado.

     O código HTML a seguir demonstra como chamar um método no objeto de script com um clique de botão. Copie esse código no elemento body de um documento HTML que você carrega usando o método do <xref:System.Windows.Forms.WebBrowser.Navigate%2A> controle ou que você atribui à propriedade do <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> controle.

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. Implemente funções em seu código de script que seu código do aplicativo usará.

     O seguinte elemento SCRIPT HTML apresenta uma função de exemplo. Copie esse código no elemento de cabeçalho de um documento HTML que você carrega usando o método do <xref:System.Windows.Forms.WebBrowser.Navigate%2A> controle ou que você atribui à propriedade do <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> controle.

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. Use a <xref:System.Windows.Forms.WebBrowser.Document%2A> propriedade para acessar o código de script do código do aplicativo cliente.

     Por exemplo, adicione o código a seguir a um <xref:System.Windows.Forms.Control.Click> manipulador de eventos de botão.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. Quando você terminar de depurar seu DHTML, defina a propriedade do <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> controle como `true` para impedir que <xref:System.Windows.Forms.WebBrowser> o controle exiba mensagens de erro para problemas de código de script.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a>Exemplo

O exemplo de código completo a seguir fornece um aplicativo de demonstração que você pode usar para entender esse recurso. O código HTML é carregado no <xref:System.Windows.Forms.WebBrowser> controle por meio da <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> Propriedade em vez de ser carregado de um arquivo HTML separado.

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a>Compilando o código

Esse código requer:

- Referências aos assemblies Sistema e System.Windows.Forms.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [Controle WebBrowser](webbrowser-control-windows-forms.md)
