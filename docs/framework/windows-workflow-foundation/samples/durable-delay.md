---
title: Atraso durável
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507627"
---
# <a name="durable-delay"></a>Atraso durável
Este exemplo demonstra como usar um atraso durável, que é um atraso que persiste o fluxo de trabalho para um dispositivo durável durante o atraso. O fluxo de trabalho de exemplo contém duas mensagens ao console que são separadas por um atraso. Quando o atraso é disparado, o trabalho são descarregados e esperam 5 segundos no armazenamento de instância de trabalho antes de ser recarregado na memória.  
  
## <a name="workflow-details"></a>Detalhes de fluxo de trabalho  
 O host serviço de fluxo de trabalho hospeda o fluxo de trabalho e gerenciar as instâncias de fluxo de trabalho carregar e descarregando as. Para iniciar uma instância de definição de fluxo de trabalho, o exemplo define um proxy que enviar uma mensagem a atividade de <xref:System.ServiceModel.Activities.Receive> no fluxo de trabalho. A propriedade de <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> é definida como `true`, permitindo que você criar uma nova instância de fluxo de trabalho uma vez que recebe uma mensagem.  
  
 A lista a seguir detalha a configuração pelo host serviço de fluxo de trabalho durante a inicialização.  
  
1.  Cria um host de serviço com um endereço (http://localhost:8080/Client).  
  
2.  Cria um ponto de extremidade no host serviço para habilitar comunicação com a atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho.  
  
3.  Configura de um armazenamento de instância de SQL.  
  
4.  Adiciona um comportamento de instância de unload que especifica as circunstâncias em que o host serviço de fluxo de trabalho deve descarregar uma instância de fluxo de trabalho para o armazenamento de persistência SQL. Para esse exemplo, descarrega a instância imediatamente após o fluxo de trabalho aparece ociosa (quando o atraso é disparado).  
  
5.  Cria o proxy que envia uma mensagem à atividade de <xref:System.ServiceModel.Activities.Receive> no fluxo de trabalho.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Configurar o base de dados de persistência.  
  
    1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Navegue até o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] diretório (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  Edite o arquivo de Workflowmanagementservice e adicione a seguinte cadeia de conexão dentro de <`database`> elemento.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  Navegue para o diretório de DurableDelay \ CS.  
  
    5.  Executar Setup.cmd.  
  
2.  Execute [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] usando permissões elevadas clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.  
  
3.  Abra o arquivo de solução de Delay.sln.  
  
4.  Pressione CTRL+SHIFT+B para criar a solução.  
  
5.  Pressione CTRL+F5 para executar a solução.  
  
#### <a name="to-uninstall-this-sample"></a>Para desinstalar este exemplo  
  
1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Navegue para o diretório de DurableDelay \ CS.  
  
3.  Execução Cleanup.cmd.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`