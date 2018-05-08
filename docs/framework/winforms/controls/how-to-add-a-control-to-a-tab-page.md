---
title: Como adicionar um controle a uma página da guia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 1bb2233cf9e288ae89ebb8cab3df4f6451dc8eed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Como adicionar um controle a uma página da guia
Você pode usar o Windows Forms <xref:System.Windows.Forms.TabControl> para exibir outros controles de forma organizada. O procedimento a seguir mostra como adicionar um botão à guia primeiro. Para obter informações sobre como adicionar um ícone à parte do rótulo de uma página da guia, veja [Como alterar a aparência do TabControl dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Para adicionar um controle programaticamente  
  
1.  Use o <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> método da coleção retornada pelo <xref:System.Windows.Forms.Control.Controls%2A> propriedade <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Controle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [Visão geral do controle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Como alterar a aparência do TabControl dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [Como desabilitar páginas de guia](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Como adicionar e remover guias com o TabControl dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
