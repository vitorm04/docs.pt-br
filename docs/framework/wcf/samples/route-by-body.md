---
title: Rota por corpo
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: e9a0c947a1dd7ac2a6c7af74baaa072aae67358c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504228"
---
# <a name="route-by-body"></a>Rota por corpo
Este exemplo demonstra como implementar um serviço que aceita objetos de mensagem com qualquer ação SOAP. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo. O serviço implementa uma única `Calculate` operação aceita um <xref:System.ServiceModel.Channels.Message> solicitação de parâmetro e retorna um <xref:System.ServiceModel.Channels.Message> resposta.  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço está hospedado no IIS.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O exemplo demonstra a expedição de mensagem com base no conteúdo do corpo. O Windows Communication Foundation (WCF) serviço modelo mensagem expedição mecanismo interno baseia-se a mensagem de ações. No entanto, há muitos serviços Web existentes que definem todas as operações com ação = "". É possível criar um serviço baseado em WSDL que mantém expedir a solicitação de mensagens com base nas informações de ação. Este exemplo demonstra um contrato de serviço com base no WSDL (WSDL está contida no Service. WSDL que está incluído com o exemplo). O contrato de serviço é Calculadora, semelhante à usada no [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). No entanto, a `[OperationContract]` especifica `Action=""` para todas as operações.  
  
```  
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
  
 Dado um contrato, um serviço requer comportamento de distribuição personalizada `DispatchByBodyBehavior` para permitir que as mensagens sejam enviados entre as operações. Esse comportamento de expedição inicializa o `DispatchByBodyElementOperationSelector` seletor de operação personalizada com uma tabela dos nomes de operação chaveado QName de elementos do respectivos wrapper. `DispatchByBodyElementOperationSelector` examina a marca de início do primeiro filho do corpo e seleciona a operação usando a tabela mencionada anteriormente.  
  
 O cliente usa um proxy gerado automaticamente a partir de WSDL exportado usando o serviço [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 O fato de que as ações de todas as operações são vazias não tem impacto sobre o código do cliente, exceto para os parâmetros de ação no proxy gerado automaticamente.  
  
 O código de cliente executa vários cálculos. Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a>Consulte também
