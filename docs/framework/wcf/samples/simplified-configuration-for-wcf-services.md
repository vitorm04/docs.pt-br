---
title: "Configuração simplificada para serviços do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2167b1709ed8db0be76a330eaf72d6d52445fd1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="simplified-configuration-for-wcf-services"></a>Configuração simplificada para serviços do WCF
Este exemplo demonstra como implementar e configurar um serviço típico e o cliente usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Este exemplo é a base para todos os outros exemplos de tecnologia básico.  
  
 Esse serviço, que expõe um ponto de extremidade de comunicação com o serviço, usa a configuração simplificada no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Antes de [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], o ponto de extremidade normalmente é definido em um arquivo de configuração (Web. config), conforme mostrado no código de configuração de exemplo a seguir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Em [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], o `<service>` elemento é opcional. Quando um serviço não define nenhum ponto de extremidade, um ponto de extremidade para cada endereço de base e o contrato implementado são adicionados ao serviço. O endereço base é acrescentado ao nome do contrato para determinar o ponto de extremidade e a associação é determinada pelo esquema de endereço. O exemplo de código a seguir demonstra um arquivo de configuração simplificada. Conforme configurado, o serviço pode ser acessado em http://localhost/servicemodelsamples/service.svc por um cliente no mesmo computador. Para clientes em computadores remotos acessar o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez de localhost. Por padrão, o serviço não expõe metadados. Como tal, o serviço ativa o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Execute o exemplo seguindo estas etapas:  
  
    1.  Clique com botão direito do **Service** do projeto e selecione **definir como projeto de inicialização**, em seguida, pressione **Ctrl + F5**.  
  
    2.  Aguarde até que a saída do console confirmando que o serviço está ativo e em execução.  
  
    3.  Clique com botão direito do **cliente** do projeto e selecione **definir como projeto de inicialização**, em seguida, pressione **Ctrl + F5**.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de gerenciamento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) (Configuração simplificada)
