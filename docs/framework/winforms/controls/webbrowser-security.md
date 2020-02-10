---
title: Segurança de WebBrowser
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: b25cabca050d06dbfe97c563eb56622d1f21be54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095249"
---
# <a name="webbrowser-security"></a>Segurança de WebBrowser
O controle <xref:System.Windows.Forms.WebBrowser> é projetado para funcionar somente com confiança total. O conteúdo HTML exibido no controle pode vir de servidores Web externos e pode conter código não gerenciado na forma de scripts ou controles da Web. Se você usar o controle de <xref:System.Windows.Forms.WebBrowser> nessa situação, o controle não será menos seguro do que o Internet Explorer seria, mas o controle de <xref:System.Windows.Forms.WebBrowser> gerenciado não impedirá a execução desse código não-gerenciado.  
  
 Para obter mais informações sobre problemas de segurança relacionados ao controle de `WebBrowser` ActiveX subjacente, consulte [controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.WebBrowser>
- [Visão geral do controle WebBrowser](webbrowser-control-overview.md)
- [Controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))
