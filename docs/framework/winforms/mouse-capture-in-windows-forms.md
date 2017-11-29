---
title: Captura do mouse no Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a>Captura do mouse no Windows Forms
*Captura do mouse* significa quando um controle toma o comando todas as entradas do mouse. Quando um controle tiver capturado o mouse, ele recebe a entrada do mouse com o ponteiro estando ou não dentro de suas bordas.  
  
## <a name="setting-mouse-capture"></a>Configuração da captura do mouse  
 nos Windows Forms, o mouse é capturado pelo controle quando o usuário pressiona um botão do mouse em um controle e o mouse é liberado pelo controle quando o usuário solta o botão do mouse.  
  
 O <xref:System.Windows.Forms.Control.Capture%2A> propriedade o <xref:System.Windows.Forms.Control> classe Especifica se um controle capturou o mouse. Para determinar quando um controle perde a captura do mouse, tratar o <xref:System.Windows.Forms.Control.MouseCaptureChanged> evento.  
  
 Somente a janela em primeiro plano pode capturar o mouse. Quando uma janela de tela de fundo tenta capturar o mouse, a janela recebe mensagens apenas de eventos de mouse que ocorrerem quando o ponteiro do mouse estiver dentro a parte visível da janela. Além disso, mesmo que a janela em primeiro plano tenha capturado o mouse, o usuário ainda poderá clicar em outra janela, colocando-a em primeiro plano. Quando o mouse é capturado, as teclas de atalho não funcionam.  
  
## <a name="see-also"></a>Consulte também  
 [Entrada do mouse em um aplicativo dos Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
