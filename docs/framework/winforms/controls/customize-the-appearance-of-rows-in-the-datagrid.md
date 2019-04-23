---
title: 'Como: Personalizar a aparência de linhas no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 107ec75257907b934412d9ee333b00d5df05a99c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110313"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Como: Personalizar a aparência de linhas no controle DataGridView do Windows Forms
Você pode controlar a aparência dos <xref:System.Windows.Forms.DataGridView> linhas manipulando uma ou ambas as <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> eventos. Esses eventos são projetados para que você pode pintar apenas o que você deseja enquanto permitindo que o <xref:System.Windows.Forms.DataGridView> controle pintará o restante. Por exemplo, se você desejar pintar um plano de fundo personalizado, você pode manipular o <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> eventos e permitem que as células individuais pintar seus próprio conteúdo em primeiro plano. Como alternativa, você pode permitir que as células se pintarem e adicione o conteúdo do primeiro plano personalizado em um manipulador para o <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> eventos. Você também pode desabilitar a pintura da célula e pintar tudo por conta própria em uma <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> manipulador de eventos.  
  
 O exemplo de código a seguir implementa manipuladores para ambos os eventos a fim de fornecer uma tela de fundo de seleção do gradiente e algum conteúdo de primeiro plano personalizado que abrange várias colunas.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
