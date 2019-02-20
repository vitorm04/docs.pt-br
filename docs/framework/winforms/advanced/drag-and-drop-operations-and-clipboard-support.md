---
title: Operações de arrastar e soltar e suporte à área de transferência
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 281d102ecd02623e7e18ebf4fc569538ebbdaf7f
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442003"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a>Operações de arrastar e soltar e suporte à área de transferência
Você pode habilitar operações de arrastar e soltar do usuário dentro de um aplicativo baseado em Windows manipulando uma série de eventos, mais notavelmente os <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> eventos.  
  
 Você também pode implementar o suporte ao usuário recortar/copiar/colar e a transferência de dados do usuário para a área de transferência em seus aplicativos baseados no Windows usando chamadas de método simples.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 Explica como iniciar uma operação do tipo "arrastar e soltar".  
  
 [Como: Executar operações de arrastar e soltar entre aplicativos](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 Ilustra como realizar operações do tipo "arrastar e soltar" entre aplicativos.  
  
 [Como: Adicionar dados à área de transferência](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 Descreve uma maneira de inserir via programação informações na área de transferência.  
  
 [Como: Recuperar dados da área de transferência](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 Descreve como acessar os dados armazenados na área de transferência.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Funcionalidade do tipo "arrastar e soltar" no Windows Forms](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 Descreve os métodos, os eventos e as classes usados para implementar o comportamento do tipo "arrastar e soltar".  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 Descreve a complexidade do evento que pede permissão para continuar a operação de arrastar.  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 Descreve a complexidade do método essencial para começar a operação de arrastar.  
  
 <xref:System.Windows.Forms.Clipboard>  
 Consulte também [como: Enviar dados para o filho MDI ativo](how-to-send-data-to-the-active-mdi-child.md).
