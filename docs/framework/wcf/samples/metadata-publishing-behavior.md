---
title: Comportamento de publicação de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144390"
---
# <a name="metadata-publishing-behavior"></a>Comportamento de publicação de metadados
A amostra Comportamento de publicação de metadados demonstra como controlar os recursos de publicação de metadados de um serviço. Para evitar a divulgação não intencional de metadados de serviços potencialmente sensíveis, a configuração padrão dos serviços do Windows Communication Foundation (WCF) desativa a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como svcutil.exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente ativado na configuração.  
  
> [!IMPORTANT]
> Para obter clareza, esta amostra demonstra como criar um ponto final de publicação de metadados não seguro. Esses pontos finais estão potencialmente disponíveis para consumidores anônimos não autenticados e os cuidados devem ser tomados antes de implantar tais pontos finais para garantir que a divulgação pública dos metadados de um serviço seja apropriada. Consulte a amostra [Deponto de Metadados Personalizados para](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) obter uma amostra que proteja um ponto final de metadados.  
  
 A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço. Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Para que um serviço exponha metadados, o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> deve ser configurado no serviço. Quando esse comportamento estiver presente, você pode publicar metadados <xref:System.ServiceModel.Description.IMetadataExchange> configurando um ponto final para expor o contrato como uma implementação de um protocolo WS-MetadataExchange (MEX). Como conveniência, este contrato recebeu o nome de configuração abreviado de "IMetadataExchange". Esta amostra `mexHttpBinding`usa o , que é uma `wsHttpBinding` vinculação padrão de `None`conveniência que é equivalente ao com o modo de segurança definido para . Um endereço relativo de "mex" é usado no ponto final, que quando resolvido `http://localhost/servicemodelsamples/service.svc/mex`contra o endereço base de serviços resulta em um endereço de ponto final de . A seguir, mostra a configuração de comportamento:  
  
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
  
 O seguinte mostra o ponto final do MEX.  
  
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
  
 Esta amostra <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> define `true`a propriedade para , que também expõe os metadados do serviço usando HTTP GET. Para habilitar um ponto final de metadados HTTP GET, o serviço deve ter um endereço base HTTP. A seqüência de consultas `?wsdl` é usada no endereço base do serviço para acessar os metadados. Por exemplo, para ver o WSDL para o serviço `http://localhost/servicemodelsamples/service.svc?wsdl`em um navegador da Web, você usaria o endereço . Alternativamente, você pode usar esse comportamento para <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> expor `true`metadados sobre HTTPS, configurando para . Isso requer um endereço base HTTPS.  
  
 Para acessar o ponto final do serviço, use a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Isso gera um cliente com base nos metadados do serviço.  
  
 Para acessar os metadados do serviço usando HTTP `http://localhost/servicemodelsamples/service.svc?wsdl`GET, aponte seu navegador para .  
  
 Se você remover esse comportamento e tentar abrir o serviço, você terá uma exceção. Esse erro ocorre porque, sem o comportamento, o ponto final configurado com o `IMetadataExchange` contrato não tem implementação.  
  
 Se você `HttpGetEnabled` `false`definir, verá a página de ajuda CalculadoraService em vez de ver os metadados do serviço.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
