---
title: Modo de preenchimento da coluna no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: a85745d39903719ec1e44ccf70df72d472720b7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214722"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Modo de preenchimento da coluna no controle DataGridView dos Windows Forms
No modo de preenchimento de coluna, o <xref:System.Windows.Forms.DataGridView> controle redimensiona as colunas automaticamente para que elas preencham a largura da área de exibição disponíveis. O controle não exibe a barra de rolagem horizontal, exceto quando ele for necessário para manter a largura de cada coluna igual a ou maior que sua <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> valor da propriedade.  
  
 O comportamento de dimensionamento de cada coluna depende do seu <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> propriedade. O valor dessa propriedade é herdado da coluna <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> propriedade ou o controle <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> propriedade se o valor da coluna for <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (o valor padrão).  
  
 Cada coluna pode ter um modo de tamanho diferente, mas nenhuma coluna com um modo de tamanho de <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> compartilharão a largura da área de exibição que não seja usada por outras colunas. Essa largura é dividida entre as colunas do modo de preenchimento em proporções relativo a seu <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores de propriedade. Por exemplo, se duas colunas tiverem <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores de 100 e 200, a primeira coluna serão metade da largura da segunda coluna.  
  
## <a name="user-resizing-in-fill-mode"></a>Redimensionamento de usuário no modo de preenchimento  
 Ao contrário de modos de dimensionamento que redimensionarem com base no conteúdo da célula, o modo de preenchimento não impedir que os usuários redimensionem colunas que tenham <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> valores de propriedade de `true`. Quando um usuário redimensionar uma coluna do modo de preenchimento, quaisquer colunas do modo de preenchimento depois da coluna redimensionada (à direita se <xref:System.Windows.Forms.Control.RightToLeft%2A> é `false`; caso contrário, à esquerda) também serão redimensionadas para compensar a alteração na largura disponível. Se não houver nenhuma coluna do modo de preenchimento depois da coluna redimensionada, todas as outras colunas do modo de preenchimento no controle serão redimensionadas para compensar. Se não houver nenhuma outra coluna do modo de preenchimento no controle, o redimensionamento será ignorado. Se uma coluna que não estiver no modo de preenchimento for redimensionada, todas as colunas do modo de preenchimento no controle terão os tamanhos alterados para compensar.  
  
 Depois de redimensionar uma coluna do modo de preenchimento, o <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> os valores para todas as colunas que foram alteradas serão ajustadas proporcionalmente. Por exemplo, se tiverem quatro colunas de modo de preenchimento <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores de 100, o redimensionamento da segunda coluna para metade de sua largura original resultará em <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores de 100, 50, 125 e 125. Redimensionamento de uma coluna que não está no modo de preenchimento não alterará nenhum <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores porque as colunas do modo de preenchimento simplesmente serão redimensionadas para compensar, mantendo as mesmas proporções.  
  
## <a name="content-based-fillweight-adjustment"></a>Ajuste de FillWeight baseado em conteúdo  
 Você pode inicializar <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores para colunas do modo de preenchimento usando o <xref:System.Windows.Forms.DataGridView> automática de redimensionamento de métodos, como o <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> método. Esse método primeiro calcula as larguras necessárias por colunas para exibir seu conteúdo. Em seguida, o controle se ajusta a <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores para todas as colunas do modo de preenchimento para que suas proporções correspondam às proporções das larguras calculadas. Por fim, o controle redimensiona as colunas do modo de preenchimento usando o novo <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> proporções para que todas as colunas no controle preencham o espaço horizontal disponível.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Usando os valores apropriados para o <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, e <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> propriedades, você pode personalizar os comportamentos de dimensionamento de colunas para vários cenários diferentes.  
  
 O seguinte código de demonstração lhe permite fazer experiências com valores diferentes para o <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, e <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> propriedades das colunas diferentes. Neste exemplo, uma <xref:System.Windows.Forms.DataGridView> controle é associado a seu próprio <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção e uma coluna está associada a cada um dos <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, e <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> propriedades. Cada uma das colunas também é representada por uma linha no controle e a alteração dos valores em uma linha atualizará as propriedades da coluna correspondente para que você possa ver como os valores interagem.  
  
### <a name="code"></a>Código  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Comentários  
 Para usar esse aplicativo de demonstração:  
  
-   Altere o tamanho do formulário. Observe como colunas alteram suas larguras enquanto retêm as proporções indicadas pelo <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores de propriedade.  
  
-   Altere os tamanhos das colunas arrastando os divisores de coluna com o mouse. Observe como o <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores alterados.  
  
-   Alterar o <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> para uma coluna de valor e, em seguida, arraste para redimensionar o formulário. Observe como, quando você faz o formulário pequeno o suficiente, o <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> valores não ficam abaixo de <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> valores.  
  
-   Alterar o <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> valores para todas as colunas para números grandes para que os valores combinados excedam a largura do controle. Observe como a barra de rolagem horizontal é exibida.  
  
-   Alterar o <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> valores para algumas colunas. Observe o efeito quando você redimensiona as colunas ou o formulário.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
-   Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>
- [Redimensionando colunas e linhas no controle DataGridView dos Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
