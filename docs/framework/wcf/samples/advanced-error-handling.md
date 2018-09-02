---
title: Tratamento avançado de erros
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423426"
---
# <a name="advanced-error-handling"></a>Tratamento avançado de erros
Este exemplo demonstra o serviço de roteamento do Windows Communication Foundation (WCF). O serviço de roteamento é um componente do WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo mostra como o serviço de roteamento de forma inteligente recupera de erros, usando transações e outros conceitos de sistema de mensagens mais complexos como multicasting.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Neste exemplo, o serviço de roteamento é configurado para ler uma mensagem de uma fila do MSMQ e multicast esta mensagem para duas listas de filas. Uma lista é usada para filas de serviço e a outra é usada para filas de registro em log.  
  
 Porque, por padrão, o MSMQ associação que o serviço de roteamento está configurado para uso oferece suporte ao uso de transações, o serviço de roteamento certifica-se de que a mensagem é transacional e recebidas pelo menos uma fila em cada lista antes de relatar para o (fila de entrada `InQ`) que a mensagem foi roteada com êxito. Assim, no caso em que ambas as filas de serviço ou ambas as filas de registro em log estão disponíveis, o serviço de roteamento relata que não foi possível rotear a mensagem e a fila de entrada deve executar alguma ação. Essa ação consiste em mover a mensagem à fila de mensagens mortas do sistema.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  > [!IMPORTANT]
    >  Instale o MSMQ antes de executar esse exemplo. Se o MSMQ não estiver instalado, uma mensagem de exceção é retornada ao executar a amostra. Instruções para instalar o MSMQ podem ser encontradas em [instalar o enfileiramento de mensagens (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra AdvancedErrorHandling.sln.  
  
2.  Pressione **F5** ou **CTRL + SHIFT + B** no Visual Studio.  
  
    1.  Se você compilar o aplicativo com CTRL + SHIFT + B, você deve iniciar o aplicativo no. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  Na janela do console, pressione ENTER para iniciar o cliente.  
  
4.  O cliente retorna diferentes estatísticas sobre as filas para cada caso.  
  
    1.  A seguir está a saída retornada para o caso 1 (não há falhas).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  A seguir está a saída retornada para o caso 3 (serviço primário e registro em log falhas de fila).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  A seguir está a saída retornada para o caso 4 (fila de serviço primário e falhas de fila de log primários e de backup).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  A seguir está a saída retornada para o caso 2 (Falha de fila de serviço principal).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurável por meio de código ou App. config  
 O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo RoutingService\App.config para algo diferente para que ele não é reconhecido e altere o valor da `configDriven` campo RoutingService\Program.cs para `false` para usar a configuração definida no código. Qualquer um dos métodos resulta no mesmo comportamento do roteador.  
  
### <a name="scenario"></a>Cenário  
 Este exemplo demonstra que o serviço de roteamento pode lidar com recursos avançados de mensagens, como transações e contexto de recebimento, e que ele pode utilizar esses recursos como parte de lidar corretamente com cenários de erro.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja utilizar transacional recebe por meio do serviço de roteamento para garantir que todos os serviços necessários recebam informações mesmo durante as condições de erro. Além disso, eles gostariam erros a serem manipulados corretamente e automaticamente e falhas sejam relatados no caso de que uma mensagem é entregue até mesmo quando lógica de tratamento de erro é utilizado. Para essa finalidade, configurar o serviço de roteamento para fazer failover para pontos de extremidade específicos conforme o esperado e o serviço de roteamento, que manipula as situações de erro, que inclui a criação, conclusão e/anulando a reversão de transações/receber contextos como necessário.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
