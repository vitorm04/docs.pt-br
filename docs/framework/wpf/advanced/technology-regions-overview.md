---
title: Visão geral das regiões de tecnologia
ms.date: 03/30/2017
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
ms.openlocfilehash: 40ec8d033852bba5cb5ccb0739309cfe988a3ce5
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63808359"
---
# <a name="technology-regions-overview"></a>Visão geral das regiões de tecnologia
Se várias tecnologias de apresentação forem usadas em um aplicativo, como WPF, Win32 ou DirectX, elas deverão compartilhar as áreas de renderização em uma janela de nível superior comum. Este tópico descreve problemas que podem influenciar a apresentação e a entrada para seu aplicativo de interoperação do WPF.  
  
## <a name="regions"></a>Regiões  
 Em uma janela de nível superior, você pode conceitualizar que cada HWND que abrange uma das tecnologias de um aplicativo de interoperação tem sua própria região (também chamada de "espaço aéreo"). Cada pixel na janela pertence a exatamente um HWND, que constitui a região daquele HWND. (Estritamente falando, haverá mais de uma região [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se houver mais de um HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mas para os fins desta discussão, suponha que haja apenas um). A região implica que todas as camadas ou outras janelas que tentarem renderizar acima daquele pixel durante o tempo de vida do aplicativo devem ser parte da mesma tecnologia de nível de renderização. A tentativa de renderizar pixels [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sobre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] leva a resultados indesejáveis e é proibida tanto quanto possível por meio da interoperação [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  
  
### <a name="region-examples"></a>Exemplos de região  
 A ilustração a seguir mostra um aplicativo que combina [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cada tecnologia usa seu próprio conjunto de pixels separado, sem sobreposição e não tem problemas de região.  
  
 ![Um exemplo de um aplicativo que combina o Win32, WPF e o DirectX.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Suponha que esse aplicativo usa a posição do ponteiro do mouse para criar uma animação que tenta renderizar sobre qualquer uma dessas três regiões. Não importa qual tecnologia era responsável pela animação em si, essa tecnologia violaria a região das outras duas. A ilustração a seguir mostra uma tentativa de renderizar um círculo do WPF em uma região do Win32.  
  
 ![Uma tentativa de renderizar um círculo do WPF em uma região do Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Outra violação ocorrerá se você tenta usar a transparência/combinação alfa entre tecnologias diferentes.  Na ilustração a seguir, a caixa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] viola as regiões [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Como os pixels naquela caixa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são semitransparentes, eles teriam de ser propriedade conjunta por [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o que não é possível.  Portanto, essa é outra violação e não pode ser compilada.  
  
 ![Diagrama mostrando uma caixa de WPF violar as regiões do Win32 e do DirectX.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Os três exemplos anteriores usaram regiões retangulares. No entanto, formas diferentes podem ser usadas.  Por exemplo, uma região pode ter um espaço. A ilustração a seguir mostra uma região [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] com um espaço retangular. Esse é o tamanho das regiões [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] combinadas.  
  
 ![Diagrama que mostra uma região do Win32 com um espaço retangular.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 As regiões também podem ser totalmente não retangulares ou ter qualquer forma descrita por um HRGN [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (região).  
  
 ![Diagrama que mostra uma região não retangular.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Transparência e janelas de nível superior  
 O gerenciador de janelas no Windows, de fato, processa apenas HWNDs [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Portanto, cada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> é um HWND. O <xref:System.Windows.Window> HWND deve seguir as regras gerais para qualquer HWND. Neste HWND, o código [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode fazer tudo o que as [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gerais do [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fazem. Mas, para que haja interações com outros HWNDs na área de trabalho, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deve obedecer às regras de processamento e renderização do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte para janelas não retangulares usando as [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] do [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]— HRGNs para janelas não retangulares e janelas em camadas para uma versão alfa por pixel.  
  
 Não há suporte para alfa constante e chaves de cores.  Os recursos de janela em camadas do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] variam por plataforma.  
  
 As janelas em camadas podem tornar a janela inteira translúcida (semitransparente) ao especificarem um valor alfa para aplicar a cada pixel na janela.  (na verdade, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dá suporte para a versão alfa por pixel, mas é muito difícil de usá-la em programas práticos porque, neste modo, você precisaria desenhar qualquer HWND filho, inclusive as caixas de diálogo e os menus suspensos).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte para os HRGNs. No entanto, não há nenhuma [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] gerenciada para essa funcionalidade. Você pode usar a plataforma de invocação e <xref:System.Windows.Interop.HwndSource> para chamar o relevantes [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Para obter mais informações, consulte [Chamando funções nativas do código gerenciado](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 As janelas em camadas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm recursos diferentes em sistemas operacionais distintos. Isso ocorre porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] para renderizar e as janelas em camadas foram projetadas principalmente para a renderização de [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] e não de [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)].  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte para janelas em camadas aceleradas por hardware no [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] e em versões posteriores. As janelas em camadas aceleradas por hardware no [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] exigem suporte de [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)], portanto, os recursos dependem da versão do [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] nesse computador.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não dá suporte para as chaves de cores de transparência porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não pode assegurar a renderização da cor exata solicitada, especialmente quando a renderização é acelerada por hardware.  
  
- Se seu aplicativo for executado no [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)], as janelas em camadas na parte superior das superfícies do [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] cintilarão quando o aplicativo [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] for renderizado.  (A sequência de processamento real consiste no [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] ocultar a janela em camadas e, em seguida, o [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] desenhar e então, o [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] colocar a janela em camadas novamente).  As janelas em camadas não [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também têm essa limitação.  
  
## <a name="see-also"></a>Consulte também

- [Interoperação do WPF e do Win32](wpf-and-win32-interoperation.md)
- [Passo a passo: Hospedando um relógio do WPF no Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hospedando conteúdo Win32 no WPF](hosting-win32-content-in-wpf.md)
