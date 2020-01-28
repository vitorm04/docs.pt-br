---
title: Especificar valores padrão para novas linhas no controle DataGridView
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
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742935"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Como especificar valores padrão para novas linhas no controle DataGridView dos Windows Forms
Você pode tornar a entrada de dados mais conveniente quando o aplicativo preenche valores padrão para linhas adicionadas recentemente. Com a classe <xref:System.Windows.Forms.DataGridView>, você pode preencher valores padrão com o evento <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>. Esse evento é gerado quando o usuário insere a linha para novos registros. Quando seu código manipula esse evento, você pode preencher as células desejadas com os valores de sua escolha.  
  
 O exemplo de código a seguir demonstra como especificar valores padrão para novas linhas usando o evento <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Uma função `NewCustomerId` para gerar valores de `CustomerID` exclusivos.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
