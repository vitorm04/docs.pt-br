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
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015823"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Como: Navegar até uma URL com o controle WebBrowser
O exemplo de código a seguir demonstra como navegar <xref:System.Windows.Forms.WebBrowser> o controle para uma URL específica.

 Para determinar quando o novo documento está totalmente carregado, manipule o <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> evento. Para ver uma demonstração desse evento, consulte [como: Imprima com um controle](how-to-print-with-a-webbrowser-control.md)WebBrowser.

## <a name="example"></a>Exemplo

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Compilando o código
 Este exemplo requer:

- Um controle <xref:System.Windows.Forms.WebBrowser> chamado `webBrowser1`.

- Referências aos assemblies `System` e `System.Windows.Forms`.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [Controle WebBrowser](webbrowser-control-windows-forms.md)
- [Como: Imprimir com um controle WebBrowser](how-to-print-with-a-webbrowser-control.md)
