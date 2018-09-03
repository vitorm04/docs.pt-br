---
title: Como habilitar exibição lado a lado em um controle ListView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 4eb418bbd2d399c57ce4a8235130a9939be56ce4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480962"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Como habilitar exibição lado a lado em um controle ListView dos Windows Forms
Com o recurso de exibição de bloco a <xref:System.Windows.Forms.ListView> controle, você pode fornecer um equilíbrio visual entre informações gráficas e textuais. As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes. Exibição lado a lado funciona em combinação com recursos de marca de agrupamento ou inserção no <xref:System.Windows.Forms.ListView> controle.  
  
 O modo de exibição lado a lado usa um ícone de 32 x 32 pixels e várias linhas de texto, conforme mostrado nas imagens a seguir.  
  
 ![Exibição lado a lado em um controle ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
Ícones e texto da exibição lado a lado  
  
 Para habilitar exibição lado a lado, defina as <xref:System.Windows.Forms.ListView.View%2A> propriedade para <xref:System.Windows.Forms.View.Tile>. Você pode ajustar o tamanho dos blocos, definindo o <xref:System.Windows.Forms.ListView.TileSize%2A> propriedade e o número de linhas de texto exibidas no bloco ajustando a <xref:System.Windows.Forms.ListView.Columns%2A> coleção.  
  
> [!NOTE]
>  A exibição lado a lado está disponível apenas no [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando seu aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método. Em sistemas operacionais anteriores, qualquer código relacionado ao modo de exibição lado a lado não terá efeito e o <xref:System.Windows.Forms.ListView> controle exibe no modo de exibição de ícones grandes. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Para definir a exibição lado a lado programaticamente  
  
1.  Use o <xref:System.Windows.Forms.View> enumeração do <xref:System.Windows.Forms.ListView> controle.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo a seguir demonstra a exibição lado a lado com blocos modificados para mostrar as três linhas de texto. O tamanho de bloco foi ajustado para evitar encapsulamento de linha.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
-   Um arquivo de ícone denominado book.ico no mesmo diretório do arquivo executável.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Recursos do Windows XP e controles do Windows Forms](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
