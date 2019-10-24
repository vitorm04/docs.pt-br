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
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "69951727"
---
# <a name="popup-placement-behavior"></a>Comportamento de posicionamento do pop-up
Um controle de <xref:System.Windows.Controls.Primitives.Popup> exibe o conteúdo em uma janela separada que flutua sobre um aplicativo. Você pode especificar a posição de um <xref:System.Windows.Controls.Primitives.Popup> em relação a um controle, ao mouse ou à tela usando as propriedades <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>.  Essas propriedades funcionam em conjunto para proporcionar flexibilidade na especificação da posição do <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> As classes <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ContextMenu> também definem essas cinco propriedades e se comportam de forma semelhante.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Posicionamento do pop-up  
 O posicionamento de um <xref:System.Windows.Controls.Primitives.Popup> pode ser relativo a uma <xref:System.Windows.UIElement> ou à tela inteira.  O exemplo a seguir cria quatro controles de <xref:System.Windows.Controls.Primitives.Popup> que são relativos a um <xref:System.Windows.UIElement> — nesse caso, uma imagem. Todos os controles de <xref:System.Windows.Controls.Primitives.Popup> têm a propriedade <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> definida como `image1`, mas cada <xref:System.Windows.Controls.Primitives.Popup> tem um valor diferente para a propriedade de posicionamento.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 A ilustração a seguir mostra a imagem e os controles de <xref:System.Windows.Controls.Primitives.Popup>  
  
 ![Imagem com quatro controles de pop-up](./media/popup-placement-behavior/popup-placement-intro.png "Imagem com quatro pop-ups")    
  
 Este exemplo simples demonstra como definir as propriedades <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> e <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, mas usando as propriedades <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>, você tem ainda mais controle sobre onde o <xref:System.Windows.Controls.Primitives.Popup> está posicionado.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definições de termos: a anatomia de um pop-up  
 Os termos a seguir são úteis para entender como as propriedades <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> se relacionam entre si e a <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Objeto de destino  
  
- Área de destino  
  
- Origem do destino  
  
- Ponto de alinhamento do pop-up  
  
 Esses termos fornecem uma maneira conveniente de se referir a vários aspectos do <xref:System.Windows.Controls.Primitives.Popup> e ao controle ao qual ele está associado.  
  
### <a name="target-object"></a>Objeto de destino  
 O *objeto de destino* é o elemento ao qual o <xref:System.Windows.Controls.Primitives.Popup> está associado. Se a propriedade <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> for definida, ela especificará o objeto de destino.  Se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> não estiver definido e o <xref:System.Windows.Controls.Primitives.Popup> tiver um pai, o pai será o objeto de destino.  Se não houver nenhum valor <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> e nenhum pai, não haverá nenhum objeto de destino e o <xref:System.Windows.Controls.Primitives.Popup> será posicionado em relação à tela.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.Popup> que é o filho de um <xref:System.Windows.Controls.Canvas>.  O exemplo não define a propriedade <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> no <xref:System.Windows.Controls.Primitives.Popup>. O valor padrão para <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, portanto, o <xref:System.Windows.Controls.Primitives.Popup> aparece abaixo do <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 A ilustração a seguir mostra que o <xref:System.Windows.Controls.Primitives.Popup> está posicionado em relação ao <xref:System.Windows.Controls.Canvas>.  
  
 ![Controle de pop-up sem PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Popup sem PlacementTarget.")  

 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.Popup> que é o filho de um <xref:System.Windows.Controls.Canvas>, mas desta vez o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é definido como `ellipse1`, portanto, o Popup aparece abaixo do <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 A ilustração a seguir mostra que o <xref:System.Windows.Controls.Primitives.Popup> está posicionado em relação ao <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Pop-up posicionado em relação a uma elipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Pop-up com PlacementTarget")    
  
> [!NOTE]
> Por <xref:System.Windows.Controls.ToolTip>, o valor padrão de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Por <xref:System.Windows.Controls.ContextMenu>, o valor padrão de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Esses valores são explicados posteriormente, em “Como as propriedades funcionam juntas”.  
  
### <a name="target-area"></a>Área de destino  
 A *área de destino* é a área na tela à qual o <xref:System.Windows.Controls.Primitives.Popup> é relativo. Nos exemplos anteriores, o <xref:System.Windows.Controls.Primitives.Popup> está alinhado com os limites do objeto de destino, mas em alguns casos, o <xref:System.Windows.Controls.Primitives.Popup> está alinhado a outros limites, mesmo que o <xref:System.Windows.Controls.Primitives.Popup> tenha um objeto de destino.  Se a propriedade <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> for definida, a área de destino será diferente dos limites do objeto de destino.  
  
 O exemplo a seguir cria dois objetos <xref:System.Windows.Controls.Canvas>, cada um contendo um <xref:System.Windows.Shapes.Rectangle> e um <xref:System.Windows.Controls.Primitives.Popup>.  Em ambos os casos, o objeto de destino para o <xref:System.Windows.Controls.Primitives.Popup> é o <xref:System.Windows.Controls.Canvas>. O <xref:System.Windows.Controls.Primitives.Popup> na primeira <xref:System.Windows.Controls.Canvas> tem o conjunto de <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, com suas propriedades <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A> e <xref:System.Windows.Rect.Height%2A> definidas como 50, 50, 50 e 100, respectivamente. O <xref:System.Windows.Controls.Primitives.Popup> no segundo <xref:System.Windows.Controls.Canvas> não tem o conjunto de <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  Como resultado, a primeira <xref:System.Windows.Controls.Primitives.Popup> está posicionada abaixo da <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> e a segunda <xref:System.Windows.Controls.Primitives.Popup> está posicionada abaixo do <xref:System.Windows.Controls.Canvas>. Cada <xref:System.Windows.Controls.Canvas> também contém uma <xref:System.Windows.Shapes.Rectangle> que tem os mesmos limites que o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> da primeira <xref:System.Windows.Controls.Primitives.Popup>.  Observe que o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> não cria um elemento visível no aplicativo; o exemplo cria um <xref:System.Windows.Shapes.Rectangle> para representar o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Pop-up com e sem PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Popup com e sem PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Origem do destino e ponto de alinhamento do pop-up  
 A *origem do destino* e o *ponto de alinhamento do pop-up* são pontos de referência na área de destino e no pop-up, respectivamente, usados para posicionamento. Você pode usar as propriedades <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> para deslocar o pop-up da área de destino.  O <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> são relativos à origem de destino e ao ponto de alinhamento Popup. O valor da propriedade <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> determina onde a origem de destino e o ponto de alinhamento de popup estão localizados.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Primitives.Popup> e define as propriedades <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> como 20.  A propriedade <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (o padrão), portanto, a origem de destino é o canto inferior esquerdo da área de destino e o ponto de alinhamento pop-up é o canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Posicionamento do pop-up com ponto de alinhamento da origem do destino](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Popup com as e VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Como as propriedades trabalham juntas  
 Os valores de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> e <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> precisam ser considerados juntos para descobrir a área de destino, a origem de destino e o ponto de alinhamento pop-up corretos.  Por exemplo, se o valor de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> for <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, não haverá nenhum objeto de destino, o <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> será ignorado e a área de destino será o limite do ponteiro do mouse. Por outro lado, se <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> for <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, o <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai determinará o objeto de destino e <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> determinará a área de destino.  
  
 A tabela a seguir descreve o objeto de destino, a área de destino, a origem de destino e o ponto de alinhamento pop-up e indica se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> e <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> são usadas para cada valor de enumeração <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
|PlacementMode|Objeto de destino|Área de destino|Origem do destino|Ponto de alinhamento do pop-up|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|A tela ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ela estiver definida.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo à tela.|O canto superior esquerdo da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|A tela ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ela estiver definida.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo à tela.|O canto superior esquerdo da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto inferior esquerdo da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O centro da área de destino.|O centro do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é ignorado.|O canto inferior esquerdo da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é ignorado.|O canto superior esquerdo da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior direito da área de destino.|O canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou pai.|O objeto de destino ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ele estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto de destino.|O canto superior esquerdo da área de destino.|O canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 As ilustrações a seguir mostram a <xref:System.Windows.Controls.Primitives.Popup>, a área de destino, a origem de destino e o ponto de alinhamento pop-up para cada valor de <xref:System.Windows.Controls.Primitives.PlacementMode>. Em cada figura, a área de destino é amarela e a <xref:System.Windows.Controls.Primitives.Popup> é azul.  
  
 ![Pop-up com posicionamento Absolute ou AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "O posicionamento é absoluto ou AbsolutePoint.")    
  
 ![Pop-up com posicionamento Bottom](./media/popup-placement-behavior/popup-placement-bottom.png "O posicionamento é inferior.")   
  
 ![Pop-up com posicionamento Center](./media/popup-placement-behavior/popup-placement-center.png "O posicionamento é o centro.")    
  
 ![Pop-up com posicionamento Left](./media/popup-placement-behavior/popup-placement-left.png "O posicionamento é deixado.")   
  
 ![Pop-up com posicionamento Mouse](./media/popup-placement-behavior/popup-placement-mouse.png "O posicionamento é o mouse.")  
  
 ![Pop-up com posicionamento MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "O posicionamento é MousePoint.")  
  
 ![Pop-up com posicionamento Relative ou RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "O posicionamento é relativo ou RelativePoint.")    
  
 ![Pop-up com posicionamento Right](./media/popup-placement-behavior/popup-placement-right.png "O posicionamento está certo.")    
  
 ![Pop-up com posicionamento Top](./media/popup-placement-behavior/popup-placement-top.png "A colocação é superior.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Quando o pop-up encontra a borda da tela  
 Por motivos de segurança, uma <xref:System.Windows.Controls.Primitives.Popup> não pode ser ocultada pela borda de uma tela. Uma das três ações a seguir ocorre quando o <xref:System.Windows.Controls.Primitives.Popup> encontra uma borda de tela:  
  
- O Popup se realinha ao longo da borda da tela que obscureceria a <xref:System.Windows.Controls.Primitives.Popup>.  
  
- O pop-up usa um ponto de alinhamento do pop-up diferente.  
  
- O pop-up usa uma origem do destino e um ponto de alinhamento do pop-up diferentes.  
  
 Essas opções são descritas detalhadamente mais adiante nesta seção.  
  
 O comportamento do <xref:System.Windows.Controls.Primitives.Popup> quando ele encontra uma borda de tela depende do valor da propriedade <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> e da borda da tela que o Popup encontra. A tabela a seguir resume o comportamento quando o <xref:System.Windows.Controls.Primitives.Popup> encontra uma borda de tela para cada valor de <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
|PlacementMode|Borda superior|Borda inferior|Borda esquerda|Borda direita|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up é alterado para o canto inferior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|O ponto de alinhamento pop-up é alterado para o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alinha-se com a borda superior.|A origem de destino muda para o canto superior esquerdo da área de destino e o ponto de alinhamento Popup muda para o canto inferior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|A origem de destino muda para o canto superior direito da área de destino e o ponto de alinhamento Popup muda para o canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alinha-se com a borda superior.|A origem de destino muda para o canto superior esquerdo da área de destino (os limites do ponteiro do mouse) e o ponto de alinhamento pop-up é alterado para o canto inferior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up é alterado para o canto inferior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up é alterado para o canto inferior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|A origem de destino muda para o canto superior esquerdo da área de destino e o ponto de alinhamento Popup muda para o canto superior direito da <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|A origem de destino muda para o canto inferior esquerdo da área de destino e o ponto de alinhamento Popup muda para o canto superior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>. Em vigor, isso é o mesmo que quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alinhamento com a borda da tela  
 Um <xref:System.Windows.Controls.Primitives.Popup> pode se alinhar à borda da tela reposicionando-se, de modo que todo o <xref:System.Windows.Controls.Primitives.Popup> fique visível na tela.  Quando isso ocorre, a distância entre a origem de destino e o ponto de alinhamento pop-up pode diferir dos valores de <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center> ou <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, o <xref:System.Windows.Controls.Primitives.Popup> se alinha a cada borda da tela.  Por exemplo, suponha que um <xref:System.Windows.Controls.Primitives.Popup> tenha <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> definido como <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> definido como 100.  Se a borda inferior da tela ocultar todo ou parte da <xref:System.Windows.Controls.Primitives.Popup>, a <xref:System.Windows.Controls.Primitives.Popup> será reposicionada na borda inferior da tela e a distância vertical entre a origem de destino e o ponto de alinhamento pop-up será menor que 100. A ilustração a seguir demonstra isso.  
  
 ![Pop-up que se alinha com a borda da tela](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "O Popup se alinha à borda da tela.")    
  
### <a name="changing-the-popup-alignment-point"></a>Alterando o ponto de alinhamento do pop-up  
 Se <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> for <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> ou <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, o ponto de alinhamento pop-up será alterado quando o pop-up encontrar a borda inferior ou direita da tela.  
  
 A ilustração a seguir demonstra que, quando a borda de tela inferior oculta todo ou parte da <xref:System.Windows.Controls.Primitives.Popup>, o ponto de alinhamento popup é o canto inferior esquerdo da <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup encontra a borda inferior da tela e altera o ponto de alinhamento pop-up.")  

 A ilustração a seguir demonstra que, quando a <xref:System.Windows.Controls.Primitives.Popup> é ocultada pela borda direita da tela, o ponto de alinhamento popup é o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento do pop-up devido à borda da tela](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup encontra a borda direita da tela e altera o ponto de alinhamento Popup.")    
  
 Se o <xref:System.Windows.Controls.Primitives.Popup> encontrar as bordas inferior e direita da tela, o ponto de alinhamento pop-up será o canto inferior direito da <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Mudando a origem do destino e o ponto de alinhamento do pop-up  
 Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> for <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right> ou <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, a origem de destino e o ponto de alinhamento de Popup serão alterados se uma determinada borda de tela for encontrada.  A borda da tela que faz com que a posição seja alterada depende do valor de <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
 A ilustração a seguir demonstra que, quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> e o <xref:System.Windows.Controls.Primitives.Popup> encontra a borda de tela inferior, a origem de destino é o canto superior esquerdo da área de destino e o ponto de alinhamento pop-up é o canto inferior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "O posicionamento é inferior e o Popup encontra a borda inferior da tela.")    
  
 A ilustração a seguir demonstra que, quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Left> e a <xref:System.Windows.Controls.Primitives.Popup> encontra a borda da tela à esquerda, a origem de destino é o canto superior direito da área de destino e o ponto de alinhamento popup é o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda esquerda da tela](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "O posicionamento é deixado e o Popup encontra a borda esquerda da tela.")  
  
 A ilustração a seguir demonstra que, quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Right> e o <xref:System.Windows.Controls.Primitives.Popup> encontra a borda de tela direita, a origem de destino é o canto superior esquerdo da área de destino e o ponto de alinhamento pop-up é o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda direita da tela](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "O posicionamento está correto e o Popup encontra a borda direita da tela.")  

 A ilustração a seguir demonstra que, quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Top> e o <xref:System.Windows.Controls.Primitives.Popup> encontra a borda de tela superior, a origem de destino é o canto inferior esquerdo da área de destino e o ponto de alinhamento pop-up é o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda superior da tela](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "O posicionamento é superior e o Popup encontra a borda superior da tela.")  
  
 A ilustração a seguir demonstra que, quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> é <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> e o <xref:System.Windows.Controls.Primitives.Popup> encontra a borda de tela inferior, a origem de destino é o canto superior esquerdo da área de destino (os limites do ponteiro do mouse) e o ponto de alinhamento popup é o inferior esquerdo canto do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido ao mouse perto da borda da tela](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "O posicionamento é o mouse e o Popup encontra a borda inferior da tela.")    
  
### <a name="customizing-popup-placement"></a>Personalizando o posicionamento do pop-up  
 Você pode personalizar a origem de destino e o ponto de alinhamento pop-up definindo a propriedade <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Em seguida, defina um delegado <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> que retorna um conjunto de possíveis pontos de posicionamento e eixos primários (em ordem de preferência) para o <xref:System.Windows.Controls.Primitives.Popup>. O ponto que mostra a maior parte do <xref:System.Windows.Controls.Primitives.Popup> está selecionado.  A posição da <xref:System.Windows.Controls.Primitives.Popup> será ajustada automaticamente se a <xref:System.Windows.Controls.Primitives.Popup> estiver oculta pela borda da tela. Para ver um exemplo, consulte [Especificar uma posição de pop-up personalizada](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Consulte também

- [Amostra de posicionamento do pop-up](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
