---
title: Visão geral do controle SplitContainer (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 4afdd764b2f6ef7f15e8bd26459f0fa4c7d345e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971958"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>Visão geral do controle SplitContainer (Windows Forms)
O controle <xref:System.Windows.Forms.SplitContainer> dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel. Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.  
  
> [!IMPORTANT]
>  No **caixa de ferramentas**, <xref:System.Windows.Forms.SplitContainer> controlar substitui o <xref:System.Windows.Forms.Splitter> controle que existia na versão anterior do Visual Studio. O <xref:System.Windows.Forms.SplitContainer> controle é preferida em relação a <xref:System.Windows.Forms.Splitter> controle. O <xref:System.Windows.Forms.Splitter> classe ainda está incluída na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para compatibilidade com aplicativos existentes, mas recomendamos que você use o <xref:System.Windows.Forms.SplitContainer> controle para novos projetos.  
  
 Com o <xref:System.Windows.Forms.SplitContainer> controle, você pode criar interfaces do usuário complexas; muitas vezes, uma seleção em um painel determina quais objetos são mostrados no outro painel. Essa disposição é muito eficiente para exibir e procurar informações. Ter dois painéis permite agregar as informações em áreas e a barra, ou “divisor”, tornando mais fácil para os usuários redimensionar os painéis.  
  
 Mais de um <xref:System.Windows.Forms.SplitContainer> controle também pode ser aninhado, com a segunda <xref:System.Windows.Forms.SplitContainer> controle orientado horizontalmente, para criar painéis superior e inferior.  
  
 Lembre-se que o <xref:System.Windows.Forms.SplitContainer> controle é acessível pelo teclado por padrão, os usuários podem pressionar as teclas de direção para mover o divisor se a <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> estiver definida como `false`.  
  
 O <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade do <xref:System.Windows.Forms.SplitContainer> controle determina a direção do divisor, não do próprio controle. Portanto, quando essa propriedade é definida como <xref:System.Windows.Forms.Orientation.Vertical>, o divisor é executado de cima para baixo, Criando painéis esquerdo e direito.  
  
 Além disso, lembre-se que o valor da <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriedade varia dependendo do valor da <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade. Para obter mais informações, consulte <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriedade.  
  
 Você também pode restringir o tamanho e a movimentação do <xref:System.Windows.Forms.SplitContainer> controle. O <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> propriedade determina qual painel permanecerá do mesmo tamanho após o <xref:System.Windows.Forms.SplitContainer> controle é redimensionado e o <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> propriedade determina se o divisor é movido pelo teclado ou mouse.  
  
> [!NOTE]
>  Mesmo se o <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> estiver definida como `true`, o divisor ainda poderá ser movido programaticamente; por exemplo, usando o <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> propriedade.  
  
 Por fim, cada painel do <xref:System.Windows.Forms.SplitContainer> controle tem propriedades para determinar seu tamanho individual.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriedades, métodos e eventos normalmente usados  
  
|Nome|Descrição|  
|----------|-----------------|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Determina qual painel permanecerá o mesmo tamanho após o <xref:System.Windows.Forms.SplitContainer> controle é redimensionado.|  
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
