---
title: Rastreamento de rede no .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
ms.openlocfilehash: e212b2c77a8b0b016e03bfe08f350a0b86ba6ee1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514693"
---
# <a name="network-tracing-in-the-net-framework"></a>Rastreamento de rede no .NET Framework
O rastreamento de rede no .NET Framework fornece acesso a informações sobre invocações de método e tráfego de rede geradas por um aplicativo gerenciado. Esse recurso é útil para a depuração de aplicativos em desenvolvimento e para analisar aplicativos implantados. A saída fornecida pelo rastreamento de rede é personalizável para oferecer suporte a diferentes cenários de uso em tempo de desenvolvimento e em um ambiente de produção.  
  
 Para habilitar o rastreamento de rede no .NET Framework, você deve selecionar um destino para rastrear a saída e adicionar parâmetros de configuração de rastreamento de rede ao aplicativo ou ao arquivo de configuração do computador. Para obter descrições dos arquivos de configuração e como eles são usados, consulte [Arquivos de configuração](../../../docs/framework/configure-apps/index.md). Para obter informações sobre como habilitar o rastreamento de rede, consulte [Habilitar o rastreamento de rede](../../../docs/framework/network-programming/enabling-network-tracing.md). Para obter informações sobre as configurações que você precisa adicionar ao arquivo de configuração, confira [Como: Configurar o rastreamento de rede](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 Quando o rastreamento for habilitado, você poderá coletar informações de rastreamento emitidas pelas classes **System.Net**. Os membros da classe de rede que gerenciam as informações de rastreamento incluem esta nota na seção Observações da documentação da biblioteca de classes do NET Framework:  
  
> [!NOTE]
>  Esse membro emite o rastreamento de informações quando você ativa o rastreamento de rede em seu aplicativo. Para obter mais informações, consulte Rastreamento de rede.  
  
## <a name="see-also"></a>Consulte também
- [Habilitando o rastreamento de rede](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [Como: Configurar o rastreamento de rede](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [Interpretando o rastreamento de rede](../../../docs/framework/network-programming/interpreting-network-tracing.md)
- [Rastreando e instrumentando aplicativos](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
