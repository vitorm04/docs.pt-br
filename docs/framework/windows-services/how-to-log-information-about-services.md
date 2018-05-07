---
title: Como registrar informações em log sobre serviços
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
manager: douge
ms.openlocfilehash: a046c62de8789cbe438dcc849ffc23991a803ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-information-about-services"></a>Como registrar informações em log sobre serviços
Por padrão, todos os projetos de serviço do Windows têm a capacidade de interagir com o log de eventos do aplicativo e gravar informações e exceções. Você usa o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade para indicar se deseja que essa funcionalidade em seu aplicativo. Por padrão, o log está ativado para qualquer serviço que você criar com o modelo de projeto de serviço do Windows. Você pode usar uma forma estática do <xref:System.Diagnostics.EventLog> classe para gravar informações de serviço em um log sem a necessidade de criar uma instância de um <xref:System.Diagnostics.EventLog> componente ou registrar manualmente uma fonte.  
  
 O instalador para o serviço registra automaticamente cada serviço em seu projeto como uma origem válida de eventos com o log de aplicativo no computador onde o serviço é instalado, quando o log está ativado. O serviço registra informações cada vez que o serviço é iniciado, interrompido, pausado, reiniciado, instalado ou desinstalado. Também registra erros que ocorrem. Você não precisa escrever nenhum código para gravar entradas de log ao usar o comportamento padrão; o serviço trata isso para você automaticamente.  
  
 Se você quiser gravar um log de eventos que não sejam o log do aplicativo, você deve definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade `false`, crie seu próprio log de eventos personalizado em seu código de serviços e registrar seu serviço como uma fonte válida de entradas de log. Você deve escrever código para registrar entradas de log sempre que uma ação que você está interessado ocorre.  
  
> [!NOTE]
>  Se você usar um log de eventos personalizado e configura seu aplicativo de serviço para gravar nele, você não deve tentar acessar o log de eventos antes de configurar o serviço <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriedade em seu código. O log de eventos precisa o valor dessa propriedade para registrar seu serviço como uma origem válida de eventos.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Para habilitar o log de eventos padrão para o serviço  
  
-   Definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade para seu componente para `true`.  
  
    > [!NOTE]
    >  Por padrão, essa propriedade é definida como `true`. Você não precisa definir isso explicitamente, a menos que você está criando o processamento mais complexo, como avaliar uma condição e, em seguida, definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade com base no resultado da condição.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Para desabilitar o log de eventos para o serviço  
  
-   Definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade para seu componente para `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Para configurar o registro em um log personalizado  
  
1.  Defina a propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> como `false`.  
  
    > [!NOTE]
    >  Você deve definir <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> como falso para usar um log personalizado.  
  
2.  Configurar uma instância de um <xref:System.Diagnostics.EventLog> em seu aplicativo de serviço do Windows.  
  
3.  Criar um log personalizado chamando o <xref:System.Diagnostics.EventLog.CreateEventSource%2A> método e especificando a cadeia de caracteres de origem e o nome do log de arquivo que você deseja criar.  
  
4.  Definir o <xref:System.Diagnostics.EventLog.Source%2A> propriedade o <xref:System.Diagnostics.EventLog> instância do componente para a cadeia de caracteres de origem que você criou na etapa 3.  
  
5.  Gravar as entradas, acessando o <xref:System.Diagnostics.EventLog.WriteEntry%2A> método sobre o <xref:System.Diagnostics.EventLog> instância do componente.  
  
     O código a seguir mostra como configurar o log para um log personalizado.  
  
    > [!NOTE]
    >  Neste exemplo de código, uma instância de um <xref:System.Diagnostics.EventLog> componente é chamado `eventLog1` (`EventLog1` no Visual Basic). Se você criou uma instância com outro nome na etapa 2, altere o código adequadamente.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
