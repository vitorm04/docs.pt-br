---
title: "Comportamento de depuração de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04520eda9fe7ce2cd461e094fe2cec76d52ccc7d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="service-debug-behavior"></a>Comportamento de depuração de serviço
Este exemplo demonstra como as configurações de comportamento de serviço podem ser configuradas. O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço. Este exemplo define explicitamente o comportamento de depuração de serviço no arquivo de configuração. Ele também pode ser feito imperativa no código.  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O arquivo Web. config para o servidor define o comportamento de depuração de serviço para habilitar a página de Ajuda e o tratamento de exceções, conforme mostrado no exemplo a seguir.  
  
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
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) é o elemento de configuração que permite alterar as propriedades de comportamento de depuração do serviço. O usuário pode modificar esse comportamento para realizar o seguinte:  
  
-   Isso permite que o serviço retornar qualquer exceção que é lançada pelo código do aplicativo, mesmo se a exceção não é declarada usando a <xref:System.ServiceModel.FaultContractAttribute>. Isso é feito definindo `includeExceptionDetailInFaults` para `true`. Essa configuração é útil durante a depuração de casos em que o servidor está lançando uma exceção inesperada.  
  
    > [!IMPORTANT]
    >  Não é seguro para ativar essa configuração em um ambiente de produção. Uma exceção inesperada do servidor pode ter algumas informações que não são destinadas para o cliente e, portanto definindo `includeExceptionDetailsInFaults` para `true` pode resultar em um vazamento de informação.  
  
-   O [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) também permite que um usuário habilitar ou desabilitar a página de Ajuda. Cada serviço opcionalmente pode expor uma página de Ajuda que contém informações sobre o serviço, incluindo o ponto de extremidade para obter o WSDL para o serviço. Isso pode ser habilitado definindo `httpHelpPageEnabled` para `true`. Isso permite que a página de ajuda a ser retornado para uma solicitação GET para o endereço base do serviço. Você pode alterar esse endereço, definindo outro atributo `httpHelpPageUrl`. Você pode fazer isso segura usando HTTPS em vez de HTTP. Isso pode ser feito definindo `httpsHelpPageEnabled` e `httpsHelpPageUrl`.  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. As três primeiras operações (Adicionar, subtrair e multiplique) deve ter êxito. A última operação ("divisão") falhará com uma divisão por zero exceção.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>Consulte também
