---
title: Captura do mouse no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: ca16d2fa2339f8d9110bb748a687f90e093598fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690315"
---
# <a name="mouse-capture-in-windows-forms"></a>Captura do mouse no Windows Forms
*Captura do mouse* significa quando um controle toma o comando todas as entradas do mouse. Quando um controle tiver capturado o mouse, ele recebe a entrada do mouse com o ponteiro estando ou não dentro de suas bordas.  
  
## <a name="setting-mouse-capture"></a>Configuração da captura do mouse  
 nos Windows Forms, o mouse é capturado pelo controle quando o usuário pressiona um botão do mouse em um controle e o mouse é liberado pelo controle quando o usuário solta o botão do mouse.  
  
 O <xref:System.Windows.Forms.Control.Capture%2A> propriedade do <xref:System.Windows.Forms.Control> classe Especifica se um controle capturou o mouse. Para determinar quando um controle perde a captura do mouse, manipule o <xref:System.Windows.Forms.Control.MouseCaptureChanged> eventos.  
  
 Somente a janela em primeiro plano pode capturar o mouse. Quando uma janela de tela de fundo tenta capturar o mouse, a janela recebe mensagens apenas de eventos de mouse que ocorrerem quando o ponteiro do mouse estiver dentro a parte visível da janela. Além disso, mesmo que a janela em primeiro plano tenha capturado o mouse, o usuário ainda poderá clicar em outra janela, colocando-a em primeiro plano. Quando o mouse é capturado, as teclas de atalho não funcionam.  
  
## <a name="see-also"></a>Consulte também
- [Entrada do mouse em um Aplicativo do Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
