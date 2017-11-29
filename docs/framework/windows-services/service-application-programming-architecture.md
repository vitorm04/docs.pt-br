---
title: "Arquitetura de programação do aplicativo de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e9c16f2e603a3ce9bbc59be4e01aa492239d2c63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="service-application-programming-architecture"></a>Arquitetura de programação do aplicativo de serviço
Aplicativos de serviço do Windows baseiam-se em uma classe que herda de <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> classe. Substituir os métodos dessa classe e define funcionalidade para eles determinar o comportamento do seu serviço.  
  
 As classes principais envolvidas na criação de serviço são:  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— É substituir os métodos do <xref:System.ServiceProcess.ServiceBase> classe ao criar um serviço e define o código para determinar como o seu serviço funciona nesta classe herdada.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>e <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — use essas classes para instalar e desinstalar o serviço.  
  
 Além disso, uma classe denominada <xref:System.ServiceProcess.ServiceController> pode ser usado para manipular o próprio serviço. Essa classe não está envolvida na criação de um serviço, mas pode ser usada para iniciar e parar o serviço, passar comandos para ele e retornar uma série de enumerações.  
  
## <a name="defining-your-services-behavior"></a>Definindo o comportamento do serviço  
 Em sua classe de serviço, você deve substituir funções de classe base que determinam o que acontece quando o estado do serviço é alterado no Gerenciador de controle de serviços. O <xref:System.ServiceProcess.ServiceBase> classe expõe os métodos a seguir, que você pode substituir para adicionar o comportamento personalizado.  
  
|Método|Substituir para|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Indica quais ações devem ser tomadas quando o serviço é iniciado. Você deve escrever o código neste procedimento para seu serviço para realizar um trabalho útil.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Indica o que deve acontecer quando o serviço está em pausa.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Indica o que deve acontecer quando o serviço é interrompido.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Indica o que deve acontecer quando o serviço continua o funcionamento normal após ser pausado.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Indica o que deve acontecer antes de seu sistema desligado, se seu serviço estiver em execução no momento.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Indica o que deve acontecer quando o serviço recebe um comando personalizado. Para obter mais informações sobre comandos personalizados, consulte o MSDN online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Indica como o serviço deve responder quando um evento de gerenciamento de energia é recebido, como uma bateria fraca ou operação de suspensão.|  
  
> [!NOTE]
>  Esses métodos representam estados que o serviço se movimentam através de seu tempo de vida; a serviço faz a transição de um estado para o próximo. Por exemplo, você nunca obterá o serviço para responder a um <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> comando antes de <xref:System.ServiceProcess.ServiceBase.OnStart%2A> foi chamado.  
  
 Há várias outras propriedades e métodos que são de interesse. Elas incluem:  
  
-   O <xref:System.ServiceProcess.ServiceBase.Run%2A> método sobre o <xref:System.ServiceProcess.ServiceBase> classe. Este é o ponto de entrada principal para o serviço. Quando você cria um serviço usando o modelo de serviço do Windows, o código é inserido em seu aplicativo `Main` método para executar o serviço. Esse código tem esta aparência:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Esses exemplos usam uma matriz do tipo <xref:System.ServiceProcess.ServiceBase>, na qual cada serviço que seu aplicativo contém pode ser adicionado e, em seguida, todos os serviços podem ser executados juntos. Se você estiver apenas criando um único serviço, no entanto, você pode escolher não usar a matriz e simplesmente declarar um novo objeto herdado de <xref:System.ServiceProcess.ServiceBase> e, em seguida, executá-lo. Para obter um exemplo, consulte [como: escrever serviços programaticamente](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Uma série de propriedades de <xref:System.ServiceProcess.ServiceBase> classe. Eles determinam quais métodos podem ser chamados em seu serviço. Por exemplo, quando o <xref:System.ServiceProcess.ServiceBase.CanStop%2A> está definida como `true`, o <xref:System.ServiceProcess.ServiceBase.OnStop%2A> método no seu serviço pode ser chamado. Quando o <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> está definida como `true`, o <xref:System.ServiceProcess.ServiceBase.OnPause%2A> e <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> métodos podem ser chamados. Quando você define uma dessas propriedades para `true`, em seguida, você deve substituir e definir processamento para os métodos associados.  
  
    > [!NOTE]
    >  O serviço deve substituir pelo menos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> para ser útil.  
  
 Você também pode usar um componente denominado o <xref:System.ServiceProcess.ServiceController> para se comunicar com e controlar o comportamento de um serviço existente.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos aplicativos de serviço do Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como: criar serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
