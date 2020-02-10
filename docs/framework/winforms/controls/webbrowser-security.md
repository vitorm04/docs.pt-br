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
# <a name="webbrowser-security"></a><span data-ttu-id="0c225-102">Segurança de WebBrowser</span><span class="sxs-lookup"><span data-stu-id="0c225-102">WebBrowser Security</span></span>
<span data-ttu-id="0c225-103">O controle <xref:System.Windows.Forms.WebBrowser> é projetado para funcionar somente com confiança total.</span><span class="sxs-lookup"><span data-stu-id="0c225-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="0c225-104">O conteúdo HTML exibido no controle pode vir de servidores Web externos e pode conter código não gerenciado na forma de scripts ou controles da Web.</span><span class="sxs-lookup"><span data-stu-id="0c225-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="0c225-105">Se você usar o controle de <xref:System.Windows.Forms.WebBrowser> nessa situação, o controle não será menos seguro do que o Internet Explorer seria, mas o controle de <xref:System.Windows.Forms.WebBrowser> gerenciado não impedirá a execução desse código não-gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0c225-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="0c225-106">Para obter mais informações sobre problemas de segurança relacionados ao controle de `WebBrowser` ActiveX subjacente, consulte [controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0c225-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c225-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c225-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="0c225-108">Visão geral do controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="0c225-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- <span data-ttu-id="0c225-109">[Controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0c225-109">[WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span></span>
