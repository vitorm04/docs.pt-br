---
title: 'Como: Habilitar a tecla TAB mover um controle ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: e1d7917d7e12ba286e7ddf4e95a68769852a17f7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704330"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Como: Habilitar a tecla TAB mover um controle ToolStrip
Use o procedimento a seguir para habilitar o usuário pressione a tecla TAB para mover de um <xref:System.Windows.Forms.ToolStrip> para o próximo controle na ordem de tabulação.  
  
 O <xref:System.Windows.Forms.ToolStrip> aceita o primeiro pressione a tecla TAB e os chaves de seta para selecionar itens dentro de <xref:System.Windows.Forms.ToolStrip>. Quando o usuário pressiona a tecla TAB uma segunda vez, ele leva o usuário para o próximo controle na ordem de tabulação.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Para habilitar o usuário pressione a tecla TAB para mover para fora de uma faixa de ferramentas para o próximo controle  
  
-   Defina as <xref:System.Windows.Forms.ToolStrip.TabStop%2A> propriedade do <xref:System.Windows.Forms.ToolStrip> para `true`.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
