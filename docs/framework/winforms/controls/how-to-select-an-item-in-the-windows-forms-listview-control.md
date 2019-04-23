---
title: 'Como: Selecionar um item no controle ListView do Windows Forms'
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
ms.openlocfilehash: b3cfcc6c2873dfb0eb95cf7950adc6b2bb73e74c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977607"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Como: Selecionar um item no controle ListView do Windows Forms
Este exemplo demonstra como selecionar programaticamente um item em um Windows Forms <xref:System.Windows.Forms.ListView> controle. Selecionar um item por meio de programação não altera automaticamente o foco para o <xref:System.Windows.Forms.ListView> controle. Por esse motivo, você normalmente também desejará definir o item focados ao selecionar um item.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.ListView> controle chamado `listView1` que contém pelo menos um item.  
  
-   Referências aos namespaces <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
