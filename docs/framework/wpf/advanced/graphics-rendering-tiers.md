---
title: Camadas de renderização de gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
ms.openlocfilehash: 05847271cf82739a6a0b609771043c02a7ffc0e9
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291583"
---
# <a name="graphics-rendering-tiers"></a>Camadas de renderização de gráficos
Um nível de renderização define um nível de funcionalidade de hardware de gráficos e de desempenho para um dispositivo que executa um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="graphics_hardware"></a>
## <a name="graphics-hardware"></a>Hardware de gráficos  
 Os recursos do hardware gráfico que mais afetam os níveis de camada de renderização são:  
  
- **RAM de Vídeo** A quantidade de memória de vídeo no hardware gráfico determina o tamanho e o número de buffers que podem ser usados para compor gráficos.  
  
- **Sombreador de Pixel** Um sombreador de pixel é uma função de processamento gráfico que calcula efeitos por pixel. Dependendo da resolução dos gráficos exibidos, pode haver muitos milhões de pixels que precisam ser processados para cada quadro de vídeo.  
  
- **Sombreador de Vértice** O sombreador de vértice é uma função de processamento gráfico que realiza operações matemáticas nos dados de vértice do objeto.  
  
- **Suporte Multitextura** Suporte multitextura refere-se à capacidade de aplicar duas ou mais texturas distintas durante uma operação de mesclagem em um objeto gráfico 3D. O grau de suporte a multitextura é determinado pelo número de unidades de multitextura no hardware gráfico.  
  
<a name="rendering_tier_definitions"></a>
## <a name="rendering-tier-definitions"></a>Definições da camada de processamento  
 Os recursos do hardware gráfico determinam a capacidade de renderização de um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O sistema [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] define três camadas de renderização:  
  
- **Camada de Renderização 0** Sem aceleração de hardware gráfico. Todos os recursos gráficos usam a aceleração de software. O nível da versão DirectX é menor que o da versão 9.0.  
  
- **Camada de Renderização 1** Alguns recursos gráficos usam aceleração de hardware gráfico. O nível de versão directx é maior ou igual à versão 9.0.  
  
- **Camada de Renderização 2** A maioria dos recursos gráficos usa aceleração de hardware gráfico. O nível de versão directx é maior ou igual à versão 9.0.  
  
 A <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> propriedade permite que você recupere o nível de renderização no tempo de execução do aplicativo. Você pode usar o nível de renderização para determinar se o dispositivo dá suporte a certas características aceleradas por hardware. Seu aplicativo então pode adotar diferentes caminhos de código no tempo de execução, dependendo da camada de renderização que tem suporte no dispositivo.  
  
### <a name="rendering-tier-0"></a>Camada de renderização 0  
 Um valor de nível de renderização 0 significa que não há nenhum gráficos aceleração de hardware disponível para o aplicativo no dispositivo. Nesse nível, você deve assumir que todos os gráficos serão renderizados por software sem aceleração de hardware. A funcionalidade deste nível corresponde a uma versão DirectX inferior a 9.0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Camada de Renderização 1 e Camada de Renderização 2
  
> [!NOTE]
> A partir do .NET Framework 4, o nível de renderização 1 foi redefinido para incluir apenas o hardware gráfico que suporta DirectX 9.0 ou superior. O hardware gráfico que suporta DirectX 7 ou 8 agora é definido como renderização de nível 0.  
  
 Um valor da camada de renderização de 1 ou 2 significa que a maioria dos recursos gráficos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usará a aceleração de hardware se os recursos de sistema necessários estiverem disponíveis e não forem esgotados. Isso corresponde a uma versão DirectX maior ou igual a 9.0.  
  
 A tabela a seguir mostra as diferenças nos requisitos de hardware gráfico para renderização do nível 1 e do nível de renderização 2:  
  
|Recurso|Camada 1|Camada 2|  
|-------------|------------|------------|  
|Versão DirectX|Deve ser maior ou igual a 9.0.|Deve ser maior ou igual a 9.0.|  
|Vídeo Ram|Deve ser maior ou igual a 60 MB.|Deve ser maior ou igual a 120 MB.|  
|Sombreador de pixel|O nível da versão deve ser maior ou igual a 2.0.|O nível da versão deve ser maior ou igual a 2.0.|  
|Sombreador de vértica|Não é necessário.|O nível da versão deve ser maior ou igual a 2.0.|  
|Unidades multitexturas|Não é necessário.|Número de unidades deve ser maior ou igual a 4.|  
  
 Os seguintes recursos e capacidades são acelerados por hardware para camada de renderização 1 e 2:  
  
|Recurso|Observações|  
|-------------|-----------|  
|Renderização 2D|A maioria das renderizações 2D tem suporte.|  
|Rasterização 3D|A maioria das rasterizações 3D tem suporte.|  
|Filtro anisotrópico 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tenta usar o filtro anisotrópico quando renderiza conteúdo 3D. O filtro anisotrópico se refere a melhorar a qualidade da imagem de texturas em superfícies distantes e profundamente angular em relação a câmera.|  
|Mapeamento de MIP 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tenta utilizar mapeamento MIP quando renderiza conteúdo 3D. O mapeamento MIP melhora a qualidade da renderização da textura <xref:System.Windows.Controls.Viewport3D>quando uma textura ocupa um campo de visão menor em um .|  
|Gradientes radiais|Enquanto estiver apoiado, <xref:System.Windows.Media.RadialGradientBrush> evite o uso de objetos grandes.|  
|Cálculos de iluminação 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realiza iluminação por vértice, o que significa que uma intensidade de luz precisa ser calculada a cada vértice para cada material aplicado a uma malha.|  
|Renderização de texto|A renderização da fonte subpixel usa sombreadores de pixeldisponíveis no hardware gráfico.|  
  
 Os seguintes recursos e capacidades são acelerados por hardware apenas para a camada de renderização 2:  
  
|Recurso|Observações|  
|-------------|-----------|  
|Suavização 3D|O anti-aliasing 3D é suportado apenas em sistemas operacionais que suportam o Windows Display Driver Model (WDDM), como o Windows Vista e o Windows 7.|  
  
 Os seguintes recursos e capacidades **não** são acelerados por hardware:  
  
|Recurso|Observações|  
|-------------|-----------|  
|Conteúdo impresso|Todo conteúdo impresso é renderizado utilizando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de software.|  
|Conteúdo rasterizado que usa<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Qualquer conteúdo renderizado <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> usando <xref:System.Windows.Media.Imaging.RenderTargetBitmap>o método de .|  
|Conteúdo em azulejo que usa<xref:System.Windows.Media.TileBrush>|Qualquer conteúdo de ladrilho <xref:System.Windows.Media.TileBrush> no qual <xref:System.Windows.Media.TileMode.Tile>a <xref:System.Windows.Media.TileBrush.TileMode%2A> propriedade do é definido para .|  
|Superfícies que excedam o tamanho máximo de textura do hardware de gráficos|Para a maioria dos hardwares gráficos, superfícies grandes tem 2048x2048 ou 4096x4096 pixels de tamanho.|  
|Qualquer operação cujo requisito de RAM de vídeo excede a memória do hardware de gráficos|Você pode monitorar o uso de memória RAM de vídeo do aplicativo usando a ferramenta Perforator incluída no [pacote de desempenho WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) no SDK do Windows.|  
|Janelas em camadas|Janelas em camadas permitem que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos renderizem o conteúdo na tela em uma janela não retangular. Em sistemas operacionais que suportam o Windows Display Driver Model (WDDM), como o Windows Vista e o Windows 7, as janelas em camadas são aceleradas pelo hardware. Em outros sistemas, como o Windows XP, janelas em camadas são renderizadas por software sem aceleração de hardware.<br /><br /> Você pode ativar janelas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em camadas definindo as seguintes <xref:System.Windows.Window> propriedades:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>
## <a name="other-resources"></a>Outros recursos  
 Os recursos a seguir podem ajudá-lo a analisar as características de desempenho de seu aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="graphics-rendering-registry-settings"></a>Configurações do Registro de renderização dos elementos gráficos  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece quatro configurações do Registro para controlar a renderização [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|**Desabilitar Opção de Aceleração de hardware**|Especifica se a aceleração de hardware deve ser habilitada.|  
|**Valor máximo de Multisample**|Especifica o grau de multiamostragem para antialiasing de conteúdo 3D.|  
|**Driver de vídeo configuração de data necessário**|Especifica se o sistema desabilita a aceleração de hardware para drivers lançados antes de novembro de 2004.|  
|**Usar a opção de rasterizador de referência**|Especifica se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deve utilizar o rasterizador de referência.|  
  
 Essas configurações podem ser acessadas por qualquer utilitário de configuração externo que sabe como referenciar as configurações do Registro de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Essas configurações também podem ser criadas ou modificadas acessando os valores diretamente usando o Editor de Registro do Windows. Para obter mais informações, consulte as [configurações de Registro de renderização de gráficos](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Ferramentas de criação de perfil de desempenho do WPF  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um pacote de ferramentas de criação de perfil de desempenho que permitem analisar o comportamento de tempo de execução do aplicativo e determinar os tipos de otimização de desempenho que você pode aplicar. A tabela a seguir lista as ferramentas de criação de perfil de desempenho incluídas na ferramenta Windows SDK, WPF Performance Suite:  
  
|Ferramenta|Descrição|  
|----------|-----------------|  
|Perforator|Use para analisar o comportamento de renderização.|  
|Visual Profiler|Utilize para criar perfil do uso de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] serviços, como layout e manipulação de eventos, pelos elementos na árvore visual.|  
  
 O pacote de desempenho WPF fornece uma exibição gráfica rica em dados de desempenho. Para obter mais informações sobre ferramentas de desempenho do WPF, consulte [Pacote de desempenho WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Ferramenta de diagnóstico do DirectX  
 A Ferramenta de Diagnóstico DirectX, Dxdiag.exe, foi projetada para ajudá-lo a solucionar problemas relacionados ao DirectX. A pasta de instalação padrão da Ferramenta de Diagnóstico DirectX é:  
  
 `~\Windows\System32`  
  
 Quando você executa a Ferramenta de Diagnóstico DirectX, a janela principal contém um conjunto de guias que permitem exibir e diagnosticar informações relacionadas ao DirectX. Por exemplo, a guia **Sistema** fornece informações do sistema sobre o seu computador e especifica a versão do DirectX que está instalada no seu computador.  
  
 ![Captura de tela: DirectX Ferramenta de diagnóstico](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Janela principal da Ferramenta de diagnóstico do DirectX  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Pacote de desempenho WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Configurações do Registro de renderização dos elementos gráficos](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Dicas e truques de animação](../graphics-multimedia/animation-tips-and-tricks.md)
