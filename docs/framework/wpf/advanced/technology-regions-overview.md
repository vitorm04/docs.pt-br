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
ms.openlocfilehash: 0b6ad222737f992da3074770fb5a2bff17860c00
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740298"
---
# <a name="technology-regions-overview"></a>Visão geral das regiões de tecnologia
Se várias tecnologias de apresentação forem usadas em um aplicativo, como WPF, Win32 ou DirectX, elas deverão compartilhar as áreas de renderização em uma janela de nível superior comum. Este tópico descreve problemas que podem influenciar a apresentação e a entrada para seu aplicativo de interoperação do WPF.  
  
## <a name="regions"></a>Regiões  
 Em uma janela de nível superior, você pode conceitualizar que cada HWND que abrange uma das tecnologias de um aplicativo de interoperação tem sua própria região (também chamada de "espaço aéreo"). Cada pixel na janela pertence a exatamente um HWND, que constitui a região daquele HWND. (Estritamente falando, haverá mais de uma região [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se houver mais de um HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mas para os fins desta discussão, suponha que haja apenas um). A região implica que todas as camadas ou outras janelas que tentarem renderizar acima daquele pixel durante o tempo de vida do aplicativo devem ser parte da mesma tecnologia de nível de renderização. A tentativa de renderizar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pixels sobre o Win32 leva a resultados indesejáveis e não é permitida tanto quanto possível por meio das APIs de interoperação.  
  
### <a name="region-examples"></a>Exemplos de região  
 A ilustração a seguir mostra um aplicativo que combina Win32, DirectX e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cada tecnologia usa seu próprio conjunto de pixels separado, sem sobreposição e não tem problemas de região.  
  
 ![Um exemplo de um aplicativo que combina Win32, DirectX e WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Suponha que esse aplicativo usa a posição do ponteiro do mouse para criar uma animação que tenta renderizar sobre qualquer uma dessas três regiões. Não importa qual tecnologia era responsável pela animação em si, essa tecnologia violaria a região das outras duas. A ilustração a seguir mostra uma tentativa de renderizar um círculo do WPF em uma região do Win32.  
  
 ![Uma tentativa de renderizar um círculo do WPF em uma região Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Outra violação ocorrerá se você tenta usar a transparência/combinação alfa entre tecnologias diferentes.  Na ilustração a seguir, a caixa de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] viola as regiões do Win32 e do DirectX. Como os pixels nessa caixa de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são semitransparentes, eles teriam que ser de Propriedade do DirectX e do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o que não é possível.  Portanto, essa é outra violação e não pode ser compilada.  
  
 ![Diagrama mostrando uma caixa do WPF violando as regiões Win32 e DirectX.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 Os três exemplos anteriores usaram regiões retangulares. No entanto, formas diferentes podem ser usadas.  Por exemplo, uma região pode ter um espaço. A ilustração a seguir mostra uma região do Win32 com um buraco retangular. esse é o tamanho das regiões [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e DirectX combinadas.  
  
 ![Diagrama que mostra uma região Win32 com um buraco retangular.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 As regiões também podem ser completamente não retangulares ou qualquer forma describable por um HRGN Win32 (região).  
  
 ![Diagrama que mostra uma região não retangular.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Transparência e janelas de nível superior  
 O Gerenciador de janelas no Windows apenas realmente processa os HWNDs Win32. Portanto, cada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> é um HWND. O <xref:System.Windows.Window> HWND deve obedecer às regras gerais para qualquer HWND. Dentro desse HWND, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] código pode fazer tudo o que a API de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geral dá suporte. Mas, para interações com outros HWNDs na área de trabalho, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deve obedecer às regras de processamento e renderização do Win32.  o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a janelas não retangulares usando APIs do Win32 — HRGNs para janelas não retangulares e janelas em camadas para um alfa por pixel.  
  
 Não há suporte para alfa constante e chaves de cores.  Os recursos de janela em camadas do Win32 variam de acordo com a plataforma.  
  
 As janelas em camadas podem tornar a janela inteira translúcida (semitransparente) ao especificarem um valor alfa para aplicar a cada pixel na janela.  (O Win32 dá suporte a Alpha por pixel, mas isso é muito difícil de usar em programas práticos porque, nesse modo, você precisaria desenhar qualquer HWND filho por conta própria, incluindo caixas de diálogo e listas suspensas).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a HRGNs; no entanto, não há APIs gerenciadas para essa funcionalidade. Você pode usar a invocação de plataforma e <xref:System.Windows.Interop.HwndSource> para chamar as APIs do Win32 relevantes. Para obter mais informações, consulte [Chamando funções nativas do código gerenciado](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 As janelas em camadas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm recursos diferentes em sistemas operacionais distintos. Isso ocorre porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o DirectX para renderizar, e janelas em camadas foram projetadas principalmente para a renderização GDI, não para a renderização do DirectX.  
  
- O WPF dá suporte a janelas em camadas aceleradas por hardware.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não dá suporte para as chaves de cores de transparência porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não pode assegurar a renderização da cor exata solicitada, especialmente quando a renderização é acelerada por hardware.  
  
## <a name="see-also"></a>Veja também

- [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md)
- [Passo a passo: hospedando um relógio do WPF em Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hospedando conteúdo Win32 no WPF](hosting-win32-content-in-wpf.md)
