---
title: Visão geral da classe SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 31ce87303b7b96cfd14d4daf07fd21c9de91a548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535958"
---
# <a name="soundplayer-class-overview"></a>Visão geral da classe SoundPlayer
A classe <xref:System.Media.SoundPlayer> permite que você inclua facilmente sons em seus aplicativos.  
  
 O <xref:System.Media.SoundPlayer> classe pode reproduzir arquivos de som no formato. wav, a partir de um recurso ou UNC ou locais HTTP. Além disso, a <xref:System.Media.SoundPlayer> classe permite que você carregue ou reproduza sons de forma assíncrona.  
  
 Você também pode usar o <xref:System.Media.SystemSounds> classe para reproduzir sons do sistema comum, incluindo um bipe.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriedades, métodos e eventos normalmente usados  
  
|Nome|Descrição|  
|----------|-----------------|  
|Propriedade <xref:System.Media.SoundPlayer.SoundLocation%2A>|O caminho do arquivo ou o endereço Web do som. Os valores aceitáveis podem ser HTTP ou UNC.|  
|Propriedade <xref:System.Media.SoundPlayer.LoadTimeout%2A>|O número de milissegundos que o programa irá esperar para carregar um som antes que ele gere uma exceção. O padrão é 10 segundos.|  
|Propriedade <xref:System.Media.SoundPlayer.IsLoadCompleted%2A>|Um valor booliano que indica se o som terminou de ser carregado.|  
|Método <xref:System.Media.SoundPlayer.Load%2A>|Carrega um som de forma síncrona.|  
|Método <xref:System.Media.SoundPlayer.LoadAsync%2A>|Começa a carregar um som de forma assíncrona. Quando o carregamento for concluído, ele gera o <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> evento.|  
|Método <xref:System.Media.SoundPlayer.Play%2A>|Toca o som especificado no <xref:System.Media.SoundPlayer.SoundLocation%2A> ou <xref:System.Media.SoundPlayer.Stream%2A> propriedade em um novo thread.|  
|Método <xref:System.Media.SoundPlayer.PlaySync%2A>|Toca o som especificado no <xref:System.Media.SoundPlayer.SoundLocation%2A> ou <xref:System.Media.SoundPlayer.Stream%2A> propriedade no thread atual.|  
|Método <xref:System.Media.SoundPlayer.Stop%2A>|Interrompe qualquer som que está em reprodução no momento.|  
|Evento <xref:System.Media.SoundPlayer.LoadCompleted>|Gerado depois que o carregamento de um som é tentado.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
