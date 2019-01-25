---
title: Segurança de WebBrowser
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 4c69f1c39d3a22db361fef1ffb65f21aa9d75128
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736267"
---
# <a name="webbrowser-security"></a><span data-ttu-id="b557f-102">Segurança de WebBrowser</span><span class="sxs-lookup"><span data-stu-id="b557f-102">WebBrowser Security</span></span>
<span data-ttu-id="b557f-103">O <xref:System.Windows.Forms.WebBrowser> controle foi projetado para trabalhar na relação de confiança total.</span><span class="sxs-lookup"><span data-stu-id="b557f-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="b557f-104">O conteúdo HTML exibido no controle pode vir de servidores Web externos e pode conter código não gerenciado na forma de scripts ou controles da Web.</span><span class="sxs-lookup"><span data-stu-id="b557f-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="b557f-105">Se você usar o <xref:System.Windows.Forms.WebBrowser> controle nessa situação, o controle é não menos segura do que o Internet Explorer seria, mas o gerenciado <xref:System.Windows.Forms.WebBrowser> controle não impede que esse código não gerenciado em execução.</span><span class="sxs-lookup"><span data-stu-id="b557f-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="b557f-106">Para obter mais informações sobre problemas de segurança relacionados ao ActiveX subjacente `WebBrowser` de controle, consulte [controle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="b557f-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b557f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b557f-107">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="b557f-108">Visão geral do controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="b557f-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [<span data-ttu-id="b557f-109">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="b557f-109">WebBrowser Control</span></span>](https://go.microsoft.com/fwlink/?LinkId=198812)
