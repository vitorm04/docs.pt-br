---
title: Como alterar a ordem de colunas no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a2048025bbd582d812d0748cc2d1521f44f140
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Como alterar a ordem de colunas no controle DataGridView dos Windows Forms
Quando você usa um <xref:System.Windows.Forms.DataGridView> para exibir dados de uma fonte de dados, as colunas no esquema da fonte de dados, às vezes, não aparecem na ordem em que deseja exibi-los. Você pode alterar a ordem das colunas de exibido usando o <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> propriedade o <xref:System.Windows.Forms.DataGridViewColumn> classe.  
  
 O exemplo de código a seguir reposiciona algumas das colunas geradas automaticamente ao se associar à tabela Clientes no banco de dados de exemplo Northwind. Para obter mais informações sobre como associar o <xref:System.Windows.Forms.DataGridView> em uma tabela de banco de dados, consulte [como: associar dados para o controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Há suporte para esta tarefa no Visual Studio.  Veja também [Como alterar a ordem de colunas no controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle chamado `customersDataGridView` que está associado a uma tabela com os nomes de coluna indicada, como o `Customers` tabela no banco de dados de exemplo Northwind.  
  
-   Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, e <xref:System.Xml?displayProperty=nameWithType> assemblies.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Como associar dados ao controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
