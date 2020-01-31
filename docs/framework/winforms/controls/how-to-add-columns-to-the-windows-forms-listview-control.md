---
title: Adicionar colunas ao controle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: dd438ffbadddfc37ec9eb15e59a908bb58472a45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744588"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Como adicionar colunas ao controle ListView dos Windows Forms
No modo de exibição de detalhes, o controle de <xref:System.Windows.Forms.ListView> pode exibir várias colunas para cada item de lista. Você pode usar as colunas a serem exibidas para o usuário vários tipos de informações sobre cada item de lista. Por exemplo, uma lista de arquivos pode exibir o nome do arquivo, tipo de arquivo, tamanho e data da última modificação do arquivo. Para obter informações sobre como preencher as colunas depois que elas são criadas, consulte [como Exibir subitens em colunas com o controle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Para adicionar colunas programaticamente  
  
1. Defina a propriedade <xref:System.Windows.Forms.ListView.View%2A> do controle como <xref:System.Windows.Forms.View.Details>.  
  
2. Use o método <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> da propriedade <xref:System.Windows.Forms.ListView.Columns%2A> da exibição de lista.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ListView>
- [Controle ListView](listview-control-windows-forms.md)
- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
