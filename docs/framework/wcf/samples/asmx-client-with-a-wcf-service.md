---
title: Cliente ASMX com um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 5a0262361eac35ac45c3861deee13133011754ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="asmx-client-with-a-wcf-service"></a>Cliente ASMX com um serviço do WCF
Este exemplo demonstra como criar um serviço usando o Windows Communication Foundation (WCF) e, em seguida, acessar o serviço de não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, como um cliente ASMX.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedada pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply`, e `Divide`). O cliente ASMX faz solicitações síncronas para uma operação matemática e as respostas do serviço com o resultado.  
  
 O serviço implementa uma `ICalculator` contrato conforme definido no código a seguir.  
  
```  
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
  
 O <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> mapear tipos CLR para uma representação XML. O <xref:System.Runtime.Serialization.DataContractSerializer> interpreta algumas representações XML diferente XmlSerializer. Não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geradores de proxy como Wsdl.exe, geram uma interface mais utilizável quando o XmlSerializer está sendo usado. O <xref:System.ServiceModel.XmlSerializerFormatAttribute> é aplicada para o `ICalculator` interface, para garantir que o XmlSerializer é usado para mapear os tipos CLR em XML. A implementação do serviço calcula e retorna o resultado apropriado.  
  
 O serviço expõe um ponto de extremidade de comunicação com o serviço, definido usando um arquivo de configuração (Web. config). O ponto de extremidade consiste em um endereço, uma ligação e um contrato. O serviço expõe o ponto de extremidade no endereço base fornecido pelo host do Internet Information Services (IIS). O `binding` atributo é definido como basicHttpBinding que permite a comunicação HTTP usando SOAP 1.1, que é compatível com o WS-I Basic Profile 1.1 conforme mostrado no exemplo de configuração.  
  
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
  
 O cliente ASMX se comunica com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço usando um proxy tipado que é gerado pelo utilitário de WSDL Web Services Description Language () (Wsdl.exe). O proxy digitado está contido no generatedClient.cs arquivo. O utilitário WSDL recupera metadados para o serviço especificado e gera um proxy tipado para uso por um cliente para se comunicar. Por padrão, a estrutura não expõem quaisquer metadados. Para expor os metadados necessários para gerar o proxy, você deve adicionar um [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) e defina seu `httpGetEnabled` atributo `True` conforme mostrado na configuração a seguir.  
  
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
  
 Execute o seguinte comando em um prompt de comando no diretório do cliente para gerar o proxy digitado.  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 Usando o proxy com tipo gerado, o cliente pode acessar um ponto de extremidade do serviço em questão, configurando o endereço apropriado. O cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade para se comunicar com.  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 A implementação de cliente constrói uma instância do proxy com tipo para começar a se comunicar com o serviço.  
  
```  
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
  
> [!NOTE]
>  Para obter mais informações sobre a transmissão e retorno de dados complexos tipos consulte: [associação de dados em um cliente de formulários do Windows](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [associação de dados em um cliente do Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), e [dados Associação em um cliente do ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a>Consulte também
