---
title: 'Como: Permitir que os usuários para copiarem várias células na área de transferência do controle DataGridView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: ad603204ad97df55e8b7f30686b08103a55f1e8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624321"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Como: Permitir que os usuários para copiarem várias células na área de transferência do controle DataGridView dos Windows Forms
Quando você habilita a cópia de célula, você tornar os dados no seu <xref:System.Windows.Forms.DataGridView> controle facilmente acessível para outras aplicações através de <xref:System.Windows.Forms.Clipboard>. Os valores das células selecionadas são convertidos em cadeias de caracteres e adicionados à área de transferência como valores de texto delimitado por tabulação para colar em aplicativos como Bloco de Notas e Excel, e como uma tabela formatada em HTML para colar em aplicativos como Word.  
  
 É possível configurar a cópia de célula para copiar somente valores de célula, para incluir texto de cabeçalho de linha e coluna nos dados da área de transferência ou para incluir somente texto de cabeçalho quando os usuários selecionarem linhas ou colunas inteiras.  
  
 Dependendo do modo de seleção, os usuários podem selecionar vários grupos de células desconectados. Quando um usuário copia as células para a área de transferência, linhas e colunas sem células selecionadas não são copiadas. Todas as outras linhas ou colunas se tornam linhas e colunas na tabela de dados copiados para a área de transferência. Células não selecionadas nessas linhas ou colunas são copiadas como espaços reservados em branco para a área de transferência.  
  
### <a name="to-enable-cell-copying"></a>Habilitar cópia de célula  
  
-   Definir a propriedade <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo a seguir demonstra como as células são copiadas para a Área de Transferência. Este exemplo inclui um botão que copia as células selecionadas para a área de transferência usando o <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> método e exibe a área de transferência de conteúdo em uma caixa de texto.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este código requer:  
  
-   Referências aos assemblies N:System e N:System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [Seleção e uso da Área de Transferência com o controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
