---
title: 'Como: Navegar até uma URL com o controle WebBrowser'
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
ms.openlocfilehash: a174b6ae60f87e91e6f97e8fa7f8ad3892ef017a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132932"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Como: Navegar até uma URL com o controle WebBrowser
O exemplo de código a seguir demonstra como navegar o <xref:System.Windows.Forms.WebBrowser> controle a uma URL específica.  
  
 Para determinar quando o novo documento está totalmente carregado, lidar com o <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> eventos. Para ver uma demonstração desse evento, consulte [como: Impressão com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md).  
  
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

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [Controle WebBrowser](webbrowser-control-windows-forms.md)
- [Como: Imprimir com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md)
