---
title: Definindo e especificando falhas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 754c938242035549b9deb94a2fe3b975b1384fc0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="defining-and-specifying-faults"></a>Definindo e especificando falhas
Falhas de SOAP transmitem condição informações de erro de um serviço para um cliente e, no caso de duplex, de um cliente para um serviço de forma interoperável. Este tópico discute quando e como definir o conteúdo de falhas personalizado e especificar quais operações podem retorná-los. [!INCLUDE[crabout](../../../includes/crabout-md.md)]como um serviço ou cliente duplex, pode enviar as falhas e como um cliente ou aplicativo de serviço lida com essas falhas, consulte [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md). Para obter uma visão geral de tratamento de erros em [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativos, consulte [especificando e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Visão Geral  
 Declarado falhas de SOAP são aquelas em que uma operação tem um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> que especifica um tipo personalizado de falhas SOAP. Falhas de SOAP não declaradas são aqueles que não são especificados no contrato para uma operação. Este tópico ajuda você a identificar as condições de erro e criar um contrato de falha para o serviço que os clientes podem usar para lidar adequadamente com essas condições de erro quando notificado por falhas de SOAP personalizadas. As tarefas básicas são, em ordem:  
  
1.  Defina as condições de erro que um cliente do seu serviço deve conhecer.  
  
2.  Defina o conteúdo personalizado das falhas SOAP para essas condições de erro.  
  
3.  Marca as operações para que as falhas SOAP específicas que elas geram são expostas aos clientes em WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definir condições de erro que os clientes devem saber sobre  
 Falhas de SOAP são publicamente descritas mensagens que contêm informações de falha de uma determinada operação. Porque eles são descritos junto com outras mensagens de operação em WSDL, os clientes saberem e, portanto, esperam lidar com tais falhas ao invocar uma operação. Mas porque [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços são escritos em código gerenciado, decidir qual erro condições em código gerenciado devem ser convertidos em falhas e retornada ao cliente fornece a oportunidade para separar as condições de erro e os bugs no seu serviço a partir de conversa de erro formal com um cliente.  
  
 Por exemplo, o exemplo de código a seguir mostra uma operação que utiliza dois inteiros e retorna outro inteiro. Várias exceções podem ser geradas aqui, portanto ao criar o contrato de falha, você deve determinar quais condições de erro são importantes para seu cliente. Nesse caso, o serviço deve detectar o <xref:System.DivideByZeroException?displayProperty=nameWithType> exceção.  
  
```csharp  
[ServiceContract]  
public class CalculatorService  
{  
    [OperationContract]   
    int Divide(int a, int b)  
    {  
      if (b==0) throw new Exception("Division by zero!");  
      return a/b;  
    }  
}  
```  
  
```vb  
<ServiceContract> _  
Public Class CalculatorService  
    <OperationContract]> _  
    Public Function Divide(ByVal a As Integer, ByVal b As Integer) _  
       As Integer  
      If (b==0) Then   
            Throw New Exception("Division by zero!")  
      Return a/b  
    End Function  
End Class  
```  
  
 No exemplo anterior, a operação pode retornará uma falha SOAP personalizada específicas para a divisão por zero, uma falha personalizada que é específico para as operações matemáticas, mas que contém informações específicas de divisão por zero, várias falhas de vários diferentes situações de erro, ou nenhuma falha SOAP em todos os.  
  
### <a name="define-the-content-of-error-conditions"></a>Definir o conteúdo das condições de erro  
 Depois que uma condição de erro foi identificada como aquele útil pode retornar uma falha SOAP personalizada, a próxima etapa é definir o conteúdo que falha e certifique-se de que a estrutura de conteúdo pode ser serializada. O exemplo de código na seção anterior mostra um erro específico para um `Divide` operação, mas se há outras operações no `Calculator` de serviço, em seguida, uma única falha SOAP personalizada pode informar ao cliente de todas as condições de erro de cálculo, `Divide`incluídos. O exemplo de código a seguir mostra a criação de uma falha SOAP personalizada, `MathFault`, que podem relatar erros feitos usando todas as operações matemáticas, incluindo `Divide`. Enquanto a classe pode especificar uma operação (o `Operation` propriedade) e um valor que descreve o problema (a `ProblemType` propriedade), a classe e essas propriedades devem ser serializáveis devem ser transferidos para o cliente em uma falha SOAP personalizado. Portanto, o <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> e <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atributos são usados para tornar serializável e interoperável como possível o tipo e suas propriedades.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]como garantir que seus dados é serializável, consulte [especificando a transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Para obter uma lista de serialização de suporte que <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> fornece, consulte [tipos suportados pelo serializador de contrato de dados](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Operações de marca para estabelecer o contrato de falha  
 Depois que uma estrutura de dados serializáveis que é retornada como parte de uma falha SOAP personalizada é definida, a última etapa é marcar seu contrato de operação como gerar uma falha SOAP desse tipo. Para fazer isso, use o <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> de atributos e passar o tipo do tipo de dados personalizado que você tenha criado. O exemplo de código a seguir mostra como usar o <xref:System.ServiceModel.FaultContractAttribute> atributo para especificar que o `Divide` operação pode retornar uma falha SOAP do tipo `MathFault`. Outras operações matemáticas agora também podem especificar que eles podem retornar um `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Uma operação pode especificar que retorna mais de uma falha personalizada ao marcar essa operação com mais de um <xref:System.ServiceModel.FaultContractAttribute> atributo.  
  
 A próxima etapa, para implementar o contrato de falha em sua implementação de operação, é descrita no tópico [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>Considerações de interoperabilidade, SOAP e WSDL  
 Em algumas circunstâncias, especialmente ao interagir com outras plataformas, é importante controlar a maneira como uma falha é exibido em uma mensagem SOAP ou a forma como é descrito nos metadados de WSDL.  
  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo tem um <xref:System.ServiceModel.FaultContractAttribute.Name%2A> propriedade que permite controlar o nome do elemento de falhas WSDL gerado nos metadados para essa falha.  
  
 Acordo com o padrão SOAP, uma falha pode ter um `Action`, um `Code`e um `Reason`. O `Action` é controlado pelo <xref:System.ServiceModel.FaultContractAttribute.Action%2A> propriedade. O <xref:System.ServiceModel.FaultException.Code%2A> propriedade e <xref:System.ServiceModel.FaultException.Reason%2A> propriedade são ambas as propriedades do <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> classe, que é a classe pai de genérica <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. O `Code` propriedade inclui um <xref:System.ServiceModel.FaultCode.SubCode%2A> membro.  
  
 Ao acessar não serviços que geram falhas, existem certas limitações. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]dá suporte a falhas somente com tipos de detalhe que descreve o esquema e que são compatíveis com os contratos de dados. Por exemplo, como mencionado acima, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] não oferece suporte a falhas que usam atributos XML em seus tipos de detalhes, ou falhas com mais de um elemento de nível superior na seção de detalhes.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) (Especificando e lidando com falhas em contratos e serviços)  
 [Sending and Receiving Faults](../../../docs/framework/wcf/sending-and-receiving-faults.md) (Enviando e recebendo falhas)  
 [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md) (Como declarar falhas em contratos de serviço)  
 [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md) (Noções básicas de nível de proteção)  
 [How to: Set the ProtectionLevel Property](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) (Como definir a propriedade ProtectionLevel)  
 [Especificando transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
