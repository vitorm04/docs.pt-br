---
title: Segurança de WebBrowser
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 957c11a085c971a81e5baa81a5b797dd53f2451a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703420"
---
# <a name="webbrowser-security"></a>Segurança de WebBrowser
O <xref:System.Windows.Forms.WebBrowser> controle foi projetado para trabalhar na relação de confiança total. O conteúdo HTML exibido no controle pode vir de servidores Web externos e pode conter código não gerenciado na forma de scripts ou controles da Web. Se você usar o <xref:System.Windows.Forms.WebBrowser> controle nessa situação, o controle é não menos segura do que o Internet Explorer seria, mas o gerenciado <xref:System.Windows.Forms.WebBrowser> controle não impede que esse código não gerenciado em execução.  
  
 Para obter mais informações sobre problemas de segurança relacionados ao ActiveX subjacente `WebBrowser` de controle, consulte [controle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=198812).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.WebBrowser>
- [Visão geral do controle WebBrowser](webbrowser-control-overview.md)
- [Controle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=198812)
