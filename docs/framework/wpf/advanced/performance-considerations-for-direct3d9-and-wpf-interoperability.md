---
title: "Considerações sobre desempenho para interoperabilidade entre Direct3D9 e WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8142125eae26b15f12652d28fdf0c34f19d49c4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Considerações sobre desempenho para interoperabilidade entre Direct3D9 e WPF
Você pode hospedar conteúdo de Direct3D9 usando o <xref:System.Windows.Interop.D3DImage> classe. Hospedar conteúdo de Direct3D9 pode afetar o desempenho do seu aplicativo. Este tópico descreve as práticas recomendadas para otimizar o desempenho ao hospedar conteúdo de Direct3D9 em um aplicativo WPF (Windows Presentation Foundation). Essas práticas recomendadas incluem como usar <xref:System.Windows.Interop.D3DImage> e práticas recomendadas quando você estiver usando o Windows Vista, Windows XP, e exibe vários monitores.  
  
> [!NOTE]
>  Para ver exemplos de códigos que demonstram essas práticas recomendadas, consulte [Interoperação Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Use D3DImage com moderação  
 Direct3D9 conteúdo hospedado em um <xref:System.Windows.Interop.D3DImage> instância não será renderizado como rápido como em um aplicativo Direct3D puro. Copiar a superfície e liberar o buffer de comando podem ser operações dispendiosas. Como o número de <xref:System.Windows.Interop.D3DImage> aumenta de instâncias, liberando mais ocorre e afeta o desempenho. Portanto, você deve usar <xref:System.Windows.Interop.D3DImage> com moderação.  
  
## <a name="best-practices-on-windows-vista"></a>Práticas recomendadas no Windows Vista  
 Para ter um melhor desempenho no Windows Vista com um visor configurado para usar o WDDM (Windows Display Driver Model), crie sua superfície de Direct3D9 em um dispositivo `IDirect3DDevice9Ex`. Isso permite o compartilhamento de superfície. A placa de vídeo deve dar suporte aos recursos de driver `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` e `D3DCAPS2_CANSHARERESOURCE` no Windows Vista. Qualquer outra configuração faz com que a superfície seja copiada por meio do software, o que reduz significativamente o desempenho.  
  
> [!NOTE]
>  Se o Windows Vista tiver um visor configurado para usar o XDDM (Display Driver Model) do Windows XP, a superfície sempre será copiada por meio do software, independentemente das configurações. Com as configurações e a placa de vídeo apropriadas, você verá um melhor desempenho no Windows Vista quando usar o WDDM, porque as cópias de superfície são executadas no hardware.  
  
## <a name="best-practices-on-windows-xp"></a>Práticas recomendadas no Windows XP  
 Para obter um melhor desempenho no Windows XP, que usa o XDDM (Display Driver Model) do Windows XP, crie uma superfície bloqueável que se comporta corretamente quando o método `IDirect3DSurface9::GetDC` for chamado. Internamente, o método `BitBlt` transfere a superfície em todos os dispositivos do hardware. O método `GetDC` sempre funciona em superfícies XRGB. No entanto, se o computador cliente estiver executando o Windows XP com SP3 ou SP2 e, se o cliente também tiver o hotfix para o recurso de janela em camadas, esse método só funcionará em superfícies ARGB. A placa de vídeo deve dar suporte à capacidade do driver `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`.  
  
 Uma profundidade de exibição de área de trabalho de 16 bits pode reduzir significativamente o desempenho. Recomenda-se uma área de trabalho de 32 bits.  
  
 Se você estiver desenvolvendo para Windows Vista e Windows XP, teste o desempenho no Windows XP. A falta de memória de vídeo no Windows XP é uma preocupação. Além disso, <xref:System.Windows.Interop.D3DImage> no Windows XP usa mais memória de vídeo e largura de banda que o Windows Vista WDDM, devido a uma cópia de memória de vídeo extra necessário. Portanto, você pode esperar que o desempenho seja pior no Windows XP do que no Windows Vista para o mesmo hardware de vídeo.  
  
> [!NOTE]
>  O XDDM está disponível no Windows XP e Windows Vista. No entanto, o WDDM está disponível apenas no Windows Vista.  
  
## <a name="general-best-practices"></a>Práticas recomendadas gerais  
 Ao criar o dispositivo, use o sinalizador de criação `D3DCREATE_MULTITHREADED`. Isso reduz o desempenho, mas o sistema de renderização do WPF chama métodos neste dispositivo de outro thread. Certifique-se de seguir o protocolo de bloqueio corretamente, para que dois threads não acessem o dispositivo ao mesmo tempo.  
  
 Se sua renderização for executada em um thread gerenciado do WPF, será altamente recomendável que você crie o dispositivo com o sinalizador de criação `D3DCREATE_FPU_PRESERVE`. Sem essa configuração, a renderização D3D pode reduzir a precisão das operações de precisão dupla do WPF e introduzir problemas de processamento.  
  
 Agrupando lado a lado um <xref:System.Windows.Interop.D3DImage> é rápida, a menos que o bloco uma superfície não pow2 sem suporte de hardware, ou se você bloco um <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> que contém um <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Práticas recomendadas para visores com vários monitores  
 Se estiver usando um computador que tenha vários monitores, você deverá seguir as práticas recomendadas descritas anteriormente. Também há algumas considerações de desempenho adicionais para uma configuração com vários monitores.  
  
 Quando você cria o buffer de fundo, ele é criado em um adaptador e um dispositivo específico, mas o WPF pode exibir o buffer frontal em qualquer adaptador. Copiar entre adaptadores para atualizar o buffer frontal pode ser muito caro. No Windows Vista, que está configurado para usar o WDDM com várias placas de vídeo e um dispositivo `IDirect3DDevice9Ex`, se o buffer frontal estiver em um adaptador diferente, mas ainda for a mesma placa de vídeo, não haverá nenhuma penalidade de desempenho. No entanto, no Windows XP e no XDDM com várias placas de vídeo, há uma redução de desempenho significativa quando o buffer frontal é exibido em um adaptador diferente do buffer de fundo. Para obter mais informações, consulte [Interoperação Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Resumo de desempenho  
 A tabela a seguir mostra o desempenho da atualização do buffer frontal como uma função do sistema operacional, do formato de pixel e da capacidade de bloqueio da superfície. O buffer frontal e o buffer de fundo devem estar no mesmo adaptador. Dependendo da configuração do adaptador, atualizações de hardware geralmente são muito mais rápidas que atualizações de software.  
  
|Formato de pixel da superfície|Windows Vista, WDDM e 9Ex|Outras configurações do Windows Vista|Windows XP SP3 ou SP2 com hotfix|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (não bloqueável)|**Atualização de hardware**|Atualização de software|Atualização de software|Atualização de software|  
|D3DFMT_X8R8G8B8 (bloqueável)|**Atualização de hardware**|Atualização de software|**Atualização de hardware**|**Atualização de hardware**|  
|D3DFMT_A8R8G8B8 (não bloqueável)|**Atualização de hardware**|Atualização de software|Atualização de software|Atualização de software|  
|D3DFMT_A8R8G8B8 (bloqueável)|**Atualização de hardware**|Atualização de software|**Atualização de hardware**|Atualização de software|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.D3DImage>  
 [Interoperação Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
 [Passo a passo: criando conteúdo Direct3D9 para hospedar no WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [Instruções Passo a Passo: Hospedando Conteúdo Direct3D9 no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
