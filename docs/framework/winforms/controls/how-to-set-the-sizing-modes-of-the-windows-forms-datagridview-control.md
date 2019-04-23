---
title: 'Como: Definir os modos de dimensionamento do controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: d92322da6644c110f5e3177acebea62799a0ed89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977867"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Como: Definir os modos de dimensionamento do controle DataGridView do Windows Forms
Os procedimentos a seguir demonstram alguns cenários comuns que personalizam ou combinam as opções de dimensionamento disponíveis para o <xref:System.Windows.Forms.DataGridView> controle e para colunas específicas em um controle.  
  
### <a name="to-create-a-fixed-width-column"></a>Para criar uma coluna de largura fixa  
  
-   Defina o <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> propriedade para <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, o <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> propriedade a ser <xref:System.Windows.Forms.DataGridViewTriState.False>, o <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> propriedade a ser `true`e o <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> propriedade para um valor apropriado.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Para criar uma coluna que ajusta seu tamanho para o conteúdo  
  
-   Defina o <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> propriedade para um modo de dimensionamento com base no conteúdo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Para criar colunas de modo de preenchimento para valores de tamanho e importância variáveis  
  
-   Defina as <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> propriedade para <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> para definir o modo de dimensionamento para todas as colunas que não substituem esse valor. Defina o <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> propriedades das colunas para valores que são proporcionais a seu média larguras de conteúdo. Defina o <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> propriedades das colunas importantes para garantir que a exibição de conteúdo parcial.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo a seguir fornece um aplicativo de demonstração que pode ajudá-lo a entender as opções de dimensionamento descritas neste tópico.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Para usar esse aplicativo de demonstração:  
  
-   Altere o tamanho do formulário. Observe como as colunas do modo de preenchimento alteram suas larguras enquanto retêm as proporções indicadas pelo <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores de propriedade. Observe como uma coluna <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> impede a alteração quando o formulário é muito pequeno.  
  
-   Altere os tamanhos das colunas arrastando os divisores de coluna com o mouse. Observe como algumas colunas não podem ser redimensionadas e como as colunas redimensionáveis não podem ficar mais estreitas do que suas larguras mínimas.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
