---
title: "Segurança de WebBrowser"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3985fc9916b3e95e650502ef1f8dc301363b1f90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="webbrowser-security"></a>Segurança de WebBrowser
O <xref:System.Windows.Forms.WebBrowser> controle foi projetado para trabalhar na relação de confiança total. O conteúdo HTML exibido no controle pode vir de servidores Web externos e pode conter código não gerenciado na forma de scripts ou controles da Web. Se você usar o <xref:System.Windows.Forms.WebBrowser> controle nessa situação, o controle é não menos segura do que o Internet Explorer deve ser, mas o gerenciado <xref:System.Windows.Forms.WebBrowser> controle não impede que esse código não gerenciado em execução.  
  
 Para obter mais informações sobre questões de segurança relacionadas a ActiveX subjacente `WebBrowser` , consulte [controle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=198812).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.WebBrowser>  
 [Visão geral do controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [Controle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=198812)
