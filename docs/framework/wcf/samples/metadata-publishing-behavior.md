---
title: Comportamento de publicação de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: c3e26454cc9b29620d80a86df7d7aee131e18200
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703467"
---
# <a name="metadata-publishing-behavior"></a>Comportamento de publicação de metadados
O comportamento de publicação de metadados que demonstra como controlar os recursos de publicação de metadados de um serviço. Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para serviços Windows Communication Foundation (WCF) desabilita a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importar ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração.  
  
> [!IMPORTANT]
>  Para maior clareza, este exemplo demonstra como criar um ponto de extremidade de publicação de metadados não segura. Esses pontos de extremidade estão potencialmente disponíveis para os consumidores não autenticados anônimos e tome cuidado antes de implantar esses pontos de extremidade para garantir que publicamente divulga metadados de um serviço são apropriado. Consulte a [ponto de extremidade do personalizado proteger metadados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) exemplo para obter um exemplo que protege um ponto de extremidade de metadados.  
  
 O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço. Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Para um serviço para expor metadados, o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> deve ser configurado no serviço. Quando esse comportamento estiver presente, você pode publicar metadados por meio da configuração de um ponto de extremidade para expor o <xref:System.ServiceModel.Description.IMetadataExchange> contrato como uma implementação de um protocolo WS-MetadataExchange (MEX). Como uma conveniência, este contrato tem o nome abreviado de configuração de "IMetadataExchange". Este exemplo usa o `mexHttpBinding`, que é uma conveniência padrão de associação que é equivalente de `wsHttpBinding` com o modo de segurança definido como `None`. Um endereço relativo "mex" é usado no ponto de extremidade, que, quando resolvido nos serviços de base endereço resulta em um endereço de ponto de extremidade de http://localhost/servicemodelsamples/service.svc/mex. O exemplo a seguir mostra a configuração de comportamento:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 O exemplo a seguir mostra o ponto de extremidade MEX.  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 Este exemplo define o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade para `true`, que também expõe metadados do serviço usando o HTTP GET. Para habilitar um ponto de extremidade de metadados HTTP GET, o serviço deve ter um endereço básico HTTP. A cadeia de caracteres de consulta `?wsdl` é usado no endereço base do serviço para acessar os metadados. Por exemplo, para ver o WSDL para o serviço em um navegador da Web você usaria o endereço http://localhost/servicemodelsamples/service.svc?wsdl. Como alternativa, você pode usar esse comportamento para expor metadados via HTTPS, definindo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> para `true`. Isso requer um endereço base HTTPS.  
  
 Para acessar o uso de ponto de extremidade MEX do serviço do [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Isso gera um cliente com base nos metadados do serviço.  
  
 Para acessar os metadados do serviço usando o HTTP GET, aponte seu navegador para http://localhost/servicemodelsamples/service.svc?wsdl.  
  
 Se você remove esse comportamento e tente abrir o serviço, você receberá uma exceção. Esse erro ocorre porque sem o comportamento, o ponto de extremidade configurado com o `IMetadataExchange` contrato não tem nenhuma implementação.  
  
 Se você definir `HttpGetEnabled` para `false`, você verá a página de ajuda CalculatorService em vez de ver os metadados do serviço.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a>Consulte também
