---
title: 'Como: Navegue até uma URL com o controle WebBrowser'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: 8d592aea972a95a582cc35ecb14227edec5860ce
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707229"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="8e31c-102">Como: Navegue até uma URL com o controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8e31c-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="8e31c-103">O exemplo de código a seguir demonstra como navegar o <xref:System.Windows.Forms.WebBrowser> controle a uma URL específica.</span><span class="sxs-lookup"><span data-stu-id="8e31c-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="8e31c-104">Para determinar quando o novo documento está totalmente carregado, lidar com o <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> eventos.</span><span class="sxs-lookup"><span data-stu-id="8e31c-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="8e31c-105">Para ver uma demonstração desse evento, consulte [como: Impressão com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="8e31c-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e31c-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e31c-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e31c-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8e31c-107">Compiling the Code</span></span>  
 <span data-ttu-id="8e31c-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8e31c-108">This example requires:</span></span>  
  
-   <span data-ttu-id="8e31c-109">Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="8e31c-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="8e31c-110">Referências aos assemblies `System` e `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="8e31c-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e31c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e31c-111">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="8e31c-112">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8e31c-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="8e31c-113">Como: Imprimir com um controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8e31c-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
