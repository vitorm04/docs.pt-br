---
title: Como selecionar um item no controle ListView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 8256eaeddf98c5a0dd80357bcd562e8f66db85b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532815"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Como selecionar um item no controle ListView dos Windows Forms
Este exemplo demonstra como programaticamente selecionar um item em um Windows Forms <xref:System.Windows.Forms.ListView> controle. Selecionando um item por meio de programação não altera automaticamente o foco para o <xref:System.Windows.Forms.ListView> controle. Por esse motivo, você normalmente também desejará definir o item como foco quando a seleção de um item.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.ListView> controle chamado `listView1` que contém pelo menos um item.  
  
-   Referências aos namespaces <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
