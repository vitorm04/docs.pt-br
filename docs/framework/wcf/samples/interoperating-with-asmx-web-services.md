---
title: Interoperabilidade com serviços Web ASMX
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa28637ad4ffdc2652c4c925208cd699134579a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="interoperating-with-asmx-web-services"></a>Interoperabilidade com serviços Web ASMX
Este exemplo demonstra como integrar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo cliente com um serviço Web ASMX existente.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedada pelo Internet Information Services (IIS). O serviço é um serviço Web ASMX que implementa um contrato que define um padrão de comunicação de solicitação-resposta. O serviço expõe operações matemáticas (`Add`, `Subtract`, `Multiply`, e `Divide`). O cliente faz solicitações síncronas para uma operação matemática e as respostas do serviço com o resultado. Atividade do cliente estiver visível na janela do console.  
  
 A implementação do serviço Web ASMX mostrada no código de exemplo a seguir calcula e retorna o resultado apropriado.  
  
```csharp  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 Conforme configurado, o serviço pode ser acessado em http://localhost/servicemodelsamples/service.asmx por um cliente no mesmo computador. Para clientes em computadores remotos acessar o serviço, especifique um nome de domínio qualificado em vez de localhost.  
  
 A comunicação é feita por meio de um cliente gerado pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). O cliente está contido em generatedClient.cs o arquivo. O serviço ASMX deve estar disponível para gerar o código de proxy, porque ele é usado para recuperar os metadados atualizados. Execute o seguinte comando em um prompt de comando no diretório do cliente para gerar o proxy digitado.  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 Usando o cliente gerado, você pode acessar um ponto de extremidade de serviço, configurando o endereço apropriado e associação. Como o serviço, o cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade para se comunicar com. A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato, conforme mostrado no exemplo de configuração.  
  
```xml  
<client>  
   <endpoint   
      address="http://localhost/ServiceModelSamples/service.asmx"   
      binding="basicHttpBinding"   
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 A implementação de cliente constrói uma instância do cliente gerado. O cliente gerado, em seguida, pode ser usado para se comunicar com o serviço.  
  
```csharp  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
// Call the Subtract service operation.  
value1 = 145.00D;  
value2 = 76.54D;  
result = client.Subtract(value1, value2);  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
// Call the Multiply service operation.  
value1 = 9.00D;  
value2 = 81.25D;  
result = client.Multiply(value1, value2);  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
// Call the Divide service operation.  
value1 = 22.00D;  
value2 = 7.00D;  
result = client.Divide(value1, value2);  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
  
## <a name="see-also"></a>Consulte também
