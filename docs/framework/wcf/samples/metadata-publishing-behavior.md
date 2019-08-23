---
title: Comportamento de publicação de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: e0385ec74c9e00472b9ba5fb68f3d97c19f86642
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930419"
---
# <a name="metadata-publishing-behavior"></a>Comportamento de publicação de metadados
O exemplo de comportamento de publicação de metadados demonstra como controlar os recursos de publicação de metadados de um serviço. Para evitar a divulgação não intencional de metadados de serviço potencialmente confidenciais, a configuração padrão para Windows Communication Foundation (WCF) Services desabilita a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como SvcUtil. exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente habilitado na configuração.  
  
> [!IMPORTANT]
>  Para maior clareza, este exemplo demonstra como criar um ponto de extremidade de publicação de metadados não seguro. Esses pontos de extremidade estão potencialmente disponíveis para consumidores anônimos não autenticados e devem ser levados em vida antes da implantação desses pontos de extremidade para garantir que os metadados de um serviço sejam desmarcados publicamente. Consulte o exemplo de [ponto de extremidade de metadados seguro personalizado](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) para obter um exemplo que protege um ponto de extremidade de metadados.  
  
 O exemplo se baseia na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o contrato `ICalculator` de serviço. Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Para que um serviço exponha metadados, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> o deve ser configurado no serviço. Quando esse comportamento estiver presente, você poderá publicar metadados Configurando um ponto de extremidade <xref:System.ServiceModel.Description.IMetadataExchange> para expor o contrato como uma implementação de um protocolo MEX (WS-MetadataExchange). Como uma conveniência, esse contrato recebeu o nome abreviado da configuração "IMetadataExchange". Este exemplo usa o `mexHttpBinding`, que é uma associação padrão de conveniência equivalente `wsHttpBinding` ao com o modo de segurança definido como `None`. Um endereço relativo de "MEX" é usado no ponto de extremidade, que, quando resolvido em relação ao endereço base de serviços, resulta `http://localhost/servicemodelsamples/service.svc/mex`em um endereço de ponto de extremidade de. O seguinte mostra a configuração de comportamento:  
  
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
  
 O ponto de extremidade MEX é mostrado a seguir.  
  
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
  
 Este exemplo define a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Propriedade como `true`, que também expõe os metadados do serviço usando HTTP Get. Para habilitar um ponto de extremidade de metadados GET de HTTP, o serviço deve ter um endereço base HTTP. A cadeia de `?wsdl` caracteres de consulta é usada no endereço base do serviço para acessar os metadados. Por exemplo, para ver o WSDL para o serviço em um navegador da Web, você usaria o `http://localhost/servicemodelsamples/service.svc?wsdl`endereço. Como alternativa, você pode usar esse comportamento para expor metadados por HTTPS definindo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> como. `true` Isso requer um endereço base HTTPS.  
  
 Para acessar o ponto de extremidade MEX do serviço, use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Isso gera um cliente com base nos metadados do serviço.  
  
 Para acessar os metadados do serviço usando HTTP GET, aponte seu navegador para `http://localhost/servicemodelsamples/service.svc?wsdl`.  
  
 Se você remover esse comportamento e tentar abrir o serviço, receberá uma exceção. Esse erro ocorre porque, sem o comportamento, o ponto de extremidade `IMetadataExchange` configurado com o contrato não tem implementação.  
  
 Se você definir `HttpGetEnabled` como `false`, verá a página de ajuda do CalculatorService em vez de ver os metadados do serviço.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
