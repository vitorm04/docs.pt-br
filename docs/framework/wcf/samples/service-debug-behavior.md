---
title: Comportamento de depuração de serviço
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 67ae8cf72baf2d6a54010a05ca4c5e047120617a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044737"
---
# <a name="service-debug-behavior"></a>Comportamento de depuração de serviço

Este exemplo demonstra como as configurações de comportamento de depuração de serviço podem ser definidas. O exemplo se baseia na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o contrato `ICalculator` de serviço. Este exemplo define explicitamente o comportamento de depuração do serviço no arquivo de configuração. Isso também pode ser feito imperativamente no código.

Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).

> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.

O arquivo Web. config do servidor define o comportamento de depuração do serviço para habilitar a página de ajuda e o tratamento de exceções, conforme mostrado no exemplo a seguir.

```xml
<behaviors>
     <serviceBehaviors>
         <behavior name="CalculatorServiceBehavior">
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->
         <!-- Please set this to false when deploying -->
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>
         </behavior>
     </serviceBehaviors>
</behaviors>
```

o Service-Debug > é o elemento de configuração que permite alterar as propriedades de comportamento de depuração do serviço. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) O usuário pode modificar esse comportamento para obter o seguinte:

- Isso permite que o serviço retorne qualquer exceção gerada pelo código do aplicativo, mesmo se a exceção não for declarada <xref:System.ServiceModel.FaultContractAttribute>usando o. Isso é feito definindo `includeExceptionDetailInFaults` como. `true` Essa configuração é útil ao depurar casos em que o servidor está lançando uma exceção inesperada.

  > [!IMPORTANT]
  > Não é seguro ativar essa configuração em um ambiente de produção. Uma exceção inesperada do servidor pode ter algumas informações que não são destinadas ao cliente e `includeExceptionDetailsInFaults` , `true` portanto, a configuração pode resultar em um vazamento de informações.

- O [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) de imdebug também permite que um usuário habilite ou desabilite a página de ajuda. Cada serviço pode, opcionalmente, expor uma página de ajuda que contém informações sobre o serviço, incluindo o ponto de extremidade para obter o WSDL para o serviço. Isso pode ser habilitado pela configuração `httpHelpPageEnabled` para `true`. Isso permite que a página de ajuda seja retornada a uma solicitação GET para o endereço base do serviço. Você pode alterar esse endereço definindo outro atributo `httpHelpPageUrl`. Você pode torná-la segura usando HTTPS em vez de HTTP. Isso pode ser feito definindo `httpsHelpPageEnabled` e. `httpsHelpPageUrl`

Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente. As três primeiras operações (adicionar, subtrair e multiplicar) devem ter sucesso. A última operação ("dividir") falha com uma exceção de divisão por zero.

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
