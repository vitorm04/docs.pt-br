---
title: Como navegar até uma URL com o controle WebBrowser
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
ms.openlocfilehash: f34577d45ddfbd2445fd4558c5694facf3f1aa29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Como navegar até uma URL com o controle WebBrowser
O exemplo de código a seguir demonstra como navegar a <xref:System.Windows.Forms.WebBrowser> controle a uma URL específica.  
  
 Para determinar quando o novo documento está totalmente carregado, tratar o <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> evento. Para ver uma demonstração desse evento, consulte [como: imprimir com um controle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).  
  
## <a name="example"></a>Exemplo  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.  
  
-   Referências aos assemblies `System` e `System.Windows.Forms`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [Controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [Como imprimir com um controle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
