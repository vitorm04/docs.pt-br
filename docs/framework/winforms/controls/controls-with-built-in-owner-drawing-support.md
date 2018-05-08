---
title: Controles com suporte de desenho do proprietário interno
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: a5cbdc733a2f1cda3e708ceaae8604297f8da58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Controles com suporte de desenho do proprietário interno
Proprietário do desenho nos Windows Forms, que é também conhecido como desenho personalizado, é uma técnica para alterar a aparência visual de certos controles.  
  
> [!NOTE]
>  A palavra "control" neste tópico é usada para indicar as classes que derivam do <xref:System.Windows.Forms.Control> ou <xref:System.ComponentModel.Component>.  
  
 Normalmente, Windows manipula pintura automaticamente usando as configurações de propriedade, como <xref:System.Windows.Forms.Control.BackColor%2A> para determinar a aparência de um controle. Com o desenho do proprietário, assumir o processo de pintura, alterando os elementos que não estão disponíveis usando propriedades de aparência. Por exemplo, muitos controles permitem que você defina a cor do texto que é exibido, mas você está limitado a uma única cor. Desenho do proprietário permite que você faça coisas como parte do texto de exibição em preto e parte em vermelho.  
  
 Na prática, o desenho do proprietário é semelhante ao desenho de gráficos em um formulário. Por exemplo, você pode usar métodos gráficos em um manipulador para o formulário <xref:System.Windows.Forms.Control.Paint> evento para emular uma `ListBox` controle, mas você teria de escrever seu próprio código para lidar com todas as interações do usuário. Com o desenho do proprietário, o controle usa seu código para desenhar seu conteúdo, mas caso contrário retém todos os seus recursos intrínsecos. Você pode usar métodos gráficos para desenhar cada item no controle ou personalizar alguns aspectos de cada item enquanto você usa a aparência padrão para outros aspectos de cada item.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Desenho do proprietário no Controle dos Windows Forms  
 Para executar o desenho do proprietário na controles que oferecem suporte a ele, você normalmente define uma propriedade e manipular um ou mais eventos.  
  
 A maioria dos controles têm de desenho do proprietário que suporte uma propriedade `OwnerDraw` ou `DrawMode` que indica se o controle será aumentará seu evento ou eventos de desenho quando ela pinta a si mesma.  
  
 Controles que não têm uma propriedade `OwnerDraw` ou `DrawMode`, incluem o `DataGridView` controle, que fornece eventos de desenho que ocorrem automaticamente e o `ToolStrip` controle, que é desenhado usando uma classe de renderização externa que tem seus próprios eventos relacionados ao desenho.  
  
 Há muitos tipos diferentes de eventos de desenho, mas ocorre um evento típico de desenho para desenhar um único item em um controle. O manipulador de eventos recebe um `EventArgs` objeto que contém informações sobre o item que está sendo desenhado e ferramentas que você pode usar para desenhá-lo. Por exemplo, esse objeto normalmente contém o número de índice do item dentro de sua coleção pai, uma <xref:System.Drawing.Rectangle> que indica o item exibe limites e um <xref:System.Drawing.Graphics> objeto para chamar métodos de pintura. Em alguns casos, o `EventArgs` objeto fornece informações adicionais sobre o item e os métodos que você pode chamar para pintar alguns aspectos do item por padrão, como a tela de fundo ou um retângulo de foco.  
  
 Para criar um controle reutilizável que contém as personalizações desenhados pelo proprietário, crie uma nova classe que deriva de uma classe de controle que dá suporte ao desenho do proprietário. Em vez de manipular eventos de desenho, incluir o código de desenho do proprietário em substituições de método ou métodos apropriados de `On` *EventName* na nova classe. Certifique-se de que você chamar o método ou métodos da classe base `On` *EventName* nesse caso, para que os usuários de seu controle possam manipular eventos de desenho do proprietário e fornecer personalização adicional.  
  
 O Windows Forms a seguir controla desenho do proprietário em todas as versões do .NET Framework:  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (usado pelo <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Os seguintes controles oferecem suporte apenas no desenho do proprietário [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Os seguintes controles dão suporte ao desenho do proprietário e são novos no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 As seções a seguir fornecem detalhes adicionais para cada um desses controles.  
  
### <a name="listbox-and-combobox-controls"></a>Controles de Caixa de Combinação e Caixa de listagem  
 O <xref:System.Windows.Forms.ListBox> e <xref:System.Windows.Forms.ComboBox> controles permitem que você desenhar itens individuais no controle em um tamanho ou em diferentes tamanhos.  
  
> [!NOTE]
>  Embora o <xref:System.Windows.Forms.CheckedListBox> controle é derivado de <xref:System.Windows.Forms.ListBox> controle, ele não suporta desenho do proprietário.  
  
 Para desenhar cada item do mesmo tamanho, defina o `DrawMode` propriedade <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> e tratar o `DrawItem` evento.  
  
 Para desenhar cada item usando um tamanho diferente, defina o `DrawMode` propriedade <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> e lidar com ambos os `MeasureItem` e `DrawItem` eventos. O evento `MeasureItem` permite indicar o tamanho de um item antes do evento `DrawItem` ocorrer para aquele item.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [Como criar texto dimensionado da variável em um controle ComboBox](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Componente do MenuItem  
 O <xref:System.Windows.Forms.MenuItem> componente representa um item de menu único em uma <xref:System.Windows.Forms.MainMenu> ou <xref:System.Windows.Forms.ContextMenu> componente.  
  
 Para desenhar uma <xref:System.Windows.Forms.MenuItem>, defina seu `OwnerDraw` propriedade `true` e manipular seu `DrawItem` eventos. Para personalizar o tamanho do item de menu antes do evento `DrawItem` ocorrer, identifique os eventos `MeasureItem` do item.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>Controle TabControl  
 O <xref:System.Windows.Forms.TabControl> controle permite que você desenhe guias individuais no controle. Desenho proprietário afeta somente as guias; o <xref:System.Windows.Forms.TabPage> conteúdo não é afetado.  
  
 Para desenhar cada guia um <xref:System.Windows.Forms.TabControl>, defina o `DrawMode` propriedade <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> e lidar com o `DrawItem` evento. Esse evento ocorre uma vez para cada guia somente quando a guia estiver visível no controle.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>Componente ToolTip  
 O <xref:System.Windows.Forms.ToolTip> componente permite que você desenhe a dica de ferramenta inteira quando ele for exibido.  
  
 Para desenhar uma <xref:System.Windows.Forms.ToolTip>, defina seu `OwnerDraw` propriedade `true` e manipular seu `Draw` eventos. Para personalizar o tamanho do <xref:System.Windows.Forms.ToolTip> antes do `Draw` evento ocorrer, lidar com o `Popup` evento e defina o <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> propriedade no manipulador de eventos.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>Controle ListView  
 O <xref:System.Windows.Forms.ListView> controle permite que você desenhar itens individuais, subitens e cabeçalhos de coluna no controle.  
  
 Para habilitar o controle de desenho do proprietário, defina a propriedade `OwnerDraw` para `true`.  
  
 Para desenhar cada item no controle, identifique o evento `DrawItem`.  
  
 Para desenhar cada cabeçalho de coluna ou subitem no controle quando o <xref:System.Windows.Forms.ListView.View%2A> está definida como <xref:System.Windows.Forms.View.Details>, tratar o `DrawSubItem` e `DrawColumnHeader` eventos.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>Controle TreeView  
 O <xref:System.Windows.Forms.TreeView> controle permite que você desenhe nós individuais no controle.  
  
 Para desenhar apenas o texto exibido em cada nó, defina o `DrawMode` propriedade <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> e tratar o `DrawNode` evento para desenhar o texto.  
  
 Para desenhar todos os elementos de cada nó, defina o `DrawMode` propriedade <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> e tratar o `DrawNode` evento para desenhar o elementos necessários, como caixas, adição e subtração sinais de seleção de texto, ícones e linhas que conectam os nós.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>Controle DataGridView  
 O <xref:System.Windows.Forms.DataGridView> controle permite que você desenhar linhas e células individuais no controle.  
  
 Para desenhar células individuais, identifique o evento `CellPainting`.  
  
 Para desenhar linhas individuais ou elementos de linhas, identifique um ou ambos os eventos `RowPrePaint` e `RowPostPaint`. O evento `RowPrePaint` ocorre antes das células em uma linha serem pintadas e o evento `RowPostPaint` ocorre depois que as células são pintadas. Você pode identificar ambos os eventos e o evento `CellPainting` para pintar a tela de fundo de linha, células individuais e primeiro plano linha separadamente ou você pode fornecer personalizações específicas em que você precisa deles e use a exibição padrão para outros elementos da linha.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>Controle ToolStrip  
 <xref:System.Windows.Forms.ToolStrip> e controles derivados permitem personalizar todos os aspectos de sua aparência.  
  
 Para fornecer processamento personalizado para <xref:System.Windows.Forms.ToolStrip> controles, defina o `Renderer` propriedade de um <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, ou <xref:System.Windows.Forms.ToolStripContentPanel> para um `ToolStripRenderer` de objeto e lidar com um ou mais dos muitos eventos de desenho fornecidos pelo `ToolStripRenderer` classe. Como alternativa, defina um `Renderer` propriedade a uma instância de sua própria classe derivada de `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> que implementa ou substitui específico `On` *EventName* métodos.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Como criar e definir um renderizador personalizado para o controle ToolStrip no Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Como personalizar o desenho de um controle ToolStrip](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Consulte também  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
