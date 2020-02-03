---
title: Visão geral do controle SplitContainer
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 5cb5240ed4ebe3e27c20844681068711c222e9a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742916"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>Visão geral do controle SplitContainer (Windows Forms)
O controle <xref:System.Windows.Forms.SplitContainer> dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel. Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.  
  
> [!IMPORTANT]
> Na **caixa de ferramentas**, <xref:System.Windows.Forms.SplitContainer> controle substitui o controle de <xref:System.Windows.Forms.Splitter> que estava lá na versão anterior do Visual Studio. O controle de <xref:System.Windows.Forms.SplitContainer> é muito preferível ao controle de <xref:System.Windows.Forms.Splitter>. A classe <xref:System.Windows.Forms.Splitter> ainda está incluída no .NET Framework para compatibilidade com os aplicativos existentes, mas é altamente recomendável que você use o controle de <xref:System.Windows.Forms.SplitContainer> para novos projetos.  
  
 Com o controle de <xref:System.Windows.Forms.SplitContainer>, você pode criar interfaces de usuário complexas; Geralmente, uma seleção em um painel determina quais objetos são mostrados no outro painel. Essa disposição é muito eficiente para exibir e procurar informações. Ter dois painéis permite agregar as informações em áreas e a barra, ou “divisor”, tornando mais fácil para os usuários redimensionar os painéis.  
  
 Mais de um controle de <xref:System.Windows.Forms.SplitContainer> também pode ser aninhado, com o segundo controle de <xref:System.Windows.Forms.SplitContainer> orientado horizontalmente, para criar painéis superiores e inferiores.  
  
 Lembre-se de que o controle de <xref:System.Windows.Forms.SplitContainer> é acessível por teclado por padrão; os usuários podem pressionar as teclas de seta para mover o separador se a propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> estiver definida como `false`.  
  
 A propriedade <xref:System.Windows.Forms.SplitContainer.Orientation%2A> do controle de <xref:System.Windows.Forms.SplitContainer> determina a direção do divisor, não do próprio controle. Portanto, quando essa propriedade é definida como <xref:System.Windows.Forms.Orientation.Vertical>, o divisor é executado de cima para baixo, criando painéis à esquerda e à direita.  
  
 Além disso, lembre-se de que o valor da propriedade <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> varia dependendo do valor da propriedade <xref:System.Windows.Forms.SplitContainer.Orientation%2A>. Para obter mais informações, consulte <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriedade.  
  
 Você também pode restringir o tamanho e a movimentação do controle de <xref:System.Windows.Forms.SplitContainer>. A propriedade <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> determina qual painel permanecerá com o mesmo tamanho depois que o controle de <xref:System.Windows.Forms.SplitContainer> é redimensionado e a propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> determina se o divisor é móvel pelo teclado ou mouse.  
  
> [!NOTE]
> Mesmo que a propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> seja definida como `true`, o divisor ainda pode ser movido programaticamente; por exemplo, usando a propriedade <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>.  
  
 Por fim, cada painel do controle de <xref:System.Windows.Forms.SplitContainer> tem propriedades para determinar seu tamanho individual.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriedades, métodos e eventos normalmente usados  
  
|{1&gt;Nome&lt;1}|Descrição|  
|----------|-----------------|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Determina qual painel permanecerá com o mesmo tamanho depois que o controle de <xref:System.Windows.Forms.SplitContainer> for redimensionado.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Determina se o divisor pode ser movido com o teclado ou mouse.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.Orientation%2A>|Determina se o separador é disposto na vertical ou horizontal.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Determina a distância em pixels da borda esquerda ou superior para o divisor móvel.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Determina a distância mínima, em pixels, que o divisor pode ser movido pelo usuário.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>|Determina a espessura, em pixels, do separador.|  
|Evento <xref:System.Windows.Forms.SplitContainer.SplitterMoving>|Ocorre quando o separador está sendo movido.|  
|Evento <xref:System.Windows.Forms.SplitContainer.SplitterMoved>|Ocorre quando o separador foi movido.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SplitContainer>
- [Controle SplitContainer](splitcontainer-control-windows-forms.md)
- [Exemplo do controle SplitContainer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
