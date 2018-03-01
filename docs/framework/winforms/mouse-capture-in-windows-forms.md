---
title: Captura do mouse no Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cc62780579c852aaa637a3ccc13ce2929423868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a>Captura do mouse no Windows Forms
*Captura do mouse* significa quando um controle toma o comando todas as entradas do mouse. Quando um controle tiver capturado o mouse, ele recebe a entrada do mouse com o ponteiro estando ou não dentro de suas bordas.  
  
## <a name="setting-mouse-capture"></a>Configuração da captura do mouse  
 nos Windows Forms, o mouse é capturado pelo controle quando o usuário pressiona um botão do mouse em um controle e o mouse é liberado pelo controle quando o usuário solta o botão do mouse.  
  
 O <xref:System.Windows.Forms.Control.Capture%2A> propriedade o <xref:System.Windows.Forms.Control> classe Especifica se um controle capturou o mouse. Para determinar quando um controle perde a captura do mouse, tratar o <xref:System.Windows.Forms.Control.MouseCaptureChanged> evento.  
  
 Somente a janela em primeiro plano pode capturar o mouse. Quando uma janela de tela de fundo tenta capturar o mouse, a janela recebe mensagens apenas de eventos de mouse que ocorrerem quando o ponteiro do mouse estiver dentro a parte visível da janela. Além disso, mesmo que a janela em primeiro plano tenha capturado o mouse, o usuário ainda poderá clicar em outra janela, colocando-a em primeiro plano. Quando o mouse é capturado, as teclas de atalho não funcionam.  
  
## <a name="see-also"></a>Consulte também  
 [Entrada do mouse em um Aplicativo do Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
