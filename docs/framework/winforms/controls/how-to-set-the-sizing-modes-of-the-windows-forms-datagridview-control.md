---
title: Definir os modos de dimensionamento do controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738395"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Como definir os modos de dimensionamento do controle DataGridView dos Windows Forms
Os procedimentos a seguir demonstram alguns cenários comuns que personalizam ou combinam as opções de dimensionamento disponíveis para o controle de <xref:System.Windows.Forms.DataGridView> e para colunas específicas em um controle.  
  
### <a name="to-create-a-fixed-width-column"></a>Para criar uma coluna de largura fixa  
  
- Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> como <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> como <xref:System.Windows.Forms.DataGridViewTriState.False>, a propriedade <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> como `true`e a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> como um valor apropriado.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Para criar uma coluna que ajusta seu tamanho para o conteúdo  
  
- Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> como um modo de dimensionamento baseado em conteúdo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Para criar colunas de modo de preenchimento para valores de tamanho e importância variáveis  
  
- Defina a propriedade <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> como <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> para definir o modo de dimensionamento para todas as colunas que não substituem esse valor. Defina as propriedades <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> das colunas como valores que são proporcionais a suas larguras de conteúdo médias. Defina as propriedades <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> de colunas importantes para garantir a exibição de conteúdo parcial.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo a seguir fornece um aplicativo de demonstração que pode ajudá-lo a entender as opções de dimensionamento descritas neste tópico.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Para usar esse aplicativo de demonstração:  
  
- Altere o tamanho do formulário. Observe como as colunas de modo de preenchimento alteram suas larguras enquanto retém as proporções indicadas pelos valores de propriedade de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>. Observe como a <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> de uma coluna impede que ela seja alterada quando o formulário é muito pequeno.  
  
- Altere os tamanhos das colunas, arrastando os divisores de coluna com o mouse. Observe como algumas colunas não podem ser redimensionadas e como as colunas redimensionáveis não podem ficar mais estreitas do que suas larguras mínimas.  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
