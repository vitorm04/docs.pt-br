---
title: Implementando contratos de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: aefe146a8941d98d7d9138e4ece83c330c967034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184002"
---
# <a name="implementing-service-contracts"></a>Implementando contratos de serviço
Um serviço é uma classe que expõe a funcionalidade disponível aos clientes em um ou mais pontos finais. Para criar um serviço, escreva uma classe que implemente um contrato de WCF (Windows Communication Foundation). É possível fazer isso de duas formas. Você pode definir o contrato separadamente como uma interface e, em seguida, criar uma classe que implemente essa interface. Alternativamente, você pode criar a classe <xref:System.ServiceModel.ServiceContractAttribute> e contrair diretamente <xref:System.ServiceModel.OperationContractAttribute> colocando o atributo na própria classe e o atributo nos métodos disponíveis para os clientes do serviço.  
  
## <a name="creating-a-service-class"></a>Criando uma classe de serviço  
 A seguir, um exemplo de um `IMath` serviço que implementa um contrato que foi definido separadamente.  
  
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
  
 Alternativamente, um serviço pode expor um contrato diretamente. A seguir, um exemplo de uma classe de `MathService` serviçoque define e implementa um contrato.  
  
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
  
 Observe que os serviços anteriores expõem contratos diferentes porque os nomes dos contratos são diferentes. No primeiro caso, o contrato exposto`IMath`é chamado de " "`MathService`enquanto no segundo caso o contrato é chamado de " ".  
  
 Você pode definir algumas coisas nos níveis de implementação de serviço e operação, como simultâneo e instancing. Para obter mais informações, consulte [Projetando e Implementando Serviços](designing-and-implementing-services.md).  
  
 Depois de implementar um contrato de serviço, você deve criar um ou mais pontos finais para o serviço. Para obter mais informações, consulte [Visão geral da criação de endpoint](endpoint-creation-overview.md). Para obter mais informações sobre como executar um serviço, consulte [Serviços de hospedagem](hosting-services.md).  
  
## <a name="see-also"></a>Confira também

- [Serviços de design e implantação](designing-and-implementing-services.md)
- [Como criar um serviço com uma classe de contrato](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Como criar um serviço com interface de contrato](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Especificando o comportamento em tempo de execução do serviço](specifying-service-run-time-behavior.md)
