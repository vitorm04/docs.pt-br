---
title: Comportamento de posicionamento do pop-up
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 1c377e62ffd334638031baee4d4831ac5a31acf3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243252"
---
# <a name="popup-placement-behavior"></a>Comportamento de posicionamento do pop-up
Um <xref:System.Windows.Controls.Primitives.Popup> controle exibe o conteúdo em uma janela separada que flutua sobre um aplicativo. Você pode especificar <xref:System.Windows.Controls.Primitives.Popup> a posição de um parente para um <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>controle, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>o mouse ou a tela usando as <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriedades e <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>propriedades.  Essas propriedades trabalham juntas para lhe dar flexibilidade <xref:System.Windows.Controls.Primitives.Popup>na especificação da posição do .  
  
> [!NOTE]
> As <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu> classes também definem essas cinco propriedades e se comportam de forma semelhante.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Posicionamento do pop-up  
 A colocação <xref:System.Windows.Controls.Primitives.Popup> de um <xref:System.Windows.UIElement> pode ser relativa a uma ou a toda a tela.  O exemplo a <xref:System.Windows.Controls.Primitives.Popup> seguir cria quatro <xref:System.Windows.UIElement>controles relativos a a — neste caso, uma imagem. Todos os <xref:System.Windows.Controls.Primitives.Popup> controles têm <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a `image1`propriedade definida, mas cada <xref:System.Windows.Controls.Primitives.Popup> um tem um valor diferente para a propriedade de colocação.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 A ilustração a seguir <xref:System.Windows.Controls.Primitives.Popup> mostra a imagem e os controles  
  
 ![Imagem com quatro controles de pop-up](./media/popup-placement-behavior/popup-placement-intro.png "Imagem com quatro popups")
  
 Este exemplo simples demonstra <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> como <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> definir as propriedades <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>e <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriedades, mas usando o , <xref:System.Windows.Controls.Primitives.Popup> e propriedades, você tem ainda mais controle sobre onde o está posicionado.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definições de termos: a anatomia de um pop-up  
 Os seguintes termos são úteis <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>para <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>entender <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> como as <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>propriedades se relacionam entre si e:  
  
- Objeto de destino  
  
- Área de destino  
  
- Origem do destino  
  
- Ponto de alinhamento do pop-up  
  
 Estes termos fornecem uma maneira conveniente de <xref:System.Windows.Controls.Primitives.Popup> se referir a vários aspectos do e do controle com o que está associado.  
  
### <a name="target-object"></a>Objeto de Destino  
 O *objeto alvo* é <xref:System.Windows.Controls.Primitives.Popup> o elemento com o que está associado. Se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a propriedade estiver definida, ela especificar o objeto-alvo.  Se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> não estiver definido <xref:System.Windows.Controls.Primitives.Popup> e tiver um pai, o pai será o objeto-alvo.  Se não <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> houver valor e nenhum pai, não <xref:System.Windows.Controls.Primitives.Popup> há objeto de destino, e o é posicionado em relação à tela.  
  
 O exemplo a <xref:System.Windows.Controls.Primitives.Popup> seguir cria um <xref:System.Windows.Controls.Canvas>que é o filho de um .  O exemplo não <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> define a <xref:System.Windows.Controls.Primitives.Popup>propriedade no . O valor <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> padrão <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>para é <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.Canvas>então o aparece abaixo do .  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 A ilustração a <xref:System.Windows.Controls.Primitives.Popup> seguir mostra que <xref:System.Windows.Controls.Canvas>o está posicionado em relação ao .  
  
 ![Controle de pop-up sem PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Popup sem PlacementTarget.")  

 O exemplo a <xref:System.Windows.Controls.Primitives.Popup> seguir cria um <xref:System.Windows.Controls.Canvas>que é <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> o filho `ellipse1`de um , mas <xref:System.Windows.Shapes.Ellipse>desta vez o é definido para , de modo que o pop-up aparece abaixo do .  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 A ilustração a <xref:System.Windows.Controls.Primitives.Popup> seguir mostra que <xref:System.Windows.Shapes.Ellipse>o está posicionado em relação ao .  
  
 ![Pop-up posicionado em relação a uma elipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Pop-up com PlacementTarget")
  
> [!NOTE]
> Para <xref:System.Windows.Controls.ToolTip>, o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> valor <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>padrão de é .  Para <xref:System.Windows.Controls.ContextMenu>, o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> valor <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>padrão de é . Esses valores são explicados posteriormente, em “Como as propriedades funcionam juntas”.  
  
### <a name="target-area"></a>Área de destino  
 A *área alvo* é a área <xref:System.Windows.Controls.Primitives.Popup> na tela a que é em relação. Nos exemplos anteriores, <xref:System.Windows.Controls.Primitives.Popup> o está alinhado com os limites do objeto-alvo, mas em alguns casos, o <xref:System.Windows.Controls.Primitives.Popup> está alinhado a outros limites, mesmo que tenha <xref:System.Windows.Controls.Primitives.Popup> um objeto de destino.  Se <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> a propriedade estiver definida, a área de destino será diferente dos limites do objeto-alvo.  
  
 O exemplo a <xref:System.Windows.Controls.Canvas> seguir cria dois <xref:System.Windows.Shapes.Rectangle> objetos, cada um contendo um e um <xref:System.Windows.Controls.Primitives.Popup>.  Em ambos os casos, <xref:System.Windows.Controls.Primitives.Popup> o <xref:System.Windows.Controls.Canvas>objeto-alvo para o é o . O <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas> primeiro tem <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> o conjunto, <xref:System.Windows.Rect.X%2A> <xref:System.Windows.Rect.Y%2A>com <xref:System.Windows.Rect.Width%2A>suas <xref:System.Windows.Rect.Height%2A> propriedades fixadas em 50, 50, 50 e 100, respectivamente. O <xref:System.Windows.Controls.Primitives.Popup> segundo <xref:System.Windows.Controls.Canvas> não tem <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> o conjunto.  Como resultado, o <xref:System.Windows.Controls.Primitives.Popup> primeiro está <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> posicionado abaixo <xref:System.Windows.Controls.Primitives.Popup> do e <xref:System.Windows.Controls.Canvas>o segundo está posicionado abaixo do . Cada <xref:System.Windows.Controls.Canvas> um <xref:System.Windows.Shapes.Rectangle> também contém um que <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> tem os <xref:System.Windows.Controls.Primitives.Popup>mesmos limites do primeiro .  Observe que <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> o não cria um elemento visível na aplicação; o exemplo <xref:System.Windows.Shapes.Rectangle> cria um <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>para representar o .  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Pop-up com e sem PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Popup com e sem PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Origem do destino e ponto de alinhamento do pop-up  
 A *origem do destino* e o *ponto de alinhamento do pop-up* são pontos de referência na área de destino e no pop-up, respectivamente, usados para posicionamento. Você pode <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> usar <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> as propriedades e para compensar o pop-up da área de destino.  Os <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> e são relativos à origem do alvo e ao ponto de alinhamento pop-up. O valor <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> da propriedade determina onde a origem alvo e o ponto de alinhamento popup estão localizados.  
  
 O exemplo a <xref:System.Windows.Controls.Primitives.Popup> seguir <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> cria <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> a e define as propriedades e as propriedades como 20.  A <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade é <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> definida como (o padrão), de modo que a origem alvo é o canto inferior esquerdo <xref:System.Windows.Controls.Primitives.Popup>da área alvo e o ponto de alinhamento popup é o canto superior esquerdo do .  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 A ilustração a seguir mostra o resultado do exemplo anterior.  
  
 ![Posicionamento do pop-up com ponto de alinhamento da origem do destino](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Popup com HorizontalOffset e VerticalOffset.")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Como as propriedades trabalham juntas  
 Os valores <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, e precisam ser considerados juntos para descobrir a área alvo correta, a origem do alvo e o ponto de alinhamento popup.  Por exemplo, se <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> o <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>valor for , não <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> há objeto de destino, o é ignorado e a área de destino é os limites do ponteiro do mouse. Por outro lado, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>se <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> for, o pai determina <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> o objeto alvo e determina a área de destino.  
  
 A tabela a seguir descreve o objeto alvo, a área de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> destino, a origem do destino e o ponto de alinhamento popup e indica se e <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> são usados para cada <xref:System.Windows.Controls.Primitives.PlacementMode> valor de enumeração.  
  
|PlacementMode|Objeto de destino|Área de destino|Origem do destino|Ponto de alinhamento do pop-up|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|A tela, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ou se está configurada.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo à tela.|O canto superior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|A tela, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ou se está configurada.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo à tela.|O canto superior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|O canto inferior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|O centro da área de destino.|O centro <xref:System.Windows.Controls.Primitives.Popup>do.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definido pelo <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|O canto superior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>direito do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é ignorado.|O canto inferior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Não aplicável. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> é ignorado.|Os limites do ponteiro do mouse. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é ignorado.|O canto superior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|O canto superior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|O canto superior esquerdo da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|O canto superior direito da área de destino.|O canto superior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou pai.|O objeto-alvo, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se estiver definido.  O <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> é relativo ao objeto alvo.|O canto superior esquerdo da área de destino.|O canto inferior <xref:System.Windows.Controls.Primitives.Popup>esquerdo do.|  
  
 As ilustrações a <xref:System.Windows.Controls.Primitives.Popup>seguir mostram o ponto de alinhamento , <xref:System.Windows.Controls.Primitives.PlacementMode> área alvo, origem alvo e popup para cada valor. Em cada figura, a área alvo <xref:System.Windows.Controls.Primitives.Popup> é amarela, e a é azul.  
  
 ![Pop-up com posicionamento Absolute ou AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "A colocação é Absolute ou AbsolutePoint.")
  
 ![Pop-up com posicionamento Bottom](./media/popup-placement-behavior/popup-placement-bottom.png "A colocação é inferior.")
  
 ![Pop-up com posicionamento Center](./media/popup-placement-behavior/popup-placement-center.png "A colocação é no Centro.")
  
 ![Pop-up com posicionamento Left](./media/popup-placement-behavior/popup-placement-left.png "A colocação é à esquerda.")
  
 ![Pop-up com posicionamento Mouse](./media/popup-placement-behavior/popup-placement-mouse.png "A colocação é mouse.")  
  
 ![Pop-up com posicionamento MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "A colocação é MousePoint.")  
  
 ![Pop-up com posicionamento Relative ou RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "A colocação é relativa ou relativapoint.")
  
 ![Pop-up com posicionamento Right](./media/popup-placement-behavior/popup-placement-right.png "A colocação é certa.")
  
 ![Pop-up com posicionamento Top](./media/popup-placement-behavior/popup-placement-top.png "A colocação é top.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Quando o pop-up encontra a borda da tela  
 Por razões <xref:System.Windows.Controls.Primitives.Popup> de segurança, não pode ser escondido pela borda de uma tela. Uma das três coisas a <xref:System.Windows.Controls.Primitives.Popup> seguir acontece quando o encontro é uma borda de tela:  
  
- O popup se realinha ao longo da <xref:System.Windows.Controls.Primitives.Popup>borda da tela que obscureceria o .  
  
- O pop-up usa um ponto de alinhamento do pop-up diferente.  
  
- O pop-up usa uma origem do destino e um ponto de alinhamento do pop-up diferentes.  
  
 Essas opções são descritas detalhadamente mais adiante nesta seção.  
  
 O comportamento <xref:System.Windows.Controls.Primitives.Popup> do quando encontra uma borda de tela <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> depende do valor da propriedade e qual tela a borda que o popup encontra. A tabela a seguir resume <xref:System.Windows.Controls.Primitives.Popup> o comportamento quando <xref:System.Windows.Controls.Primitives.PlacementMode> encontra uma borda de tela para cada valor.  
  
|PlacementMode|Borda superior|Borda inferior|Borda esquerda|Borda direita|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up muda <xref:System.Windows.Controls.Primitives.Popup>para o canto inferior esquerdo do .|Alinha-se com a borda esquerda.|O ponto de alinhamento pop-up muda <xref:System.Windows.Controls.Primitives.Popup>para o canto superior direito do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alinha-se com a borda superior.|A origem do alvo muda para o canto superior esquerdo da área alvo e <xref:System.Windows.Controls.Primitives.Popup>o ponto de alinhamento popup muda para o canto inferior esquerdo do .|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|A origem do alvo muda para o canto superior direito da área alvo e <xref:System.Windows.Controls.Primitives.Popup>o ponto de alinhamento popup muda para o canto superior esquerdo do .|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alinha-se com a borda superior.|A origem do destino muda para o canto superior esquerdo da área alvo (os limites do ponteiro do <xref:System.Windows.Controls.Primitives.Popup>mouse) e o ponto de alinhamento popup muda para o canto inferior esquerdo do .|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up muda <xref:System.Windows.Controls.Primitives.Popup>para o canto inferior esquerdo do .|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alinha-se com a borda superior.|O ponto de alinhamento pop-up muda <xref:System.Windows.Controls.Primitives.Popup>para o canto inferior esquerdo do .|Alinha-se com a borda esquerda.|O ponto de alinhamento do pop-up muda para o canto superior direito do pop-up.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alinha-se com a borda superior.|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|A origem do alvo muda para o canto superior esquerdo da área alvo e <xref:System.Windows.Controls.Primitives.Popup>o ponto de alinhamento popup muda para o canto superior direito do .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|A origem do alvo muda para o canto inferior esquerdo da área alvo e <xref:System.Windows.Controls.Primitives.Popup>o ponto de alinhamento popup muda para o canto superior esquerdo do . Na verdade, isso é <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> o <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>mesmo que quando é .|Alinha-se com a borda inferior.|Alinha-se com a borda esquerda.|Alinha-se com a borda direita.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alinhamento com a borda da tela  
 A <xref:System.Windows.Controls.Primitives.Popup> pode se alinhar à borda da tela reposicionando-se para que o todo <xref:System.Windows.Controls.Primitives.Popup> seja visível na tela.  Quando isso ocorre, a distância entre a origem alvo e <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> o <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>ponto de alinhamento popup pode diferir dos valores de e . Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>é <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>ou <xref:System.Windows.Controls.Primitives.Popup> , a linha-se a cada borda da tela.  Por exemplo, suponha <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> que <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup> tenha <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> definido e definido como 100.  Se a borda inferior da tela ocultar <xref:System.Windows.Controls.Primitives.Popup>tudo <xref:System.Windows.Controls.Primitives.Popup> ou parte do , a reposição ao longo da borda inferior da tela e a distância vertical entre a origem do alvo e o ponto de alinhamento pop-up é menor que 100. A ilustração a seguir demonstra isso.  
  
 ![Pop-up que se alinha com a borda da tela](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Popup se alinha à borda da tela.")
  
### <a name="changing-the-popup-alignment-point"></a>Alterando o ponto de alinhamento do pop-up  
 Se <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>for, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>ou , o ponto de alinhamento pop-up muda quando o pop-up encontra a borda inferior ou direita da tela.  
  
 A ilustração a seguir demonstra que quando a <xref:System.Windows.Controls.Primitives.Popup>borda inferior da tela oculta toda ou <xref:System.Windows.Controls.Primitives.Popup>parte do ponto de alinhamento popup é o canto inferior esquerdo do .  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup encontra a borda inferior da tela e altera o ponto de alinhamento popup.")  

 A ilustração a <xref:System.Windows.Controls.Primitives.Popup> seguir demonstra que quando o está escondido pela borda da tela <xref:System.Windows.Controls.Primitives.Popup>direita, o ponto de alinhamento pop-up é o canto superior direito do .  
  
 ![Novo ponto de alinhamento do pop-up devido à borda da tela](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup encontra a borda direita da tela e altera o ponto de alinhamento popup.")
  
 Se <xref:System.Windows.Controls.Primitives.Popup> encontrar as bordas da tela inferior e direita, o ponto de <xref:System.Windows.Controls.Primitives.Popup>alinhamento popup é o canto inferior direito do .  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Mudando a origem do destino e o ponto de alinhamento do pop-up  
 Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>é <xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, , ou , a origem do destino e ponto de alinhamento pop-up mudar se uma determinada borda de tela é encontrada.  A borda da tela que faz com <xref:System.Windows.Controls.Primitives.PlacementMode> que a posição mude depende do valor.  
  
 A ilustração a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> seguir <xref:System.Windows.Controls.Primitives.Popup> demonstra que quando é e a borda da tela inferior, a origem alvo é o canto <xref:System.Windows.Controls.Primitives.Popup>superior esquerdo da área alvo e o ponto de alinhamento popup é o canto inferior esquerdo do .  
  
 ![Novo ponto de alinhamento devido à borda inferior da tela](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "A colocação é Inferior e o pop-up encontra a borda inferior da tela.")
  
 A ilustração a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> seguir <xref:System.Windows.Controls.Primitives.Popup> demonstra que quando é e os encontros na borda da tela esquerda, a origem do alvo <xref:System.Windows.Controls.Primitives.Popup>é o canto superior direito da área alvo e o ponto de alinhamento popup é o canto superior esquerdo do .  
  
 ![Novo ponto de alinhamento devido à borda esquerda da tela](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "A colocação é à esquerda e o pop-up encontra a borda esquerda da tela.")  
  
 A ilustração a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> seguir <xref:System.Windows.Controls.Primitives.Popup> demonstra que quando é e a borda da tela direita, a origem do alvo é o canto superior esquerdo da área alvo e o ponto de alinhamento popup é o canto superior direito do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Novo ponto de alinhamento devido à borda direita da tela](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "A colocação é certa e o pop-up encontra a borda direita da tela.")  

 A ilustração a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> seguir <xref:System.Windows.Controls.Primitives.Popup> demonstra que quando é e a borda da tela superior, a origem alvo é o canto <xref:System.Windows.Controls.Primitives.Popup>inferior esquerdo da área alvo e o ponto de alinhamento popup é o canto superior esquerdo do .  
  
 ![Novo ponto de alinhamento devido à borda superior da tela](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "A colocação é Top e o pop-up encontra a borda superior da tela.")  
  
 A ilustração a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> seguir <xref:System.Windows.Controls.Primitives.Popup> demonstra que quando é e a borda da tela inferior, a origem alvo é o canto superior esquerdo da área alvo <xref:System.Windows.Controls.Primitives.Popup>(os limites do ponteiro do mouse) e o ponto de alinhamento popup é o canto inferior esquerdo do .  
  
 ![Novo ponto de alinhamento devido ao mouse perto da borda da tela](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "A colocação é mouse e o pop-up encontra a borda inferior da tela.")
  
### <a name="customizing-popup-placement"></a>Personalizando o posicionamento do pop-up  
 Você pode personalizar a origem do destino <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> e <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>o ponto de alinhamento pop-up definindo a propriedade para . Em seguida, defina um <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado que devolva um conjunto de <xref:System.Windows.Controls.Primitives.Popup>possíveis pontos de colocação e eixos primários (por ordem de preferência) para o . O ponto que mostra a <xref:System.Windows.Controls.Primitives.Popup> maior parte do é selecionado.  A posição <xref:System.Windows.Controls.Primitives.Popup> do é automaticamente <xref:System.Windows.Controls.Primitives.Popup> ajustada se estiver escondida pela borda da tela. Para ver um exemplo, consulte [Especificar uma posição de pop-up personalizada](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Confira também

- [Amostra de posicionamento do pop-up](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
