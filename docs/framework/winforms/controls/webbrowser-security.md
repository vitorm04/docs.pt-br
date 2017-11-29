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
ms.openlocfilehash: a0d84f0c70619324bbbd38a2961914f88ac42671
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="webbrowser-security"></a>Segurança de WebBrowser
O <xref:System.Windows.Forms.WebBrowser> controle foi projetado para trabalhar na relação de confiança total. O conteúdo HTML exibido no controle pode vir de servidores Web externos e pode conter código não gerenciado na forma de scripts ou controles da Web. Se você usar o <xref:System.Windows.Forms.WebBrowser> controle nessa situação, o controle é não menos segura do que o Internet Explorer deve ser, mas o gerenciado <xref:System.Windows.Forms.WebBrowser> controle não impede que esse código não gerenciado em execução.  
  
 Para obter mais informações sobre questões de segurança relacionadas a ActiveX subjacente `WebBrowser` , consulte [controle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=198812).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.WebBrowser>  
 [Visão geral do controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [Controle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=198812)
