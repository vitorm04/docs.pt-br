---
title: Configurações do Registro de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: d6a121e2a95ce4005b43937f83c6c74ec7d8f1c1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43473994"
---
# <a name="cleartype-registry-settings"></a>Configurações do Registro de ClearType
Este tópico fornece uma visão geral de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] configurações do registro que são usadas pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Visão geral da tecnologia  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos que renderizam texto para um dispositivo de vídeo usam [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] recursos para fornecer uma experiência aprimorada de leitura. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] é uma tecnologia de software desenvolvida por [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)], que melhora a legibilidade do texto em monitores LCD existentes, como telas de notebook, telas de Pocket PC e monitores de tela plana. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funciona ao acessar os elementos individuais da listra de cores vertical em cada pixel de uma tela LCD. Para obter mais informações sobre [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], consulte [visão geral de ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 Texto que é processado com [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] pode parecer significativamente diferente quando exibido em vários dispositivos de vídeo. Por exemplo, um pequeno número de monitores de implementa os elementos da faixa de cor na ordem azul, verde, vermelho, em vez do mais comum vermelho, verde, azul ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) ordem.  
  
 Texto que é processado com [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] também pode parecer significativamente diferente quando visualizado por pessoas com variados níveis de sensibilidade de cor. Algumas pessoas podem detectar pequenas diferenças nas cores melhor do que outras.  
  
 Em cada um desses casos, [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] recursos precisam ser modificados para fornecer a melhor experiência de leitura para cada indivíduo.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Configurações do registro  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Especifica quatro configurações do registro para controlar [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] recursos:  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nível de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]|Descreve o nível de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] clareza de cor.|  
|Nível de gama|Descreve o nível do componente de cor do pixel para um dispositivo de vídeo.|  
|Estrutura de Pixel|Descreve a disposição dos pixels para um dispositivo de vídeo.|  
|Nível de contraste do texto|Descreve o nível de contraste para o texto exibido.|  
  
 Essas configurações podem ser acessadas por um utilitário de configuração externo que sabe como referenciar o identificado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] as configurações do registro. Essas configurações também podem ser criadas ou modificadas acessando os valores diretamente usando o [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Editor do Registro.  
  
 Se o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] configurações de registro não estiverem definidas (que é o estado padrão), o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consultas de aplicativo a [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] informações de parâmetros de sistema para as configurações de suavização de fonte.  
  
> [!NOTE]
>  Para obter informações sobre a enumeração de nomes de dispositivo de vídeo, consulte a `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] função.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Nível de ClearType  
 O [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nível permite que você ajuste a renderização de texto com base na sensibilidade de cor e percepção de um indivíduo. Para algumas pessoas, a renderização de texto que usa [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em seu nível mais alto não produz a melhor experiência de leitura.  
  
 O [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nível é um valor inteiro que varia de 0 a 100. O nível padrão é 100, o que significa [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] usa a capacidade máxima dos elementos de faixa de cor do dispositivo de vídeo. No entanto, um [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nível 0 renderiza o texto como escala de cinza. Definindo o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nível em algum lugar entre 0 e 100, você pode criar um nível intermediário que é adequado à sensibilidade de cor de um indivíduo.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 O local de configuração do registro para o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nível é uma configuração de usuário individual que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de vídeo para um usuário, um `ClearTypeLevel` valor DWORD é definido. Captura de tela a seguir mostra a configuração do Editor do registro para o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nível.  
  
 ![Configurações de ClearType no Editor do Registro](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos renderizam texto em um entre dois modos, com e sem [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Quando o texto é renderizado sem [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], ele é conhecido como renderização em escala de cinza.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Nível de Gama  
 O nível de fama se refere à relação não linear entre o valor de um pixel e a luminância. A configuração do nível de gama deve corresponder às características físicas do dispositivo de vídeo. Caso contrário, podem ocorrer distorções na saída renderizada. Por exemplo, o teste pode aparecer muito largo ou muito estreito ou extremidades coloridas podem aparecer nas bordas dos troncos verticais dos glifos.  
  
 O nível de gama é um valor inteiro que varia de 1000 a 2200. O nível padrão é 1900.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para o nível de gama é uma configuração do computador local que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de vídeo para um usuário, um `GammaLevel` valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para o nível de gama.  
  
 ![Configurações de ClearType no Editor do Registro](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Estrutura de pixel  
 A estrutura de pixel descreve o tipo de pixels que compõem um dispositivo de vídeo. A estrutura de pixel é definida como um de três tipos:  
  
|Tipo|Valor|Descrição|  
|----------|-----------|-----------------|  
|Plano|0|O dispositivo de vídeo não tem uma estrutura de pixel. Isso significa que as fontes de luz para cada cor são distribuídas igualmente na área de pixel — isso é conhecido como renderização em escala de cinza. É assim que um dispositivo de vídeo padrão funciona. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nunca é aplicado ao texto renderizado.|  
|RGB|1|O dispositivo de vídeo tem pixels que consistem em três faixas na seguinte ordem: vermelho, verde e azul. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] é aplicado ao texto renderizado.|  
|BGR|2|O dispositivo de vídeo tem pixels que consistem em três faixas na seguinte ordem: azul, verde e vermelho. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] é aplicado ao texto renderizado. Observe como a ordem é invertida com relação ao tipo RGB.|  
  
 A estrutura de pixel corresponde a um valor inteiro que vai de 0 a 2. O nível padrão é 0, que representa uma estrutura de pixel plana.  
  
> [!NOTE]
>  Para obter informações sobre a enumeração de nomes de dispositivo de vídeo, consulte a `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] função.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para a estrutura de pixel é uma configuração do computador local que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de vídeo para um usuário, um `PixelStructure` valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para a estrutura de pixel.  
  
 ![Configurações de ClearType no Editor do Registro](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Nível de Contraste do Texto  
 O nível de contraste do texto permite que você ajuste a renderização do texto com base nas larguras dos troncos dos glifos. O nível de contraste do texto é um valor inteiro que varia de 0 a 6 — quanto maior o valor inteiro, mais largo o tronco. O nível padrão é 1.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para o nível de contraste do texto é uma configuração individual do usuário que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de vídeo para um usuário, um `TextContrastLevel` valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para o nível de contraste do texto.  
  
 ![Configurações de ClearType no Editor do Registro](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [Suavização de ClearType](/windows/desktop/gdi/cleartype-antialiasing)
