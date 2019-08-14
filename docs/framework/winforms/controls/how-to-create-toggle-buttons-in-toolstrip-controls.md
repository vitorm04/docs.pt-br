---
title: 'Como: Criar botões de alternância em controles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972363"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Como: Criar botões de alternância em controles ToolStrip

Quando um usuário clica em um botão de alternância, ele aparece em baixo e mantém a aparência de baixo-relevo até que o usuário clique no botão novamente.

## <a name="to-create-a-toggling-toolstripbutton"></a>Para criar uma alternância de ToolStripButton

- Use um código como o exemplo de código a seguir. Esse código pressupõe que seu formulário contém um <xref:System.Windows.Forms.ToolStrip> controle e que sua <xref:System.Windows.Forms.ToolStrip.Items%2A> coleção contém um <xref:System.Windows.Forms.ToolStripButton> chamado `toolStripButton1`. Ele também pressupõe que você tenha um manipulador de eventos `toolStripButton1_CheckedChanged`chamado.

    ```vb
    toolStripButton1.CheckOnClick = True
    toolStripButton1.CheckedChanged AddressOf _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

    ```csharp
    toolStripButton1.CheckOnClick = true;
    toolStripButton1.CheckedChanged += new _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStripButton>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
