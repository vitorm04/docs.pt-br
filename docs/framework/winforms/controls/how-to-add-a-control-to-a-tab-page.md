---
title: 'Como: Adicionar um controle a uma página da guia'
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
ms.openlocfilehash: 6eb509fd10a5000a5423d624cec5b6d126990d73
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723931"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Como: Adicionar um controle a uma página da guia
Você pode usar os formulários do Windows <xref:System.Windows.Forms.TabControl> para exibir outros controles de forma organizada. O procedimento a seguir mostra como adicionar um botão para a primeira guia. Para obter informações sobre como adicionar um ícone à parte do rótulo de uma página da guia, consulte [como: Alterar a aparência do TabControl dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Para adicionar um controle de forma programática  
  
1.  Use o <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> método de coleção retornada pela <xref:System.Windows.Forms.Control.Controls%2A> propriedade de <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- [Controle TabControl](tabcontrol-control-windows-forms.md)
- [Visão geral do controle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Como: Alterar a aparência do TabControl dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [Como: Desabilitar páginas de guia](how-to-disable-tab-pages.md)
- [Como: Adicionar e remover guias com o TabControl dos Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
