---
title: 'Como: Adicionar recursos do navegador da Web a um Aplicativo do Windows Forms'
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
ms.openlocfilehash: 60b544c630fc5c7c876293b27a5c5e159e57a797
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588885"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="d122a-102">Como: Adicionar recursos do navegador da Web a um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d122a-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="d122a-103">Com o <xref:System.Windows.Forms.WebBrowser> controle, você pode adicionar a funcionalidade do navegador da Web ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d122a-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="d122a-104">O controle funciona como um navegador da Web por padrão.</span><span class="sxs-lookup"><span data-stu-id="d122a-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="d122a-105">Depois que você carregar uma URL inicial definindo a <xref:System.Windows.Forms.WebBrowser.Url%2A> propriedade, você poderá navegar clicando nos hiperlinks ou usando atalhos de teclado para retroceder e Avançar no histórico de navegação.</span><span class="sxs-lookup"><span data-stu-id="d122a-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="d122a-106">Por padrão, você pode acessar a funcionalidade adicional do navegador por meio do menu de atalho acessado quando se clica com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="d122a-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="d122a-107">Você também pode abrir novos documentos soltando-os no controle.</span><span class="sxs-lookup"><span data-stu-id="d122a-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="d122a-108">O <xref:System.Windows.Forms.WebBrowser> controle também tem várias propriedades, métodos e eventos que você pode usar para implementar recursos de interface do usuário semelhantes àqueles encontrados no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d122a-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="d122a-109">O exemplo de código a seguir implementa uma barra de endereços, botões de navegador típicos, um menu **Arquivo**, uma barra de status e uma barra de título que exibe o título da página atual.</span><span class="sxs-lookup"><span data-stu-id="d122a-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d122a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d122a-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d122a-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d122a-111">Compiling the Code</span></span>  
 <span data-ttu-id="d122a-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d122a-112">This example requires:</span></span>  
  
- <span data-ttu-id="d122a-113">Referências para o `System`, `System.Drawing`, e `System.Windows.Forms` assemblies.</span><span class="sxs-lookup"><span data-stu-id="d122a-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d122a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d122a-114">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="d122a-115">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="d122a-115">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
