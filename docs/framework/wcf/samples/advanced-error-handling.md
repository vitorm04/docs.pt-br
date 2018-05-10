---
title: Tratamento avançado de erros
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 723b1ca9c2fa771d8bc3f337d9c4fde8c9632c68
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="advanced-error-handling"></a>Tratamento avançado de erros
Este exemplo demonstra o serviço de roteamento do Windows Communication Foundation (WCF). O serviço de roteamento é um componente WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo mostra como o serviço de roteamento de maneira inteligente recupera de erros, usando transações e outros conceitos mensagens mais complexos, como multicast.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Neste exemplo, o serviço de roteamento está configurado para ler uma mensagem de uma fila do MSMQ e multicast essa mensagem para duas listas de filas. Uma lista é usada para filas de serviço e outro é usado para filas de registro em log.  
  
 Porque, por padrão, o MSMQ associação que o serviço de roteamento está configurado para usar oferece suporte ao uso de transações, o serviço de roteamento certifica-se de que a mensagem é recebida pelo menos uma fila em cada lista e transacional antes de relatar para o (a fila de entrada `InQ`) que a mensagem foi roteada com êxito. Assim, no caso em que ambas as filas de serviço ou ambas as filas de log estão disponíveis, o serviço de roteamento de relatórios que não foi possível rotear a mensagem e a fila de entrada deve executar alguma ação. Essa ação consiste em mover a mensagem à fila de mensagens mortas do sistema.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  > [!IMPORTANT]
    >  Instale o MSMQ antes de executar este exemplo. Se o MSMQ não está instalado, uma mensagem de exceção é retornada quando a execução do exemplo. Instruções de instalação do MSMQ podem ser encontradas em [instalar o enfileiramento de mensagens (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra AdvancedErrorHandling.sln.  
  
2.  Pressione **F5** ou **CTRL + SHIFT + B** no Visual Studio.  
  
    1.  Se você compilar o aplicativo com CTRL + SHIFT + B, você deve iniciar o aplicativo. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  Na janela do console, pressione ENTER para iniciar o cliente.  
  
4.  O cliente retorna diversas estatísticas sobre as filas para cada caso.  
  
    1.  A seguir está a saída retornada para o caso 1 (sem falhas).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  A seguir está a saída retornada para o caso 3 (serviço primário e o log de falhas de fila).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  A seguir está a saída retornada para caso 4 (fila de serviço primário e falhas de fila de log primários e de backup).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  A seguir está a saída retornada para caso 2 (Falha de fila de serviço principal).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Configuráveis por meio de código ou App. config  
 O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo RoutingService\App.config para algo diferente para que ele não é reconhecido e alterar o valor da `configDriven` campo RoutingService\Program.cs para `false` para usar a configuração definida no código. Um método resulta no mesmo comportamento do roteador.  
  
### <a name="scenario"></a>Cenário  
 Este exemplo demonstra que o serviço de roteamento pode lidar com recursos de mensagens avançados, como transações e contexto de recebimento e que ele possa utilizar esses recursos como parte de lidar corretamente com cenários de erro.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja utilizar transacional recebe por meio do serviço de roteamento para assegurar que todos os serviços necessários recebam informações mesmo durante a condições de erro. Além disso, eles gostariam erros devem ser tratados corretamente e automaticamente e falhas a ser relatado no caso de que uma mensagem seja entregue mesmo quando lógica de tratamento de erro é utilizado. Para essa finalidade, eles configurar o serviço de roteamento de failover para pontos de extremidade específicos, conforme o esperado e o serviço de roteamento trata as situações de erro, que inclui a criação, conclusão de e/anulando a reversão de transações/receber contextos como é necessário.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
