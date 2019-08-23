---
title: Visão geral do controle SplitContainer (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 76299d9bbd2b3eac4e765dfacf579c9979721fff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963206"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>Visão geral do controle SplitContainer (Windows Forms)
O controle <xref:System.Windows.Forms.SplitContainer> dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel. Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.  
  
> [!IMPORTANT]
> Na **caixa**de ferramentas <xref:System.Windows.Forms.SplitContainer> , o controle <xref:System.Windows.Forms.Splitter> substitui o controle que estava lá na versão anterior do Visual Studio. O <xref:System.Windows.Forms.SplitContainer> controle é muito preferido sobre o <xref:System.Windows.Forms.Splitter> controle. A <xref:System.Windows.Forms.Splitter> classe ainda está incluída no .NET Framework para compatibilidade com os aplicativos existentes, mas é altamente recomendável que você use <xref:System.Windows.Forms.SplitContainer> o controle para novos projetos.  
  
 Com o <xref:System.Windows.Forms.SplitContainer> controle, você pode criar interfaces de usuário complexas; muitas vezes, uma seleção em um painel determina quais objetos são mostrados no outro painel. Essa disposição é muito eficiente para exibir e procurar informações. Ter dois painéis permite agregar as informações em áreas e a barra, ou “divisor”, tornando mais fácil para os usuários redimensionar os painéis.  
  
 Mais de um <xref:System.Windows.Forms.SplitContainer> controle também pode ser aninhado, com o <xref:System.Windows.Forms.SplitContainer> segundo controle orientado horizontalmente, para criar painéis superiores e inferiores.  
  
 Lembre-se de <xref:System.Windows.Forms.SplitContainer> que o controle é acessível por teclado por padrão; os usuários podem pressionar as teclas de seta para mover o <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> separador se `false`a propriedade for definida como.  
  
 A <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade<xref:System.Windows.Forms.SplitContainer> do controle determina a direção do divisor, não do próprio controle. Portanto, quando essa propriedade é definida como <xref:System.Windows.Forms.Orientation.Vertical>, o divisor é executado de cima para baixo, criando painéis à esquerda e à direita.  
  
 Além disso, lembre-se de que o <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> valor da propriedade varia dependendo do valor <xref:System.Windows.Forms.SplitContainer.Orientation%2A> da propriedade. Para obter mais informações, <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> consulte Propriedade.  
  
 Você também pode restringir o tamanho e a movimentação do <xref:System.Windows.Forms.SplitContainer> controle. A <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> propriedade determina qual painel permanecerá com o mesmo tamanho depois <xref:System.Windows.Forms.SplitContainer> que o controle for redimensionado, <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> e a propriedade determinará se o divisor é móvel pelo teclado ou mouse.  
  
> [!NOTE]
> Mesmo que a <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Propriedade seja definida como `true`, o divisor ainda pode ser movido programaticamente; por exemplo, usando a <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> propriedade.  
  
 Por fim, cada painel do <xref:System.Windows.Forms.SplitContainer> controle tem propriedades para determinar seu tamanho individual.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriedades, métodos e eventos normalmente usados  
  
|Nome|Descrição|  
|----------|-----------------|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Determina qual painel permanecerá com o mesmo tamanho depois <xref:System.Windows.Forms.SplitContainer> que o controle for redimensionado.|  
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
