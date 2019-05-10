---
title: Configuração simplificada para serviços do WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 791d2dcf2578ed0b816450f558654dae259653bb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650976"
---
# <a name="simplified-configuration-for-wcf-services"></a>Configuração simplificada para serviços do WCF
Este exemplo demonstra como implementar e configurar um serviço típico e o cliente usando o Windows Communication Foundation (WCF). Este exemplo é a base para todos os outros exemplos de tecnologia básica.  
  
 Esse serviço, que expõe um ponto de extremidade para comunicação com o serviço, usa a configuração simplificada no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Antes de [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], o ponto de extremidade normalmente é definido em um arquivo de configuração (Web. config), como mostrado no código de configuração de exemplo a seguir.  
  
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
  
 Na [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], o `<service>` elemento é opcional. Quando um serviço não define nenhum ponto de extremidade, um ponto de extremidade para cada endereço básico e contrato implementada são adicionadas ao serviço. O endereço básico é acrescentado ao nome do contrato para determinar o ponto de extremidade e a associação é determinada pelo esquema de endereço. O exemplo de código a seguir demonstra um arquivo de configuração simplificada. Conforme configurado, o serviço pode ser acessado em `http://localhost/servicemodelsamples/service.svc` por um cliente no mesmo computador. Para clientes em computadores remotos acessar o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez do localhost. O serviço não expõe metadados por padrão. Como tal, o serviço liga o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento.  
  
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
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Execute o exemplo seguindo estas etapas:  
  
    1. Clique com botão direito do **Service** do projeto e selecione **definir como projeto de inicialização**, em seguida, pressione **Ctrl + F5**.  
  
    2. Aguarde até que a saída do console confirmando que o serviço está instalado e em execução.  
  
    3. Clique com botão direito do **cliente** do projeto e selecione **definir como projeto de inicialização**, em seguida, pressione **Ctrl + F5**.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de gerenciamento do AppFabric](https://go.microsoft.com/fwlink/?LinkId=193960)
- [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)
