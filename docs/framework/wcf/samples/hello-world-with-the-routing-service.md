---
title: Olá Mundo com o serviço de roteamento
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 7a41a1b552e220dcb6367ae59876da4570bab909
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716910"
---
# <a name="hello-world-with-the-routing-service"></a>Olá Mundo com o serviço de roteamento
Este exemplo demonstra o serviço de roteamento do Windows Communication Foundation (WCF). O serviço de roteamento é um componente WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo adapta a amostra de calculadora padrão do WCF para se comunicar usando o serviço de roteamento. Neste exemplo, o cliente da calculadora está configurado para enviar mensagens para um ponto de extremidade exposto pelo roteador. O serviço de roteamento é configurado para aceitar todas as mensagens enviadas a ele e encaminhá-las a um ponto de extremidade que corresponde ao serviço de calculadora. Portanto, as mensagens enviadas do cliente são recebidas pelo roteador e roteadas novamente para o serviço de calculadora real. As mensagens do serviço de calculadora são enviadas de volta para o roteador, que, por sua vez, passa-as de volta para o cliente da calculadora.

### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Usando o Visual Studio 2012, abra HelloRoutingService. sln.

2. Pressione F5 ou CTRL + SHIFT + B.

    > [!NOTE]
    > Se você pressionar F5, o cliente da calculadora será iniciado automaticamente. Se você pressionar CTRL + SHIFT + B (Build), deverá iniciar os aplicativos a seguir por conta própria.
    >
    > 1. Cliente da calculadora (./CalculatorClient/bin/client.exe
    > 2. Serviço de calculadora (./CalculatorService/bin/service.exe)
    > 3. Serviço de roteamento (./RoutingService/bin/RoutingService.exe)

3. Pressione ENTER para iniciar o cliente.

     Você deverá ver a seguinte saída:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Configurável por meio de código ou app. config
 O exemplo é fornecido configurado para usar um arquivo app. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo app. config para algo diferente, de modo que ele não seja reconhecido e remova o comentário da chamada de método para ConfigureRouterViaCode (). O método resulta no mesmo comportamento do roteador.

### <a name="scenario"></a>Cenário
 Este exemplo demonstra o roteador que atua como uma bomba básica de mensagem. O serviço de roteamento atua como um nó de proxy transparente configurado para passar mensagens diretamente para um conjunto pré-configurado de pontos de extremidade de destino.

### <a name="real-world-scenario"></a>Cenário do mundo real
 A contoso deseja aumentar a flexibilidade que tem na nomenclatura, no endereçamento, na configuração e na segurança de seus serviços. Para fazer isso, eles colocam uma bomba básica de mensagens na frente de seus serviços para atuar como um ponto de extremidade voltado para o público. Isso permite que eles coloquem segurança adicional na frente de seus serviços reais e facilitam a implementação de soluções expandidas ou controle de versão de serviço em uma data posterior.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de persistência e de hospedagem do AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
