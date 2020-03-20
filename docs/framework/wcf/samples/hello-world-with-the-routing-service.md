---
title: Olá Mundo com o serviço de roteamento
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183642"
---
# <a name="hello-world-with-the-routing-service"></a>Olá Mundo com o serviço de roteamento
Esta amostra demonstra o Serviço de Roteamento da Windows Communication Foundation (WCF). O Serviço de Roteamento é um componente WCF que facilita a inclusão de um roteador baseado em conteúdo em seu aplicativo. Esta amostra adapta a amostra padrão da calculadora WCF para se comunicar usando o Serviço de Roteamento. Nesta amostra, o cliente Calculadora é configurado para enviar mensagens para um ponto final exposto pelo roteador. O Serviço de Roteamento está configurado para aceitar todas as mensagens enviadas a ele e encaminhá-las para um ponto final que corresponde ao serviço Calculadora. Assim, as mensagens enviadas pelo cliente são recebidas pelo roteador e redirecionadas para o serviço de Calculadora real. As mensagens do serviço Calculadora são enviadas de volta para o roteador, que por sua vez as repassa ao cliente calculadora.

### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Usando o Visual Studio 2012, abra HelloRoutingService.sln.

2. Pressione F5 ou CTRL+SHIFT+B.

    > [!NOTE]
    > Se você pressionar F5, o Cliente calculadora é automaticamente iniciado. Se você pressionar CTRL+SHIFT+B (build), você deve começar a seguir os aplicativos você mesmo.
    >
    > 1. Cliente da calculadora (./CalculadoraCliente/bin/cliente.exe
    > 2. Serviço de calculadora (./CalculadoraService/bin/service.exe)
    > 3. Serviço de roteamento (./RoutingService/bin/RoutingService.exe)

3. Pressione ENTER para iniciar o cliente.

     Você deve ver o seguinte resultado:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Configurável via Código ou App.Config
 Os navios de amostra configurados para usar um arquivo App.config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo App.config para outra coisa para que ele não seja reconhecido e descomentar a chamada do método para ConfigureRouterViaCode(). Qualquer método resulta no mesmo comportamento do roteador.

### <a name="scenario"></a>Cenário
 Esta amostra demonstra o roteador agindo como uma bomba de mensagem básica. O serviço de roteamento funciona como um nó proxy transparente configurado para passar mensagens diretamente para um conjunto pré-configurado de pontos finais de destino.

### <a name="real-world-scenario"></a>Cenário do Mundo Real
 Contoso quer aumentar a flexibilidade que tem na nomenclatura, endereçamento, configuração e segurança de seus serviços. Para isso, eles colocam uma bomba de mensagem básica na frente de seus serviços para atuar como um ponto final voltado para o público. Isso permite que eles coloquem segurança adicional na frente de seus serviços reais e facilitem a implementação de soluções dimensionadas ou versão de serviço em uma data posterior.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Confira também

- [Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
