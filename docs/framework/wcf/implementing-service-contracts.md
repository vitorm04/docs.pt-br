---
title: Implementando contratos de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196314"
---
# <a name="implementing-service-contracts"></a>Implementando contratos de serviço
Um serviço é uma classe que expõe a funcionalidade disponível para clientes em um ou mais pontos de extremidade. Para criar um serviço, escreva uma classe que implementa um contrato do Windows Communication Foundation (WCF). Você pode fazer isso de duas maneiras. Você pode definir o contrato separadamente como uma interface e, em seguida, crie uma classe que implementa essa interface. Como alternativa, você pode criar o contrato e a classe diretamente, colocando o <xref:System.ServiceModel.ServiceContractAttribute> atributo na classe em si e o <xref:System.ServiceModel.OperationContractAttribute> atributo sobre os métodos disponíveis para os clientes do serviço.  
  
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
  
 Como alternativa, um serviço pode expor um contrato diretamente. A seguir está um exemplo de uma classe de serviço que define e implementa um `MathService` contrato.  
  
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
  
 Observe que os serviços acima expõem contratos diferentes porque os nomes de contrato são diferentes. No primeiro caso, o contrato exposto é denominado "`IMath`while" no segundo caso, o contrato é denominado"`MathService`".  
  
 Você pode definir algumas coisas no serviço e operação de níveis de implementação, bem como de instanciação e simultaneidade. Para obter mais informações, consulte [projetar e implementar serviços](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Depois de implementar um contrato de serviço, você deve criar um ou mais pontos de extremidade para o serviço. Para obter mais informações, consulte [visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md). Para obter mais informações sobre como executar um serviço, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Serviços de implantação e projeção](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Como: criar um serviço com uma classe de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Como: criar um serviço com interface de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Especificando comportamento de tempo de execução de serviço](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
