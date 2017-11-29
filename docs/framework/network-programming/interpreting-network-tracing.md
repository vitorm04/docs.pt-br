---
title: Interpretando o rastreamento de rede
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: deb191f18bda5b00ef4a967f50e8e983289882a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interpreting-network-tracing"></a>Interpretando o rastreamento de rede
Quando o rastreamento de rede está habilitado, você pode usar o rastreamento para capturar as chamadas que seu aplicativo faz para membros de classe <xref:System.Net> diversos. A saída dessas chamadas pode ser semelhante aos exemplos a seguir.  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 No exemplo anterior, [588] é o identificador exclusivo do thread atual. (4357) e (4387) são os carimbos de data/hora que indicam o número de milissegundos decorridos desde que o aplicativo foi iniciado. Os dados após o carimbo de data/hora mostram o aplicativo entrando e saindo do método **Socket.Send**. O objeto executando o método **Send** tem 33574638 como seu identificador exclusivo. O rastreamento de saída do método inclui o valor retornado (que é 61 no exemplo anterior).  
  
 Rastreamentos de rede podem capturar o tráfego de rede que é enviado e recebido pelo seu aplicativo usando os protocolos de nível de aplicativo como o protocolo HTTP. Esses dados podem ser capturados como texto e, opcionalmente, como dados hexadecimais. Dados hexadecimais estão disponíveis quando você especifica **includehex** como o valor do atributo **tracemode**. (Para obter informações detalhadas sobre esse atributo, consulte [Como configurar o rastreamento de rede](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) O rastreamento de exemplo a seguir foi gerado usando **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Para omitir dados hexadecimais, especifique **protocolonly** como o valor para o atributo **tracemode**. O exemplo a seguir mostra o rastreamento quando **protocolonly** é especificado.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Consulte também  
 [Habilitar o rastreamento de rede](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Como configurar o rastreamento de rede](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [Rastreamento de rede no .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
