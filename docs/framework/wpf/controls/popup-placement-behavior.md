---
title: Comportamento de posicionamento do pop-up
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: ca984aa724cf3f076d6073aa8b8179abfb91d26c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951727"
---
# <a name="popup-placement-behavior"></a>Comportamento de posicionamento do pop-up
Um <xref:System.Windows.Controls.Primitives.Popup> controle exibe o conteúdo em uma janela separada que flutua sobre um aplicativo. Você pode especificar a posição de um <xref:System.Windows.Controls.Primitives.Popup> em relação a um controle, ao mouse ou à tela usando as <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>Propriedades, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> .  Essas propriedades funcionam em conjunto para proporcionar flexibilidade na especificação da posição do <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> As <xref:System.Windows.Controls.ToolTip> classes <xref:System.Windows.Controls.ContextMenu> e também definem essas cinco propriedades e se comportam de forma semelhante.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Posicionamento do pop-up  
 O posicionamento de um <xref:System.Windows.Controls.Primitives.Popup> pode ser relativo a um <xref:System.Windows.UIElement> ou à tela inteira.  O exemplo a seguir cria <xref:System.Windows.Controls.Primitives.Popup> quatro controles que são relativos a <xref:System.Windows.UIElement>um — nesse caso, uma imagem. Todos os <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> `image1`controles têm a propriedade definida como, mas cada <xref:System.Windows.Controls.Primitives.Popup> um tem um valor diferente para a propriedade de posicionamento. <xref:System.Windows.Controls.Primitives.Popup>  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 A ilustração a seguir mostra a imagem e <xref:System.Windows.Controls.Primitives.Popup> os controles  
  
 ![Imagem com quatro controles pop-up](./media/popup-placement-behavior/popup-placement-intro.png "Imagem com quatro pop-ups")    
  
 Este exemplo simples demonstra como definir as <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> Propriedades e <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> , mas usando as <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>Propriedades, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> , você tem ainda mais controle sobre onde o <xref:System.Windows.Controls.Primitives.Popup> está posicionado.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definições de termos: A anatomia de um popup  
 Os termos a seguir são úteis para entender como <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>as <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>propriedades <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>,, <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> e se relacionam entre si e <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Objeto de destino  
  
- Área de destino  
  
- Origem do destino  
  
- Ponto de alinhamento do pop-up  
  
 Esses termos fornecem uma maneira conveniente de se referir a vários aspectos <xref:System.Windows.Controls.Primitives.Popup> do e ao controle ao qual ele está associado.  
  
### <a name="target-object"></a>Objeto de destino  
 O *objeto de destino* é o elemento ao <xref:System.Windows.Controls.Primitives.Popup> qual o está associado. Se a <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriedade for definida, ela especificará o objeto de destino.  Se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> não estiver definido, e o <xref:System.Windows.Controls.Primitives.Popup> tiver um pai, o pai será o objeto de destino.  Se não houver nenhum <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> valor e nenhum pai, não haverá nenhum objeto de destino e o <xref:System.Windows.Controls.Primitives.Popup> será posicionado em relação à tela.  
  
 O exemplo a seguir cria <xref:System.Windows.Controls.Primitives.Popup> um que é o filho de <xref:System.Windows.Controls.Canvas>um.  O exemplo não define a <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriedade <xref:System.Windows.Controls.Primitives.Popup>no. O valor padrão de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, portanto, <xref:System.Windows.Controls.Primitives.Popup> o é exibido <xref:System.Windows.Controls.Canvas>abaixo de.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 A ilustração a seguir mostra que <xref:System.Windows.Controls.Primitives.Popup> o está posicionado em <xref:System.Windows.Controls.Canvas>relação ao.  
  
 ![Controle Popup sem PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Popup sem PlacementTarget.")  

 O exemplo a seguir cria <xref:System.Windows.Controls.Primitives.Popup> um que é o filho de <xref:System.Windows.Controls.Canvas>um, mas desta vez <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> o é definido `ellipse1`como, portanto, o Popup aparece <xref:System.Windows.Shapes.Ellipse>abaixo de.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 A ilustração a seguir mostra que <xref:System.Windows.Controls.Primitives.Popup> o está posicionado em <xref:System.Windows.Shapes.Ellipse>relação ao.  
  
 ![Popup posicionado em relação a uma elipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Pop-up com PlacementTarget")    
  
> [!NOTE]
> Para <xref:System.Windows.Controls.ToolTip>, o valor padrão de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Para <xref:System.Windows.Controls.ContextMenu>, o valor padrão de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Esses valores são explicados posteriormente, em “Como as propriedades funcionam juntas”.  
  
### <a name="target-area"></a>Área de destino  
 A *área de destino* é a área na tela à qual <xref:System.Windows.Controls.Primitives.Popup> o é relativo. Nos exemplos anteriores, o <xref:System.Windows.Controls.Primitives.Popup> é alinhado com os limites do objeto de destino, mas em alguns casos, o <xref:System.Windows.Controls.Primitives.Popup> é alinhado a outros limites, mesmo que o tenha <xref:System.Windows.Controls.Primitives.Popup> um objeto de destino.  Se a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> propriedade for definida, a área de destino será diferente dos limites do objeto de destino.  
  
 O exemplo a seguir cria <xref:System.Windows.Controls.Canvas> dois objetos, cada um contendo <xref:System.Windows.Shapes.Rectangle> um e <xref:System.Windows.Controls.Primitives.Popup>um.  Em ambos os casos, o objeto de destino <xref:System.Windows.Controls.Primitives.Popup> para o <xref:System.Windows.Controls.Canvas>é o. O <xref:System.Windows.Controls.Primitives.Popup> na primeira <xref:System.Windows.Controls.Canvas> tem o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Rect.X%2A> <xref:System.Windows.Rect.Y%2A> conjunto,<xref:System.Windows.Rect.Width%2A>com suas Propriedades,,edefinidascomo50,50,50e100,respectivamente.<xref:System.Windows.Rect.Height%2A> O <xref:System.Windows.Controls.Primitives.Popup> no segundo <xref:System.Windows.Controls.Canvas> não tem o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> conjunto.  Como resultado, o <xref:System.Windows.Controls.Primitives.Popup> primeiro está posicionado abaixo do <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> e o segundo <xref:System.Windows.Controls.Primitives.Popup> está posicionado abaixo do. <xref:System.Windows.Controls.Canvas> Cada <xref:System.Windows.Controls.Canvas> também contém um <xref:System.Windows.Shapes.Rectangle> que tem os mesmos limites do <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> para o primeiro <xref:System.Windows.Controls.Primitives.Popup>.  Observe que o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> não cria um elemento visível no aplicativo; o exemplo cria um <xref:System.Windows.Shapes.Rectangle> para representar o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Pop-up com e sem PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Popup com e sem PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Origem do destino e ponto de alinhamento do pop-up  
 A *origem do destino* e o *ponto de alinhamento do pop-up* são pontos de referência na área de destino e no pop-up, respectivamente, usados para posicionamento. Você pode usar as <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> propriedades <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> e para deslocar o pop-up da área de destino.  O <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> são relativos à origem de destino e ao ponto de alinhamento Popup. O valor da <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade determina onde a origem de destino e o ponto de alinhamento de popup estão localizados.  
  
 O exemplo a seguir cria <xref:System.Windows.Controls.Primitives.Popup> um e define <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> as <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> Propriedades e como 20.  A <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade é definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (o padrão), portanto, a origem de destino é o canto inferior esquerdo da área de destino e o ponto de alinhamento pop <xref:System.Windows.Controls.Primitives.Popup>-up é o canto superior esquerdo do.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Posicionamento de pop-up com ponto de alinhamento de origem de destino](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Popup com as e VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Como as propriedades trabalham juntas  
 Os valores de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>e <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> precisam ser considerados juntos para descobrir a área de destino, a origem de destino e o ponto de alinhamento pop-up corretos.  Por exemplo, se o valor de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> for <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, não há nenhum objeto de destino, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> o é ignorado e a área de destino são os limites do ponteiro do mouse. Por outro lado, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> se for <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai determinará o objeto de destino <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> e determinará a área de destino.  
  
 A tabela a seguir descreve o objeto de destino, a área de destino, a origem de destino e o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ponto <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> de alinhamento pop- <xref:System.Windows.Controls.Primitives.PlacementMode> up e indica se e são usados para cada valor de enumeração.  
  
|PlacementMode|Objeto de destino|Área de destino|Origem do destino|Ponto de alinhamento do pop-up|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>é ignorado.|A tela ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definida.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo à tela.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>é ignorado.|A tela ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definida.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo à tela.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto inferior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O centro da área de destino.|O centro do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>é ignorado.|O canto inferior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>é ignorado.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior direito da área de destino.|O canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> , se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 As ilustrações a seguir <xref:System.Windows.Controls.Primitives.Popup>mostram o, a área de destino, a origem de destino e <xref:System.Windows.Controls.Primitives.PlacementMode> o ponto de alinhamento pop-up para cada valor. Em cada figura, a área de destino é amarela e a <xref:System.Windows.Controls.Primitives.Popup> é azul.  
  
 ![Pop-up com posicionamento absoluto ou AbsolutePoint] O (./media/popup-placement-behavior/popup-placement-absolute.png "posicionamento é absoluto ou AbsolutePoint.")    
  
 ![Pop-up com posicionamento inferior] O (./media/popup-placement-behavior/popup-placement-bottom.png "posicionamento é inferior.")   
  
 ![Pop-up com posicionamento centralizado] O (./media/popup-placement-behavior/popup-placement-center.png "posicionamento é o centro.")    
  
 ![Pop-up com posicionamento à esquerda] O (./media/popup-placement-behavior/popup-placement-left.png "posicionamento é deixado.")   
  
 ![Pop-up com posicionamento do mouse] O (./media/popup-placement-behavior/popup-placement-mouse.png "posicionamento é o mouse.")  
  
 ![Pop-up com posicionamento MousePoint] O (./media/popup-placement-behavior/popup-placement-mousepoint.png "posicionamento é MousePoint.")  
  
 ![Pop-up com posicionamento relativo ou RelativePoint] O (./media/popup-placement-behavior/popup-placement-relative.png "posicionamento é relativo ou RelativePoint.")    
  
 ![Pop-up com posicionamento à direita] O (./media/popup-placement-behavior/popup-placement-right.png "posicionamento está certo.")    
  
 ![Pop-up com posicionamento superior] A (./media/popup-placement-behavior/popup-placement-top.png "colocação é superior.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Quando o pop-up encontra a borda da tela  
 Por motivos de segurança, <xref:System.Windows.Controls.Primitives.Popup> um não pode ser ocultado pela borda de uma tela. Uma das três ações a seguir ocorre quando o <xref:System.Windows.Controls.Primitives.Popup> encontra uma borda de tela:  
  
- O Popup se realinha ao longo da borda da tela que obscureceria o <xref:System.Windows.Controls.Primitives.Popup>.  
  
- O pop-up usa um ponto de alinhamento do pop-up diferente.  
  
- O pop-up usa uma origem do destino e um ponto de alinhamento do pop-up diferentes.  
  
 Essas opções são descritas detalhadamente mais adiante nesta seção.  
  
 O comportamento do <xref:System.Windows.Controls.Primitives.Popup> quando ele encontra uma borda de tela depende do valor <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> da propriedade e da borda da tela que o Popup encontra. A tabela a seguir resume o comportamento quando o <xref:System.Windows.Controls.Primitives.Popup> encontra uma borda de tela para <xref:System.Windows.Controls.Primitives.PlacementMode> cada valor.  
  
|PlacementMode|Borda superior|Borda inferior|Borda esquerda|Borda direita|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up é alterado para o canto inferior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do.|Alinha-se com a borda esquerda.|O ponto de alinhamento pop-up é alterado para o canto superior <xref:System.Windows.Controls.Primitives.Popup>direito do.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alinha-se com a borda superior.|A origem de destino muda para o canto superior esquerdo da área de destino e o ponto de alinhamento Popup muda para o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|A origem de destino muda para o canto superior direito da área de destino e o ponto de alinhamento Popup muda para o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alinha-se com a borda superior.|A origem de destino muda para o canto superior esquerdo da área de destino (os limites do ponteiro do mouse) e o ponto de alinhamento pop-up é alterado para o canto inferior esquerdo <xref:System.Windows.Controls.Primitives.Popup>do.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up é alterado para o canto inferior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do.|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up é alterado para o canto inferior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do.|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|A origem de destino muda para o canto superior esquerdo da área de destino e o ponto de alinhamento Popup muda para o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|A origem de destino muda para o canto inferior esquerdo da área de destino e o ponto de alinhamento Popup muda para o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>. Em vigor, isso é o mesmo que quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alinhamento com a borda da tela  
 Um <xref:System.Windows.Controls.Primitives.Popup> pode se alinhar à borda da tela reposicionando-se, de modo <xref:System.Windows.Controls.Primitives.Popup> que todo esteja visível na tela.  Quando isso ocorre, a distância entre a origem de destino e o ponto de alinhamento pop-up pode <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> diferir dos valores de e. <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, ,<xref:System.Windows.Controls.Primitives.PlacementMode.Center>ou <xref:System.Windows.Controls.Primitives.Popup> , o se alinha a cada borda da tela. <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>  Por exemplo, suponha que um <xref:System.Windows.Controls.Primitives.Popup> tenha <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> definido como <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> definido como 100.  Se a borda inferior da tela ocultar todo ou parte do <xref:System.Windows.Controls.Primitives.Popup>, o <xref:System.Windows.Controls.Primitives.Popup> se reposicionará na borda inferior da tela e a distância vertical entre a origem de destino e o ponto de alinhamento pop-up será menor que 100. A ilustração a seguir demonstra isso.  
  
 ![Pop-up que se alinha à borda da tela](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "O Popup se alinha à borda da tela.")    
  
### <a name="changing-the-popup-alignment-point"></a>Alterando o ponto de alinhamento do pop-up  
 Se <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> for <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, ,<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> ou<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, o ponto de alinhamento pop-up será alterado quando o pop-up encontrar a borda inferior ou direita da tela.  
  
 A ilustração a seguir demonstra que <xref:System.Windows.Controls.Primitives.Popup>, quando a borda da tela inferior oculta todo ou parte do, o ponto de alinhamento popup é o canto inferior esquerdo <xref:System.Windows.Controls.Primitives.Popup>do.  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup encontra a borda inferior da tela e altera o ponto de alinhamento pop-up.")  

 A ilustração a seguir demonstra que quando <xref:System.Windows.Controls.Primitives.Popup> o é ocultado pela borda direita da tela, o ponto de alinhamento popup é o canto superior direito <xref:System.Windows.Controls.Primitives.Popup>do.  
  
 ![Novo ponto de alinhamento pop-up devido à borda da tela](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup encontra a borda direita da tela e altera o ponto de alinhamento Popup.")    
  
 Se o <xref:System.Windows.Controls.Primitives.Popup> encontrar as bordas de tela inferior e direita, o ponto de alinhamento pop-up será o canto inferior <xref:System.Windows.Controls.Primitives.Popup>direito do.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Mudando a origem do destino e o ponto de alinhamento do pop-up  
 Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> for <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, ,<xref:System.Windows.Controls.Primitives.PlacementMode.Left> ,ou<xref:System.Windows.Controls.Primitives.PlacementMode.Top>, a origem de destino e o ponto de alinhamento de Popup serão alterados se uma determinada borda de tela for encontrada. <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.PlacementMode.Right>  A borda da tela que faz com que a posição seja alterada <xref:System.Windows.Controls.Primitives.PlacementMode> depende do valor.  
  
 A ilustração a seguir demonstra que <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> quando <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> o é <xref:System.Windows.Controls.Primitives.Popup> e o encontra a borda de tela inferior, a origem de destino é o canto superior esquerdo da área de destino e o ponto de alinhamento pop-up é o canto inferior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "O posicionamento é inferior e o Popup encontra a borda inferior da tela.")    
  
 A ilustração a seguir demonstra que <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> quando <xref:System.Windows.Controls.Primitives.PlacementMode.Left> o é <xref:System.Windows.Controls.Primitives.Popup> e o encontra a borda da tela à esquerda, a origem de destino é o canto superior direito da área de destino e o ponto de alinhamento pop-up é o canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda da tela esquerda] O (./media/popup-placement-behavior/popup-placement-left-screen-edge.png "posicionamento é deixado e o Popup encontra a borda esquerda da tela.")  
  
 A ilustração a seguir demonstra que <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> quando <xref:System.Windows.Controls.Primitives.PlacementMode.Right> o é <xref:System.Windows.Controls.Primitives.Popup> e o encontra a borda da tela direita, a origem de destino é o canto superior esquerdo da área de destino e o ponto de alinhamento pop-up é o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda da tela direita] O (./media/popup-placement-behavior/popup-placement-right-screen-edge.png "posicionamento está correto e o Popup encontra a borda direita da tela.")  

 A ilustração a seguir demonstra que <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> quando <xref:System.Windows.Controls.Primitives.PlacementMode.Top> o é <xref:System.Windows.Controls.Primitives.Popup> e o encontra a borda de tela superior, a origem de destino é o canto inferior esquerdo da área de destino e o ponto de alinhamento pop-up é o canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda superior da tela](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "O posicionamento é superior e o Popup encontra a borda superior da tela.")  
  
 A ilustração a seguir demonstra que <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> quando <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> o é <xref:System.Windows.Controls.Primitives.Popup> e o encontra a borda de tela inferior, a origem de destino é o canto superior esquerdo da área de destino (os limites do ponteiro do mouse) e o alinhamento de Popup ponto é o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![novo ponto de alinhamento devido ao mouse perto da borda da tela] O (./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "posicionamento é o mouse e o Popup encontra a borda inferior da tela.")    
  
### <a name="customizing-popup-placement"></a>Personalizando o posicionamento do pop-up  
 Você pode personalizar a origem de destino e o ponto de alinhamento pop <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> -up <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>definindo a propriedade como. Em seguida, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> defina um delegado que retorne um conjunto de possíveis pontos de posicionamento e eixos primários (em <xref:System.Windows.Controls.Primitives.Popup>ordem de preferência) para o. O ponto que mostra a maior parte do <xref:System.Windows.Controls.Primitives.Popup> é selecionado.  A posição do <xref:System.Windows.Controls.Primitives.Popup> será ajustada automaticamente se o <xref:System.Windows.Controls.Primitives.Popup> estiver oculto pela borda da tela. Para ver um exemplo, consulte [Especificar uma posição de pop-up personalizada](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Consulte também

- [Amostra de posicionamento do pop-up](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
