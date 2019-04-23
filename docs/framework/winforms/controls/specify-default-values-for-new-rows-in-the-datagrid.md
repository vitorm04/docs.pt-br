---
title: 'Como: Especificar valores padrão para novas linhas no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 8a90cbef7032fd3753a6c9ec0b856a4e2ea1db27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193688"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Como: Especificar valores padrão para novas linhas no controle DataGridView do Windows Forms
Você pode fazer mais conveniente a entrada de dados quando o aplicativo em default preenche os valores para linhas recém-adicionadas. Com o <xref:System.Windows.Forms.DataGridView> classe, você pode preencher em default valores com o <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> eventos. Esse evento é gerado quando o usuário insere a linha para novos registros. Quando seu código manipula esse evento, você pode preencher desejadas células com valores de sua escolha.  
  
 O exemplo de código a seguir demonstra como especificar valores padrão para novas linhas usando o <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> eventos.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Um `NewCustomerId` função para gerar exclusivo `CustomerID` valores.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
