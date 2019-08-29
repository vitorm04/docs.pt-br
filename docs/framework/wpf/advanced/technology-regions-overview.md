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
ms.openlocfilehash: 4f1489065a70065700d2f8ceb974e66ecceeebd0
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133810"
---
# <a name="technology-regions-overview"></a>Visão geral das regiões de tecnologia
Se várias tecnologias de apresentação forem usadas em um aplicativo, como WPF, Win32 ou DirectX, elas deverão compartilhar as áreas de renderização em uma janela de nível superior comum. Este tópico descreve problemas que podem influenciar a apresentação e a entrada para seu aplicativo de interoperação do WPF.  
  
## <a name="regions"></a>Regiões  
 Em uma janela de nível superior, você pode conceitualizar que cada HWND que abrange uma das tecnologias de um aplicativo de interoperação tem sua própria região (também chamada de "espaço aéreo"). Cada pixel na janela pertence a exatamente um HWND, que constitui a região daquele HWND. (Estritamente falando, haverá mais de uma região [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se houver mais de um HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mas para os fins desta discussão, suponha que haja apenas um). A região implica que todas as camadas ou outras janelas que tentarem renderizar acima daquele pixel durante o tempo de vida do aplicativo devem ser parte da mesma tecnologia de nível de renderização. A tentativa de renderizar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pixels em [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] clientes potenciais para resultados indesejáveis e não é permitida tanto quanto possível por meio das APIs de interoperação.  
  
### <a name="region-examples"></a>Exemplos de região  
 A ilustração a seguir mostra um aplicativo que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]combina, DirectX e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cada tecnologia usa seu próprio conjunto de pixels separado, sem sobreposição e não tem problemas de região.  
  
 ![Um exemplo de um aplicativo que combina Win32, DirectX e WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Suponha que esse aplicativo usa a posição do ponteiro do mouse para criar uma animação que tenta renderizar sobre qualquer uma dessas três regiões. Não importa qual tecnologia era responsável pela animação em si, essa tecnologia violaria a região das outras duas. A ilustração a seguir mostra uma tentativa de renderizar um círculo do WPF em uma região do Win32.  
  
 ![Uma tentativa de renderizar um círculo do WPF em uma região Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Outra violação ocorrerá se você tenta usar a transparência/combinação alfa entre tecnologias diferentes.  Na ilustração a seguir, a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] caixa viola as regiões [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] do e do DirectX. Como os pixels nessa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] caixa são semitransparentes, eles teriam que ser de propriedade de acordo com o DirectX [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]e, o que não é possível.  Portanto, essa é outra violação e não pode ser compilada.  
  
 ![Diagrama mostrando uma caixa do WPF violando as regiões Win32 e DirectX.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Os três exemplos anteriores usaram regiões retangulares. No entanto, formas diferentes podem ser usadas.  Por exemplo, uma região pode ter um espaço. A ilustração a seguir mostra [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uma região com um buraco retangular. esse é o tamanho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] das regiões e do DirectX combinados.  
  
 ![Diagrama que mostra uma região Win32 com um buraco retangular.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 As regiões também podem ser totalmente não retangulares ou ter qualquer forma descrita por um HRGN [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (região).  
  
 ![Diagrama que mostra uma região não retangular.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Transparência e janelas de nível superior  
 O gerenciador de janelas no Windows, de fato, processa apenas HWNDs [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Portanto, cada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> um é um HWND. O <xref:System.Windows.Window> HWND deve obedecer às regras gerais para qualquer HWND. Dentro desse HWND, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o código pode fazer tudo o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que as APIs gerais dão suporte. Mas, para que haja interações com outros HWNDs na área de trabalho, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deve obedecer às regras de processamento e renderização do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dá suporte a janelas não retangulares usando [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] APIs — HRGNs para janelas não retangulares e janelas em camadas para um alfa por pixel.  
  
 Não há suporte para alfa constante e chaves de cores.  Os recursos de janela em camadas do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] variam por plataforma.  
  
 As janelas em camadas podem tornar a janela inteira translúcida (semitransparente) ao especificarem um valor alfa para aplicar a cada pixel na janela.  (na verdade, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dá suporte para a versão alfa por pixel, mas é muito difícil de usá-la em programas práticos porque, neste modo, você precisaria desenhar qualquer HWND filho, inclusive as caixas de diálogo e os menus suspensos).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dá suporte a HRGNs; no entanto, não há APIs gerenciadas para essa funcionalidade. Você pode usar a invocação <xref:System.Windows.Interop.HwndSource> de plataforma e chamar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] as APIs relevantes. Para obter mais informações, consulte [Chamando funções nativas do código gerenciado](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 As janelas em camadas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm recursos diferentes em sistemas operacionais distintos. Isso ocorre porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o usa o DirectX para renderizar, e as janelas em camadas foram projetadas principalmente para a renderização GDI, não para a renderização do DirectX.  
  
- O WPF dá suporte a janelas em camadas aceleradas por hardware.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não dá suporte para as chaves de cores de transparência porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não pode assegurar a renderização da cor exata solicitada, especialmente quando a renderização é acelerada por hardware.  
  
## <a name="see-also"></a>Consulte também

- [Interoperação do WPF e do Win32](wpf-and-win32-interoperation.md)
- [Passo a passo: Hospedando um relógio do WPF no Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hospedando conteúdo Win32 no WPF](hosting-win32-content-in-wpf.md)
