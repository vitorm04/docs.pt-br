---
title: "Visão geral do controle SplitContainer (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SplitContainer
helpviewer_keywords: SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10f18c46c85ed840b6625d9ed754d1d036a80975
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="splitcontainer-control-overview-windows-forms"></a>Visão geral do controle SplitContainer (Windows Forms)
O controle <xref:System.Windows.Forms.SplitContainer> dos Windows Forms pode ser considerado uma composição; são dois painéis separados por uma barra móvel. Quando o ponteiro do mouse passa sobre a barra, ele muda de forma para mostrar que a barra é móvel.  
  
> [!IMPORTANT]
>  No **caixa de ferramentas**, <xref:System.Windows.Forms.SplitContainer> controlar substitui o <xref:System.Windows.Forms.Splitter> controle que existia na versão anterior do [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. O <xref:System.Windows.Forms.SplitContainer> controle é preferido sobre o <xref:System.Windows.Forms.Splitter> controle. O <xref:System.Windows.Forms.Splitter> classe ainda está incluída no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para compatibilidade com aplicativos existentes, mas recomendamos que você use o <xref:System.Windows.Forms.SplitContainer> controle para novos projetos.  
  
 Com o <xref:System.Windows.Forms.SplitContainer> controle, você pode criar interfaces de usuário complexas; frequentemente, uma seleção em um painel determina quais objetos são mostrados no painel de. Essa disposição é muito eficiente para exibir e procurar informações. Ter dois painéis permite agregar as informações em áreas e a barra, ou “divisor”, tornando mais fácil para os usuários redimensionar os painéis.  
  
 Mais de um <xref:System.Windows.Forms.SplitContainer> controle também pode ser aninhado, com a segunda <xref:System.Windows.Forms.SplitContainer> controle orientado na horizontal, para criar painéis superior e inferior.  
  
 Lembre-se que o <xref:System.Windows.Forms.SplitContainer> controle é teclado acessível por padrão, os usuários poderão pressionar as teclas de direção para mover o separador se o <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> está definida como `false`.  
  
 O <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade o <xref:System.Windows.Forms.SplitContainer> controle determina a direção do separador, não do próprio controle. Portanto, quando essa propriedade é definida como <xref:System.Windows.Forms.Orientation.Vertical>, o separador é executado de cima para baixo, criação de painéis esquerdos e direito.  
  
 Além disso, lembre-se que o valor da <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriedade varia dependendo do valor da <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade. Para obter mais informações, consulte <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriedade.  
  
 Você também pode diminuir o tamanho e a movimentação do <xref:System.Windows.Forms.SplitContainer> controle. O <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> propriedade determina qual painel permanecerá o mesmo tamanho após a <xref:System.Windows.Forms.SplitContainer> controle é redimensionado e o <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> propriedade determina se o separador é móvel pelo teclado ou mouse.  
  
> [!NOTE]
>  Mesmo que o <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> está definida como `true`, o divisor pode ainda ser movido programaticamente; por exemplo, usando o <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> propriedade.  
  
 Por fim, cada painel do <xref:System.Windows.Forms.SplitContainer> controle tem propriedades para determinar seu tamanho individual.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriedades, métodos e eventos normalmente usados  
  
|Nome|Descrição|  
|----------|-----------------|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Determina qual painel permanecerá o mesmo tamanho após a <xref:System.Windows.Forms.SplitContainer> controle é redimensionado.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Determina se o divisor pode ser movido com o teclado ou mouse.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.Orientation%2A>|Determina se o separador é disposto na vertical ou horizontal.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Determina a distância em pixels da borda esquerda ou superior para o divisor móvel.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Determina a distância mínima, em pixels, que o divisor pode ser movido pelo usuário.|  
|Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>|Determina a espessura, em pixels, do separador.|  
|Evento <xref:System.Windows.Forms.SplitContainer.SplitterMoving>|Ocorre quando o separador está sendo movido.|  
|Evento <xref:System.Windows.Forms.SplitContainer.SplitterMoved>|Ocorre quando o separador foi movido.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.SplitContainer>  
 [Controle SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Exemplo do controle SplitContainer](http://msdn.microsoft.com/en-us/9015fad0-7108-4d85-a83a-a72d038c4f65)
