---
title: "Implementando contratos de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 688637ae54e92296d103a681715dd491ba8782ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-service-contracts"></a>Implementando contratos de serviço
Um serviço é uma classe que expõe a funcionalidade disponível para clientes em um ou mais pontos de extremidade. Para criar um serviço, escrever uma classe que implementa uma [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] contrato. Você pode fazer isso de duas maneiras. Você pode definir o contrato separadamente como uma interface e, em seguida, crie uma classe que implementa essa interface. Como alternativa, você pode criar a classe e o contrato diretamente, colocando o <xref:System.ServiceModel.ServiceContractAttribute> atributo da classe em si e o <xref:System.ServiceModel.OperationContractAttribute> atributo sobre os métodos disponíveis para os clientes do serviço.  
  
## <a name="creating-a-service-class"></a>Criando uma classe de serviço  
 A seguir está um exemplo de um serviço que implementa um `IMath` contrato que tenha sido definido separadamente.  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Como alternativa, um serviço pode expor um contrato diretamente. A seguir está um exemplo de uma classe de serviço que define e implementa uma `MathService` contrato.  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Observe que os serviços anteriores expõem contratos diferentes porque os nomes de contrato são diferentes. No primeiro caso, o contrato exposto é denominado "`IMath`"enquanto no segundo caso, o contrato é denominado"`MathService`".  
  
 Você pode definir algumas coisas no serviço e operação níveis de implementação, como a simultaneidade e a instância. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Projetar e implementar serviços](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Depois de implementar um contrato de serviço, você deve criar um ou mais pontos de extremidade para o serviço. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]como executar um serviço, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md) (Serviços de design e implantação)  
 [Como: criar um serviço com uma classe de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [Como: criar um serviço com uma Interface de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [Specifying Service Run-Time Behavior](../../../docs/framework/wcf/specifying-service-run-time-behavior.md) (Especificando o comportamento em tempo de execução do serviço)
