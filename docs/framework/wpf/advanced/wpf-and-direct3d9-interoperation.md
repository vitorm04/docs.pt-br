---
title: Interoperação Direct3D9 e WPF
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: d04278cd2814106dacad53f268ef03227083274e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650806"
---
# <a name="wpf-and-direct3d9-interoperation"></a>Interoperação Direct3D9 e WPF
Você pode incluir conteúdo Direct3D9 em um aplicativo do WPF (Windows Presentation Foundation). Este tópico descreve como criar conteúdo Direct3D9 para interoperar com eficiência com o WPF.  
  
> [!NOTE]
>  Ao usar o conteúdo Direct3D9 no WPF, você também precisa pensar a respeito do desempenho. Para obter mais informações sobre como otimizar o desempenho, consulte [Considerações sobre desempenho para interoperabilidade entre Direct3D9 e WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Buffers de exibição  
 O <xref:System.Windows.Interop.D3DImage> classe gerencia dois buffers de exibição, que são chamados de *buffer de fundo* e o *buffer frontal*. O buffer de fundo é a superfície do Direct3D9. As alterações para o buffer de fundo são copiadas e encaminhadas para o buffer frontal ao chamar o <xref:System.Windows.Interop.D3DImage.Unlock%2A> método.  
  
 A ilustração a seguir mostra a relação entre o buffer de fundo e o buffer frontal.  
  
 ![Buffers de exibição D3DImage](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Criação de dispositivo Direct3D9  
 Para renderizar conteúdo Direct3D9, você deve criar um dispositivo de Direct3D9. Há dois objetos de Direct3D9 que você pode usar para criar um dispositivo: `IDirect3D9` e `IDirect3D9Ex`. Use esses objetos para criar dispositivos `IDirect3DDevice9` e `IDirect3DDevice9Ex`, respectivamente.  
  
 Crie um dispositivo chamando um dos métodos a seguir.  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 No Windows Vista ou sistemas operacionais mais recentes, use o método `Direct3DCreate9Ex` com uma exibição que está configurada para usar o WDDM (Windows Display Driver Model). Use o método `Direct3DCreate9` em qualquer outra plataforma.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Disponibilidade do método Direct3DCreate9Ex  
 O d3d9.dll tem o método `Direct3DCreate9Ex` somente no Windows Vista ou em sistemas operacionais posteriores. Se você vincular diretamente a função no Windows XP, o aplicativo falhará ao carregar. Para determinar se o método `Direct3DCreate9Ex` tem suporte, carregue a DLL e procure o endereço de proc. O código a seguir mostra como testar o método `Direct3DCreate9Ex`. Para obter um exemplo de código completo, consulte [passo a passo: Criando conteúdo Direct3D9 para hospedar no WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Criação de HWND  
 A criação de um dispositivo requer um HWND. Em geral, você cria um HWND fictício para ser usado pelo Direct3D9. O exemplo de código a seguir mostra como criar um HWND fictício.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Parâmetros presentes  
 A criação de um dispositivo também exige um struct `D3DPRESENT_PARAMETERS`, mas apenas alguns parâmetros são importantes. Esses parâmetros são escolhidos para minimizar o volume de memória.  
  
 Defina os campos `BackBufferHeight` e `BackBufferWidth` como 1. Defini-los como 0 faz com que eles sejam definidos para as dimensões do HWND.  
  
 Sempre defina os sinalizadores `D3DCREATE_MULTITHREADED` e `D3DCREATE_FPU_PRESERVE` para evitar a corrupção de memória usada pelo Direct3D9 e evitar que o Direct3D9 altere as configurações de FPU.  
  
 O código a seguir mostra como inicializar o struct `D3DPRESENT_PARAMETERS`.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Criando o destino de renderização do buffer de fundo  
 Para exibir o conteúdo de Direct3D9 em um <xref:System.Windows.Interop.D3DImage>, crie uma superfície de Direct3D9 e atribuí-lo chamando o <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> método.  
  
### <a name="verifying-adapter-support"></a>Verificando o suporte do adaptador  
 Antes de criar uma superfície, verifique se todos os adaptadores dão suporte às propriedades de superfície que você precisa. Mesmo se você renderizar para apenas um adaptador, a janela do WPF poderá ser exibida em qualquer adaptador do sistema. Você sempre deve escrever um código do Direct3D9 que manipule configurações de vários adaptadores e deve verificar o suporte de todos os adaptadores, porque o WPF pode mover a superfície entre os adaptadores disponíveis.  
  
 O exemplo de código a seguir mostra como verificar o suporte ao Direct3D9 de todos os adaptadores no sistema.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Criando a superfície  
 Antes de criar uma superfície, verifique se os recursos do dispositivo dão suporte ao bom desempenho no sistema operacional de destino. Para obter mais informações, consulte [Considerações sobre desempenho para interoperabilidade entre Direct3D9 e WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Quando os recursos do dispositivo foram verificados, você pode criar a superfície. O exemplo de código a seguir mostra como criar o destino de renderização.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 No Windows Vista e sistemas operacionais posteriores, o que são configurados para usar o WDDM, você pode criar uma textura de destino de renderização e passar a superfície de nível 0 para o <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> método. Essa abordagem não é recomendada no Windows XP, porque você não pode criar uma textura de destino de renderização bloqueável e o desempenho será reduzido.  
  
## <a name="handling-device-state"></a>Manipulação de estado de dispositivo  
 O <xref:System.Windows.Interop.D3DImage> classe gerencia dois buffers de exibição, que são chamados de *buffer de fundo* e o *buffer frontal*. O buffer de fundo é a superfície do Direct3D.  As alterações para o buffer de fundo são copiadas e encaminhadas para o buffer frontal ao chamar o <xref:System.Windows.Interop.D3DImage.Unlock%2A> método, em que ele é exibido no hardware. Ocasionalmente, o buffer frontal se torna indisponível. Essa falta de disponibilidade pode ser causada por bloqueio de tela, aplicativos Direct3D de uso exclusivo em tela inteira, troca de usuário ou outras atividades do sistema. Quando isso ocorrer, o aplicativo do WPF é notificado pela manipulação de <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> eventos.  A maneira que seu aplicativo responde à indisponibilidade do buffer frontal depende de se o WPF está habilitado para voltar à renderização de software. O <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> método tem uma sobrecarga que utiliza um parâmetro que especifica se o WPF voltará à renderização de software.  
  
 Quando você chama o <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> sobrecarregar ou ligue para o <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> sobrecarga com o `enableSoftwareFallback` parâmetro definido como `false`, o sistema de renderização libera sua referência para o buffer de fundo quando o buffer frontal se torna indisponível e nada é exibido. Quando o buffer frontal estiver disponível novamente, o sistema de processamento aciona o <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> eventos para notificar o aplicativo do WPF.  Você pode criar um manipulador de eventos para o <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> evento reinicie a renderização novamente com uma superfície Direct3D válida. Para reiniciar a renderização, você deve chamar <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Quando você chama o <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> sobrecarga com o `enableSoftwareFallback` parâmetro definido como `true`, o sistema de renderização retém sua referência para o buffer de fundo quando o buffer frontal fica indisponível, portanto, não há nenhuma necessidade de chamar <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> quando a frente buffer estiver disponível novamente.  
  
 Quando a renderização de software é habilitada, pode haver situações em que o dispositivo do usuário fica indisponível, mas o sistema de renderização retém uma referência à superfície do Direct3D. Para verificar se um dispositivo de Direct3D9 está indisponível, chame o método `TestCooperativeLevel`. Para verificar um dispositivo Direct3D9Ex, chame o método `CheckDeviceState`, porque o método `TestCooperativeLevel` foi preterido e sempre retorna êxito. Se o dispositivo do usuário ficou indisponível, chame <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> para liberar a referência do WPF ao buffer de fundo.  Se você precisar redefinir o dispositivo, chame <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> com o `backBuffer` parâmetro definido como `null`e, em seguida, chame <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> novamente com `backBuffer` definido como uma superfície Direct3D válida.  
  
 Chame o método `Reset` para recuperar de um dispositivo inválido somente se você implementar o suporte a vários adaptadores. Caso contrário, libere todas as interfaces de Direct3D9 e recrie-as completamente. Se o layout do adaptador for alterado, os objetos de Direct3D9 criados antes da alteração não serão atualizados.  
  
## <a name="handling-resizing"></a>Lidando com o redimensionamento  
 Se um <xref:System.Windows.Interop.D3DImage> é exibido em uma resolução diferente de seu tamanho nativo, ela é dimensionada de acordo com a atual <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, exceto pelo fato <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> é substituído por <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Se você precisar de maior fidelidade, você deve criar uma nova superfície quando o contêiner do <xref:System.Windows.Interop.D3DImage> muda de tamanho.  
  
 Há três abordagens possíveis para lidar com redimensionamento.  
  
- Participar no sistema de layout e criar uma nova superfície quando o tamanho for alterado. Não crie muitas superfícies, pois você poderá esgotar ou fragmentar a memória de vídeo.  
  
- Aguardar durante um período fixo de tempo sem que ocorra um evento de redimensionamento para criar a nova superfície.  
  
- Criar um <xref:System.Windows.Threading.DispatcherTimer> que verifica as dimensões do contêiner várias vezes por segundo.  
  
## <a name="multi-monitor-optimization"></a>Otimização de vários monitores  
 Desempenho significativamente reduzido pode ocorrer quando o sistema de renderização move uma <xref:System.Windows.Interop.D3DImage> para outro monitor.  
  
 No WDDM, desde que os monitores estejam na mesma placa de vídeo e você use o `Direct3DCreate9Ex`, não haverá redução no desempenho. Se os monitores estiverem em placas de vídeo separadas, o desempenho será reduzido. No Windows XP, o desempenho é sempre reduzido.  
  
 Quando o <xref:System.Windows.Interop.D3DImage> move para outro monitor, você pode criar uma nova superfície no adaptador correspondente para restaurar o bom desempenho.  
  
 Para evitar a degradação de desempenho, escreva um código especificamente para o caso de vários monitores. A lista a seguir mostra uma maneira de escrever código para vários monitores.  
  
1. Localizar um ponto do <xref:System.Windows.Interop.D3DImage> no espaço de tela com a `Visual.ProjectToScreen` método.  
  
2. Use o método GDI `MonitorFromPoint` para localizar o monitor que está exibindo o ponto.  
  
3. Use o método `IDirect3D9::GetAdapterMonitor` para localizar em qual adaptador de Direct3D9 o monitor está.  
  
4. Se o adaptador não for o mesmo que o adaptador com o buffer de fundo, crie um novo buffer de fundo no novo monitor e o atribui a <xref:System.Windows.Interop.D3DImage> buffer de fundo.  
  
> [!NOTE]
>  Se o <xref:System.Windows.Interop.D3DImage> permeiam monitores, o desempenho será lentos, exceto no caso do WDDM e `IDirect3D9Ex` no mesmo adaptador. Não há nenhuma maneira de melhorar o desempenho nessa situação.  
  
 O exemplo de código a seguir mostra como localizar o monitor atual.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Atualizar o monitor quando o <xref:System.Windows.Interop.D3DImage> alterações de tamanho ou posição do contêiner ou atualizar o monitor usando um `DispatcherTimer` que atualiza algumas vezes por segundo.  
  
## <a name="wpf-software-rendering"></a>Renderização de Software do WPF  
 O WPF renderiza de maneira síncrona no thread da interface do usuário do software nas seguintes situações.  
  
- Imprimindo  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Quando uma dessas situações ocorre, o sistema de renderização chama o <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> método para copiar o buffer de hardware para o software. A implementação padrão chama o método `GetRenderTargetData` com sua superfície. Como essa chamada ocorre fora do padrão de bloqueio/desbloqueio, ela poderá falhar. Nesse caso, o método `CopyBackBuffer` retorna `null` e nenhuma imagem é exibida.  
  
 Você pode substituir a <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> método, chamar a implementação base, e se ele retornar `null`, você pode retornar um espaço reservado <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Você também pode implementar sua própria renderização de software em vez de chamar a implementação de base.  
  
> [!NOTE]
>  Se o WPF estiver renderizando completamente no software, <xref:System.Windows.Interop.D3DImage> não é mostrada porque o WPF não tem um buffer frontal.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.D3DImage>
- [Considerações sobre Desempenho para Interoperabilidade entre Direct3D9 e WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Passo a passo: Criando conteúdo Direct3D9 para hospedar no WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Passo a passo: Hospedando conteúdo Direct3D9 no WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
