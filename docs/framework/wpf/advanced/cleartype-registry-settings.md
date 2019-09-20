---
title: Configurações do Registro de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: ab6ff2ba6e0f3f1ea9e34de80b67276a990bc83b
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151842"
---
# <a name="cleartype-registry-settings"></a>Configurações do Registro de ClearType
Este tópico fornece uma visão geral das configurações do registro do Microsoft ClearType que são usadas por aplicativos do WPF.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Visão geral da tecnologia  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]os aplicativos que renderizam texto para um dispositivo de vídeo usam recursos de ClearType para fornecer uma experiência de leitura aprimorada. O ClearType é uma tecnologia de software desenvolvida pela Microsoft que melhora a legibilidade do texto em LCDs existentes (monitores Liquid Crystal), como telas de laptops, telas de Pocket PC e monitores de tela plana. O ClearType funciona acessando os elementos da faixa de cor vertical individual em cada pixel de uma tela de LCD. Para obter mais informações sobre ClearType, consulte [visão geral de ClearType](cleartype-overview.md).  
  
 O texto que é processado com ClearType pode parecer significativamente diferente quando exibido em vários dispositivos de vídeo. Por exemplo, um pequeno número de monitores implementam os elementos de faixas de cores na ordem azul, verde e vermelha em vez da ordem mais comum de vermelho, verde, azul (RGB).  
  
 O texto que é processado com ClearType também pode ser significativamente diferente quando exibido por indivíduos com níveis variados de sensibilidade de cores. Algumas pessoas podem detectar pequenas diferenças nas cores melhor do que outras.  
  
 Em cada um desses casos, os recursos de ClearType precisam ser modificados para fornecer a melhor experiência de leitura para cada indivíduo.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Configurações do registro  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Especifica quatro configurações do registro para controlar os recursos de ClearType:  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nível de ClearType|Descreve o nível de clareza da cor ClearType.|  
|Nível de gama|Descreve o nível do componente de cor do pixel para um dispositivo de vídeo.|  
|Estrutura de Pixel|Descreve a disposição dos pixels para um dispositivo de vídeo.|  
|Nível de contraste do texto|Descreve o nível de contraste para o texto exibido.|  
  
 Essas configurações podem ser acessadas por um utilitário de configuração externo que sabe como referenciar as configurações de registro de ClearType identificadas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Essas configurações também podem ser criadas ou modificadas acessando os valores diretamente usando o editor do registro do Windows.  
  
 Se as [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]configurações do registro ClearType não estiverem definidas (que é o estado padrão), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o aplicativo consultará as informações de parâmetros do sistema do Windows para configurações de suavização de fontes.  
  
> [!NOTE]
> Para obter informações sobre como enumerar nomes de dispositivos de `SystemParametersInfo` exibição, consulte a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] função.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Nível de ClearType  
 O nível ClearType permite que você ajuste a renderização de texto com base na sensibilidade à cor e na percepção de um indivíduo. Para alguns indivíduos, a renderização de texto que usa ClearType em seu nível mais alto não produz a melhor experiência de leitura.  
  
 O nível ClearType é um valor inteiro que varia de 0 a 100. O nível padrão é 100, o que significa que o ClearType usa a capacidade máxima dos elementos de faixa de cor do dispositivo de vídeo. No entanto, um nível ClearType de 0 renderiza o texto como uma escala cinza. Ao definir o nível de ClearType em algum lugar entre 0 e 100, você pode criar um nível intermediário que seja adequado à sensibilidade de cores de um indivíduo.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 O local de configuração do registro para o nível ClearType é uma configuração de usuário individual que corresponde a um nome de dispositivo de exibição específico:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de exibição para um usuário `ClearTypeLevel` , um valor DWORD é definido. A captura de tela a seguir mostra a configuração do editor do registro para o nível ClearType.  
  
 ![Configurações de ClearType no editor do registro.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]os aplicativos renderizam o texto em um dos dois modos, com e sem ClearType. Quando o texto é renderizado sem ClearType, ele é referido como renderização de escala cinza.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Nível de Gama  
 O nível de fama se refere à relação não linear entre o valor de um pixel e a luminância. A configuração do nível de gama deve corresponder às características físicas do dispositivo de vídeo. Caso contrário, podem ocorrer distorções na saída renderizada. Por exemplo, o texto pode parecer muito largo ou muito estreito, ou as margens de cor podem aparecer nas bordas de hastes verticais de glifos.  
  
 O nível de gama é um valor inteiro que varia de 1000 a 2200. O nível padrão é 1900.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para o nível de gama é uma configuração do computador local que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de exibição para um usuário `GammaLevel` , um valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para o nível de gama.  
  
 ![Configurações de nível de gama ClearType no editor do registro](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Estrutura de pixel  
 A estrutura de pixel descreve o tipo de pixels que compõem um dispositivo de vídeo. A estrutura de pixel é definida como um de três tipos:  
  
|Tipo|Valor|Descrição|  
|----------|-----------|-----------------|  
|Plano|0|O dispositivo de vídeo não tem uma estrutura de pixel. Isso significa que as fontes de luz para cada cor são distribuídas igualmente na área de pixel — isso é conhecido como renderização em escala de cinza. É assim que um dispositivo de vídeo padrão funciona. ClearType nunca é aplicado ao texto renderizado.|  
|RGB|1|O dispositivo de vídeo tem pixels que consistem em três faixas na seguinte ordem: vermelho, verde e azul. ClearType é aplicado ao texto renderizado.|  
|BGR|2|O dispositivo de vídeo tem pixels que consistem em três faixas na seguinte ordem: azul, verde e vermelho. ClearType é aplicado ao texto renderizado. Observe como a ordem é invertida com relação ao tipo RGB.|  
  
 A estrutura de pixel corresponde a um valor inteiro que vai de 0 a 2. O nível padrão é 0, que representa uma estrutura de pixel plana.  
  
> [!NOTE]
> Para obter informações sobre como enumerar nomes de dispositivos de `EnumDisplayDevices` exibição, consulte a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] função.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para a estrutura de pixel é uma configuração do computador local que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de exibição para um usuário `PixelStructure` , um valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para a estrutura de pixel.  
  
 ![Configurações de nível de gama ClearType no editor do registro](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Nível de Contraste do Texto  
 O nível de contraste do texto permite que você ajuste a renderização do texto com base nas larguras dos troncos dos glifos. O nível de contraste do texto é um valor inteiro que varia de 0 a 6 — quanto maior o valor inteiro, mais largo o tronco. O nível padrão é 1.  
  
### <a name="registry-setting"></a>Configuração do Registro  
 A localização da configuração do Registro para o nível de contraste do texto é uma configuração individual do usuário que corresponde a um nome de dispositivo de vídeo específico:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Para cada nome de dispositivo de exibição para um usuário `TextContrastLevel` , um valor DWORD é definido. A captura de tela a seguir mostra a configuração do Editor do Registro para o nível de contraste do texto.  
  
 ![Configurações de ClearType no editor do registro.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de ClearType](cleartype-overview.md)
- [Suavização de ClearType](/windows/desktop/gdi/cleartype-antialiasing)
