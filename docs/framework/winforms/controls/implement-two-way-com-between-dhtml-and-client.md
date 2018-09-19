---
title: Como implementar a comunicação bidirecional entre o código DHTML e o código do aplicativo cliente
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
ms.openlocfilehash: 10b6bb3f55c8acd62101a48ea53b42e331e4210f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323975"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="9b24c-102">Como implementar a comunicação bidirecional entre o código DHTML e o código do aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="9b24c-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="9b24c-103">Você pode usar o <xref:System.Windows.Forms.WebBrowser> controle para adicionar o código do aplicativo Web do DHTML (HTML) dinâmico existente para seus aplicativos de cliente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9b24c-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="9b24c-104">Isso é útil quando você tiver investido tempo de desenvolvimento significativo na criação de controles com base em DHTML e quiser aproveitar os recursos de interface do usuário avançada dos Windows Forms sem reescrever o código existente.</span><span class="sxs-lookup"><span data-stu-id="9b24c-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="9b24c-105">O <xref:System.Windows.Forms.WebBrowser> controle permite que você implementar a comunicação bidirecional entre o código do aplicativo cliente e o código de script da página da Web por meio de <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> e <xref:System.Windows.Forms.WebBrowser.Document%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="9b24c-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="9b24c-106">Além disso, você pode configurar o <xref:System.Windows.Forms.WebBrowser> controlar de forma que os controles da Web combinem-se perfeitamente com outros controles no formulário de aplicativo, ocultando a implementação do DHTML.</span><span class="sxs-lookup"><span data-stu-id="9b24c-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="9b24c-107">Para mesclar diretamente os controles, formate a página exibida para que a cor de plano de fundo e o estilo visual correspondam ao restante do formulário e usam o <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, e <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> propriedades para desativar recursos do navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="9b24c-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="9b24c-108">Para inserir DHTML em seu aplicativo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b24c-108">To embed DHTML in your Windows Forms application</span></span>  
  
1.  <span data-ttu-id="9b24c-109">Defina a <xref:System.Windows.Forms.WebBrowser> do controle <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> propriedade a ser `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle abra arquivos soltados nele.</span><span class="sxs-lookup"><span data-stu-id="9b24c-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  <span data-ttu-id="9b24c-110">Defina o controle <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> propriedade para `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle de exibir o menu de atalho quando o usuário clica-lo.</span><span class="sxs-lookup"><span data-stu-id="9b24c-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  <span data-ttu-id="9b24c-111">Defina o controle <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> propriedade para `false` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle responda às teclas de atalho.</span><span class="sxs-lookup"><span data-stu-id="9b24c-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  <span data-ttu-id="9b24c-112">Defina as <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> propriedade no construtor do formulário ou um <xref:System.Windows.Forms.Form.Load> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9b24c-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="9b24c-113">O código a seguir usa a classe de formulário em si para o objeto de script.</span><span class="sxs-lookup"><span data-stu-id="9b24c-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b24c-114">O COM (Component Object Model) deve ser capaz de acessar o objeto de script.</span><span class="sxs-lookup"><span data-stu-id="9b24c-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="9b24c-115">Para tornar o formulário visível para COM, adicione o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo à classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="9b24c-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  <span data-ttu-id="9b24c-116">Implemente métodos ou propriedades públicas no código do aplicativo que seu código de script usará.</span><span class="sxs-lookup"><span data-stu-id="9b24c-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="9b24c-117">Por exemplo, se você usar a classe de formulário para o objeto de script, adicione o código a seguir à sua classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="9b24c-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  <span data-ttu-id="9b24c-118">Use o objeto `window.external` no código de script para acessar propriedades públicas e métodos do objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="9b24c-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="9b24c-119">O código HTML a seguir demonstra como chamar um método no objeto de script com um clique de botão.</span><span class="sxs-lookup"><span data-stu-id="9b24c-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="9b24c-120">Copie esse código para o elemento de corpo de um documento HTML que você carregue usando o controle <xref:System.Windows.Forms.WebBrowser.Navigate%2A> método ou que você atribua para o controle <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9b24c-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  <span data-ttu-id="9b24c-121">Implemente funções em seu código de script que seu código do aplicativo usará.</span><span class="sxs-lookup"><span data-stu-id="9b24c-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="9b24c-122">O seguinte elemento SCRIPT HTML apresenta uma função de exemplo.</span><span class="sxs-lookup"><span data-stu-id="9b24c-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="9b24c-123">Copie esse código para o elemento HEAD de um documento HTML que você carregue usando o controle <xref:System.Windows.Forms.WebBrowser.Navigate%2A> método ou que você atribua para o controle <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9b24c-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  <span data-ttu-id="9b24c-124">Use o <xref:System.Windows.Forms.WebBrowser.Document%2A> propriedade para acessar o código de script do seu código de aplicativo do cliente.</span><span class="sxs-lookup"><span data-stu-id="9b24c-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="9b24c-125">Por exemplo, adicione o seguinte código para um botão <xref:System.Windows.Forms.Control.Click> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9b24c-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="9b24c-126">Quando tiver terminado de depurar o DHTML, defina o controle <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> propriedade para `true` para impedir que o <xref:System.Windows.Forms.WebBrowser> controle de exibir mensagens de erro para problemas de código de script.</span><span class="sxs-lookup"><span data-stu-id="9b24c-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="9b24c-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b24c-127">Example</span></span>  
 <span data-ttu-id="9b24c-128">O exemplo de código completo a seguir fornece um aplicativo de demonstração que você pode usar para entender esse recurso.</span><span class="sxs-lookup"><span data-stu-id="9b24c-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="9b24c-129">O código HTML é carregado na <xref:System.Windows.Forms.WebBrowser> controlar por meio de <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> propriedade em vez de que está sendo carregado de um arquivo HTML separado.</span><span class="sxs-lookup"><span data-stu-id="9b24c-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b24c-130">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9b24c-130">Compiling the Code</span></span>  
 <span data-ttu-id="9b24c-131">Esse código requer:</span><span class="sxs-lookup"><span data-stu-id="9b24c-131">This code requires:</span></span>  
  
-   <span data-ttu-id="9b24c-132">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9b24c-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9b24c-133">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9b24c-133">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9b24c-134">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="9b24c-134">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="9b24c-135">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9b24c-135">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b24c-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b24c-136">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9b24c-137">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="9b24c-137">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
