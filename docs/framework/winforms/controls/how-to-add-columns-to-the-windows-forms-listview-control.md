---
title: Como adicionar colunas ao controle ListView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 4c284e9d2798a1992e3152a85eca47c8d33bfde8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Como adicionar colunas ao controle ListView dos Windows Forms
Na exibição de detalhes, o <xref:System.Windows.Forms.ListView> controle pode exibir várias colunas para cada item de lista. Você pode usar as colunas para exibição ao usuário vários tipos de informações sobre cada item da lista. Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo. Para obter informações sobre como preencher as colunas depois que elas são criadas, consulte [como: Exibir subitens em colunas com o controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Para adicionar colunas programaticamente  
  
1.  Definir o controle <xref:System.Windows.Forms.ListView.View%2A> propriedade <xref:System.Windows.Forms.View.Details>.  
  
2.  Use o <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> método de exibição de lista <xref:System.Windows.Forms.ListView.Columns%2A> propriedade.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView>  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
