---
title: Recuperar metadados
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 89984c0d10ee31665ddefe101e3d7416b9451cbf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518501"
---
# <a name="retrieve-metadata"></a>Recuperar metadados
Este exemplo demonstra como implementar um cliente que recupera os metadados de um serviço para escolher a comunicação com um ponto de extremidade dinamicamente. Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md). O serviço foi modificado para expor dois pontos de extremidade — um ponto de extremidade no endereço básico usando o `basicHttpBinding` associação e um ponto de extremidade seguro em {*baseaddress*} / proteger usando o `wsHttpBinding` associação. Em vez de configurar o cliente com as associações e endereços de ponto de extremidade, o cliente recupera dinamicamente os metadados para o serviço usando o <xref:System.ServiceModel.Description.MetadataExchangeClient> de classe e, em seguida, importa os metadados como um <xref:System.ServiceModel.Description.ServiceEndpointCollection> usando o <xref:System.ServiceModel.Description.WsdlImporter> classe.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O aplicativo cliente usa o importados <xref:System.ServiceModel.Description.ServiceEndpointCollection> para criar clientes para se comunicar com o serviço. O aplicativo cliente itera em cada ponto de extremidade recuperado e se comunica com cada ponto de extremidade que implementa o `ICalculator` contrato. O endereço apropriado e associação são fornecidos com o ponto de extremidade recuperado, para que o cliente está configurado para se comunicar com cada ponto de extremidade, conforme mostrado no código de exemplo a seguir.  
  
```csharp   
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 A janela de console do cliente exibe as operações enviadas para cada ponto de extremidade, exibindo o caminho de endereço e o nome da associação.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição de c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
  
## <a name="see-also"></a>Consulte também
