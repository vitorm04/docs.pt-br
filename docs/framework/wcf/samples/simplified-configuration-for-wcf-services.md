---
title: Configuração simplificada para serviços do WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183348"
---
# <a name="simplified-configuration-for-wcf-services"></a>Configuração simplificada para serviços do WCF
Esta amostra demonstra como implementar e configurar um serviço e cliente típico usando o Windows Communication Foundation (WCF). Esta amostra é a base para todas as outras amostras de tecnologia básica.  
  
 Este serviço, que expõe um ponto final para se comunicar com o serviço, usa a configuração simplificada no .NET Framework 4. Antes do .NET Framework 4, o ponto final é normalmente definido em um arquivo de configuração (Web.config), como mostrado no código de configuração do exemplo a seguir.  
  
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
  
 No Quadro .NET `<service>` 4, o elemento é opcional. Quando um serviço não define nenhum ponto final, um ponto final para cada endereço base e contrato implementado são adicionados ao serviço. O endereço base é anexado ao nome do contrato para determinar o ponto final e a vinculação é determinada pelo esquema de endereço. O exemplo de código a seguir demonstra um arquivo de configuração simplificado. Conforme configurado, o serviço pode `http://localhost/servicemodelsamples/service.svc` ser acessado por um cliente no mesmo computador. Para clientes em computadores remotos acessarem o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez de host local. O serviço não expõe metadados por padrão. Como tal, o serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> se volta contra o comportamento.  
  
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
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Execute a amostra seguindo estas etapas:  
  
    1. Clique com o botão direito do mouse no projeto **Serviço** e selecione **Set as StartUp project**e pressione **Ctrl+F5**.  
  
    2. Aguarde a saída do console confirmando que o serviço está em funcionamento.  
  
    3. Clique com o botão direito do **mouse** no projeto Cliente e selecione **Set as StartUp project**e pressione **Ctrl+F5**.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Confira também

- [Amostras de gerenciamento de appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md)
