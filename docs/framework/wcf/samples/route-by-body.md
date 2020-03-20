---
title: Rota por corpo
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144182"
---
# <a name="route-by-body"></a>Rota por corpo
Esta amostra demonstra como implementar um serviço que aceita objetos de mensagem com qualquer ação SOAP. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora. O serviço implementa `Calculate` uma única <xref:System.ServiceModel.Channels.Message> operação que aceita <xref:System.ServiceModel.Channels.Message> um parâmetro de solicitação e retorna uma resposta.  
  
 Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço está hospedado no IIS.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A amostra demonstra o envio de mensagens com base no conteúdo do corpo. O mecanismo de envio de mensagens do modelo de texto do modelo de serviço da Windows Communication Foundation (WCF) é baseado em ações de mensagem. No entanto, existem muitos serviços Web existentes que definem todas as suas operações com o Action=". É impossível construir um serviço baseado no WSDL que continue despachando mensagens de solicitação com base em informações de Ação. Esta amostra demonstra um contrato de serviço baseado em WSDL (o WSDL está contido no Service.wsdl que está incluído na amostra). O contrato de prestação de serviços é calculadora, semelhante ao utilizado em [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). No `[OperationContract]` entanto, os especificados `Action=""` para todas as operações.  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 Dado um contrato, um `DispatchByBodyBehavior` serviço requer comportamento de expedição personalizado para permitir que mensagens sejam enviadas entre as operações. Esse comportamento de despacho `DispatchByBodyElementOperationSelector` inicializa o seletor de operação personalizado com uma tabela dos nomes de operação com chave QName dos respectivos elementos do invólucro. `DispatchByBodyElementOperationSelector`olha para a tag de início do primeiro filho do Corpo e seleciona a operação usando a tabela mencionada anteriormente.  
  
 O cliente usa um proxy gerado automaticamente a partir do WSDL exportado pelo serviço usando [serviceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 O fato de as ações de todas as operações estarem vazias não tem impacto no código do cliente, exceto nos parâmetros action no proxy gerado automaticamente.  
  
 O código do cliente realiza vários cálculos. Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
