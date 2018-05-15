---
title: Segurança de WebBrowser
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 730d8f692a44a06ea142bb870bbd961d5983c785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="webbrowser-security"></a><span data-ttu-id="7fc95-102">Segurança de WebBrowser</span><span class="sxs-lookup"><span data-stu-id="7fc95-102">WebBrowser Security</span></span>
<span data-ttu-id="7fc95-103">O <xref:System.Windows.Forms.WebBrowser> controle foi projetado para trabalhar na relação de confiança total.</span><span class="sxs-lookup"><span data-stu-id="7fc95-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="7fc95-104">O conteúdo HTML exibido no controle pode vir de servidores Web externos e pode conter código não gerenciado na forma de scripts ou controles da Web.</span><span class="sxs-lookup"><span data-stu-id="7fc95-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="7fc95-105">Se você usar o <xref:System.Windows.Forms.WebBrowser> controle nessa situação, o controle é não menos segura do que o Internet Explorer deve ser, mas o gerenciado <xref:System.Windows.Forms.WebBrowser> controle não impede que esse código não gerenciado em execução.</span><span class="sxs-lookup"><span data-stu-id="7fc95-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="7fc95-106">Para obter mais informações sobre questões de segurança relacionadas a ActiveX subjacente `WebBrowser` , consulte [controle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="7fc95-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](http://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc95-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fc95-107">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="7fc95-108">Visão geral do controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="7fc95-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="7fc95-109">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="7fc95-109">WebBrowser Control</span></span>](http://go.microsoft.com/fwlink/?LinkId=198812)
