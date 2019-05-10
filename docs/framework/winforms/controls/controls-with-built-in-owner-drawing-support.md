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
ms.openlocfilehash: df3a61dae9ad926f56da4e9d15e0e8b8c6f1c8a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648254"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Controles com suporte de desenho do proprietário interno
Proprietário do desenho nos Windows Forms, que é também conhecido como desenho personalizado, é uma técnica para alterar a aparência visual de certos controles.  
  
> [!NOTE]
>  A palavra "controle" neste tópico é usada para indicar as classes que derivam de <xref:System.Windows.Forms.Control> ou <xref:System.ComponentModel.Component>.  
  
 Normalmente, Windows manipula pintura automaticamente usando as configurações de propriedade, como <xref:System.Windows.Forms.Control.BackColor%2A> para determinar a aparência de um controle. Com o desenho do proprietário, assumir o processo de pintura, alterando os elementos que não estão disponíveis usando propriedades de aparência. Por exemplo, muitos controles permitem que você defina a cor do texto que é exibido, mas você está limitado a uma única cor. Desenho do proprietário permite que você faça coisas como parte do texto de exibição em preto e parte em vermelho.  
  
 Na prática, o desenho do proprietário é semelhante ao desenho de gráficos em um formulário. Por exemplo, você pode usar métodos gráficos em um manipulador para o formulário <xref:System.Windows.Forms.Control.Paint> eventos para emular um `ListBox` controle, mas você teria de escrever seu próprio código para lidar com todas as interações do usuário. Com o desenho do proprietário, o controle usa seu código para desenhar seu conteúdo, mas caso contrário retém todos os seus recursos intrínsecos. Você pode usar métodos gráficos para desenhar cada item no controle ou personalizar alguns aspectos de cada item enquanto você usa a aparência padrão para outros aspectos de cada item.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Desenho do proprietário no Controle dos Windows Forms  
 Para executar o desenho do proprietário na controles que oferecem suporte a ele, você normalmente define uma propriedade e manipular um ou mais eventos.  
  
 A maioria dos controles têm de desenho do proprietário que suporte uma propriedade `OwnerDraw` ou `DrawMode` que indica se o controle será aumentará seu evento ou eventos de desenho quando ela pinta a si mesma.  
  
 Controles que não têm uma propriedade `OwnerDraw` ou `DrawMode`, incluem o `DataGridView` controle, que fornece eventos de desenho que ocorrem automaticamente e o `ToolStrip` controle, que é desenhado usando uma classe de renderização externa que tem seus próprios eventos relacionados ao desenho.  
  
 Há muitos tipos diferentes de eventos de desenho, mas ocorre um evento típico de desenho para desenhar um único item em um controle. O manipulador de eventos recebe um `EventArgs` objeto que contém informações sobre o item que está sendo desenhado e ferramentas que você pode usar para desenhá-lo. Por exemplo, esse objeto normalmente contém o número de índice do item dentro da sua coleção pai, uma <xref:System.Drawing.Rectangle> que indica o item exibe limites e um <xref:System.Drawing.Graphics> objeto para chamar métodos de pintura. Em alguns casos, o `EventArgs` objeto fornece informações adicionais sobre o item e os métodos que você pode chamar para pintar alguns aspectos do item por padrão, como a tela de fundo ou um retângulo de foco.  
  
 Para criar um controle reutilizável que contém as personalizações desenhados pelo proprietário, crie uma nova classe que deriva de uma classe de controle que dá suporte ao desenho do proprietário. Em vez de manipular eventos de desenho, incluir o código de desenho do proprietário em substituições de método ou métodos apropriados de `On` *EventName* na nova classe. Certifique-se de que você chamar o método ou métodos da classe base `On` *EventName* nesse caso, para que os usuários de seu controle possam manipular eventos de desenho do proprietário e fornecer personalização adicional.  
  
 O Windows Forms a seguir controla desenho do proprietário em todas as versões do .NET Framework:  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem> (usado pelo <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu>)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 Os seguintes controles oferecem suporte apenas no desenho do proprietário [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 Os seguintes controles dão suporte ao desenho do proprietário e são novos no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 As seções a seguir fornecem detalhes adicionais para cada um desses controles.  
  
### <a name="listbox-and-combobox-controls"></a>Controles de Caixa de Combinação e Caixa de listagem  
 O <xref:System.Windows.Forms.ListBox> e <xref:System.Windows.Forms.ComboBox> controles permitem que você desenhe itens individuais no controle de tudo em um tamanho ou de tamanhos variados.  
  
> [!NOTE]
>  Embora o <xref:System.Windows.Forms.CheckedListBox> controle deriva o <xref:System.Windows.Forms.ListBox> controle, ele não suporta desenho do proprietário.  
  
 Para desenhar cada item do mesmo tamanho, defina as `DrawMode` propriedade para <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> e lidar com o `DrawItem` eventos.  
  
 Para desenhar cada item usando um tamanho diferente, defina as `DrawMode` propriedade para <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> e lidar com ambos os `MeasureItem` e `DrawItem` eventos. O evento `MeasureItem` permite indicar o tamanho de um item antes do evento `DrawItem` ocorrer para aquele item.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [Como: Criar texto dimensionado da variável em um controle ComboBox](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Componente do MenuItem  
 O <xref:System.Windows.Forms.MenuItem> componente representa um item de menu único em um <xref:System.Windows.Forms.MainMenu> ou <xref:System.Windows.Forms.ContextMenu> componente.  
  
 Para desenhar um <xref:System.Windows.Forms.MenuItem>, defina sua `OwnerDraw` propriedade a ser `true` e tratar seu `DrawItem` eventos. Para personalizar o tamanho do item de menu antes do evento `DrawItem` ocorrer, identifique os eventos `MeasureItem` do item.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>Controle TabControl  
 O <xref:System.Windows.Forms.TabControl> controle permite que você desenhe as guias individuais no controle. Desenho do proprietário afeta somente as guias; o <xref:System.Windows.Forms.TabPage> conteúdo não é afetado.  
  
 Para desenhar cada guia em um <xref:System.Windows.Forms.TabControl>, defina a `DrawMode` propriedade <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> e lidar com o `DrawItem` eventos. Esse evento ocorre uma vez para cada guia somente quando a guia estiver visível no controle.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>Componente ToolTip  
 O <xref:System.Windows.Forms.ToolTip> componente permite que você desenhe toda ToolTip quando ele for exibido.  
  
 Para desenhar um <xref:System.Windows.Forms.ToolTip>, defina sua `OwnerDraw` propriedade a ser `true` e tratar seu `Draw` eventos. Para personalizar o tamanho do <xref:System.Windows.Forms.ToolTip> antes do `Draw` evento ocorre, identifique o `Popup` eventos e defina o <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> propriedade no manipulador de eventos.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>Controle ListView  
 O <xref:System.Windows.Forms.ListView> controle permite que você desenhe itens individuais, subitens e cabeçalhos de coluna no controle.  
  
 Para habilitar o controle de desenho do proprietário, defina a propriedade `OwnerDraw` para `true`.  
  
 Para desenhar cada item no controle, identifique o evento `DrawItem`.  
  
 Para desenhar cada cabeçalho de coluna ou subitem no controle quando o <xref:System.Windows.Forms.ListView.View%2A> estiver definida como <xref:System.Windows.Forms.View.Details>, lidar com as `DrawSubItem` e `DrawColumnHeader` eventos.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>Controle TreeView  
 O <xref:System.Windows.Forms.TreeView> controle permite que você desenhe os nós individuais no controle.  
  
 Para desenhar somente o texto exibido em cada nó, defina as `DrawMode` propriedade para <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> e lidar com o `DrawNode` evento para desenhar o texto.  
  
 Para desenhar todos os elementos de cada nó, defina as `DrawMode` propriedade para <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> e lidar com o `DrawNode` evento para desenhar qualquer elementos necessários, como texto, ícones, caixas de verificação, adição e subtração sinais e linhas que conectam os nós.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos de referência:  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>Controle DataGridView  
 O <xref:System.Windows.Forms.DataGridView> controle permite que você desenhe as células e linhas individuais no controle.  
  
 Para desenhar células individuais, identifique o evento `CellPainting`.  
  
 Para desenhar linhas individuais ou elementos de linhas, identifique um ou ambos os eventos `RowPrePaint` e `RowPostPaint`. O evento `RowPrePaint` ocorre antes das células em uma linha serem pintadas e o evento `RowPostPaint` ocorre depois que as células são pintadas. Você pode identificar ambos os eventos e o evento `CellPainting` para pintar a tela de fundo de linha, células individuais e primeiro plano linha separadamente ou você pode fornecer personalizações específicas em que você precisa deles e use a exibição padrão para outros elementos da linha.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [Como: Personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [Como: Personalizar a aparência das linhas no controle DataGridView dos Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>Controle ToolStrip  
 <xref:System.Windows.Forms.ToolStrip> e controles derivados permitem que você personalize qualquer aspecto de sua aparência.  
  
 Para fornecer processamento personalizado para <xref:System.Windows.Forms.ToolStrip> controles, defina a `Renderer` propriedade de uma <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, ou <xref:System.Windows.Forms.ToolStripContentPanel> para um `ToolStripRenderer` do objeto e manipule um ou mais dos muitos eventos de desenho fornecidos pelo `ToolStripRenderer` classe. Como alternativa, definir um `Renderer` propriedade para uma instância de sua própria classe derivada de `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> que implementa ou substitui específico `On` *EventName* métodos.  
  
 Para obter mais informações, incluindo exemplos de código, consulte os seguintes tópicos:  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [Como: Criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [Como: Personalizar o desenho de um controle ToolStrip](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Consulte também

- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
