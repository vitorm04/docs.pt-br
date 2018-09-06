---
title: Como adicionar recursos do navegador da Web a um Aplicativo do Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: 514895d11ba5a9c4ac47538f2d1a9c1d0e9d7995
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800429"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="5015d-102">Como adicionar recursos do navegador da Web a um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5015d-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="5015d-103">Com o <xref:System.Windows.Forms.WebBrowser> controle, você pode adicionar a funcionalidade do navegador da Web ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5015d-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="5015d-104">O controle funciona como um navegador da Web por padrão.</span><span class="sxs-lookup"><span data-stu-id="5015d-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="5015d-105">Depois que você carregar uma URL inicial definindo a <xref:System.Windows.Forms.WebBrowser.Url%2A> propriedade, você poderá navegar clicando nos hiperlinks ou usando atalhos de teclado para retroceder e Avançar no histórico de navegação.</span><span class="sxs-lookup"><span data-stu-id="5015d-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="5015d-106">Por padrão, você pode acessar a funcionalidade adicional do navegador por meio do menu de atalho acessado quando se clica com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="5015d-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="5015d-107">Você também pode abrir novos documentos soltando-os no controle.</span><span class="sxs-lookup"><span data-stu-id="5015d-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="5015d-108">O <xref:System.Windows.Forms.WebBrowser> controle também tem várias propriedades, métodos e eventos que você pode usar para implementar recursos de interface do usuário semelhantes àqueles encontrados no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5015d-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="5015d-109">O exemplo de código a seguir implementa uma barra de endereços, botões de navegador típicos, um menu **Arquivo**, uma barra de status e uma barra de título que exibe o título da página atual.</span><span class="sxs-lookup"><span data-stu-id="5015d-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5015d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5015d-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5015d-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5015d-111">Compiling the Code</span></span>  
 <span data-ttu-id="5015d-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5015d-112">This example requires:</span></span>  
  
-   <span data-ttu-id="5015d-113">Referências aos assemblies `System,``System.Drawing` e `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="5015d-113">References to the `System,``System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
 <span data-ttu-id="5015d-114">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5015d-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5015d-115">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="5015d-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="5015d-116">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5015d-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5015d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5015d-117">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="5015d-118">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="5015d-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
