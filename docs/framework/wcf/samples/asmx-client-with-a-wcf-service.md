---
title: Cliente ASMX com um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 1eee814b17a7547bbbc07e17dd675c5f37860341
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302218"
---
# <a name="asmx-client-with-a-wcf-service"></a>Cliente ASMX com um serviço do WCF
Este exemplo demonstra como criar um serviço usando o Windows Communication Foundation (WCF) e, em seguida, acessar o serviço de um cliente não WCF, como um cliente do ASMX.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Esse exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedado pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply`, e `Divide`). O cliente do ASMX faz solicitações síncronas para uma operação matemática e as respostas de serviço com o resultado.  
  
 O serviço implementa um `ICalculator` contrato conforme definido no código a seguir.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 O <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> mapear tipos CLR para uma representação XML. O <xref:System.Runtime.Serialization.DataContractSerializer> interpreta algumas representações XML de forma diferente do que o XmlSerializer. Geradores de proxy não WCF, como Wsdl.exe, geram uma interface mais utilizável, quando o XmlSerializer está sendo usado. O <xref:System.ServiceModel.XmlSerializerFormatAttribute> é aplicada para o `ICalculator` interface, para garantir que o XmlSerializer é usado para mapear os tipos CLR em XML. A implementação do serviço calcula e retorna o resultado apropriado.  
  
 O serviço expõe um ponto de extremidade para se comunicar com o serviço, definido usando um arquivo de configuração (Web. config). O ponto de extremidade consiste em um endereço, uma ligação e um contrato. O serviço expõe o ponto de extremidade no endereço base fornecido pelo host de serviços de informações da Internet (IIS). O `binding` atributo é definido como basicHttpBinding que fornece comunicações HTTP usando o SOAP 1.1, que está em conformidade com WS-I Basic Profile 1.1 como mostrado no seguinte exemplo de configuração.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
    <endpoint address=""  
              binding="basicHttpBinding"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
</services>  
```  
  
 O cliente do ASMX se comunica com o serviço WCF usando um proxy tipado que é gerado pelo utilitário descrição linguagem WSDL (Web Services) (Wsdl.exe). O proxy tipado está contido no generatedClient.cs arquivo. O utilitário WSDL recupera os metadados para o serviço especificado e gera um proxy tipado para uso por um cliente para se comunicar. Por padrão, a estrutura não expõem quaisquer metadados. Para expor os metadados necessários para gerar o proxy, você deve adicionar uma [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) e defina seu `httpGetEnabled` atributo `True` conforme mostrado na seguinte configuração.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Execute o seguinte comando em um prompt de comando no diretório do cliente para gerar o proxy tipado.  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 Usando o proxy tipado gerado, o cliente pode acessar um ponto de extremidade de serviço fornecido pela configuração do endereço apropriado. O cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade para se comunicar com.  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 A implementação do cliente constrói uma instância do proxy tipado para começar a se comunicar com o serviço.  
  
```csharp
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
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
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console 
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Para obter mais informações sobre como passar e retornar dados complexos tipos consulte: [Associação de dados em um Windows Forms de cliente](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [associação de dados em um cliente do Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), e [vinculação de dados em um cliente do ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
