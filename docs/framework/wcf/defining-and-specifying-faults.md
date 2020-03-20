---
title: Definindo e especificando falhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
ms.openlocfilehash: 10fc045cab995cca8d78e470d74ec9341e167308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176689"
---
# <a name="defining-and-specifying-faults"></a>Definindo e especificando falhas
As falhas do SOAP transmitem informações de condição de erro de um serviço para um cliente e, no caso duplex, de um cliente para um serviço de forma interoperável. Este tópico discute quando e como definir o conteúdo de falha personalizada e especificaquais operações podem devolvê-los. Para obter mais informações sobre como um serviço, ou cliente duplex, pode enviar essas falhas e como um cliente ou aplicativo de serviço lida com essas falhas, consulte [Envio e Recebimento de Falhas](sending-and-receiving-faults.md). Para obter uma visão geral do tratamento de erros nos aplicativos wcf (Windows Communication Foundation, a WCF) de [especificação e manuseio de falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Visão geral  
 As falhas de SOAP declaradas são <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> aquelas em que uma operação tem um que especifica um tipo de falha SOAP personalizado. As falhas soap não declaradas são aquelas que não estão especificadas no contrato para uma operação. Este tópico ajuda você a identificar essas condições de erro e criar um contrato de falha para o seu serviço que os clientes podem usar para lidar adequadamente com essas condições de erro quando notificados por falhas de SOAP personalizadas. As tarefas básicas são, em ordem:  
  
1. Defina as condições de erro que um cliente do seu serviço deve saber.  
  
2. Defina o conteúdo personalizado das falhas SOAP para essas condições de erro.  
  
3. Marque suas operações para que as falhas específicas de SOAP que eles jogam sejam expostas aos clientes no WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definindo condições de erro que os clientes devem saber  
 As falhas do SOAP são mensagens descritas publicamente que carregam informações de falha para uma determinada operação. Como são descritos junto com outras mensagens de operação no WSDL, os clientes sabem e, portanto, esperam lidar com tais falhas ao invocar uma operação. Mas como os serviços WCF são escritos em código gerenciado, decidir quais condições de erro no código gerenciado devem ser convertidas em falhas e devolvidas ao cliente, oferece-lhe a oportunidade de separar condições de erro e bugs em seu serviço do erro formal conversa que você tem com um cliente.  
  
 Por exemplo, o exemplo de código a seguir mostra uma operação que pega dois inteiros e retorna outro inteiro. Várias exceções podem ser lançadas aqui, então ao projetar o contrato de falha, você deve determinar quais condições de erro são importantes para o seu cliente. Neste caso, o serviço <xref:System.DivideByZeroException?displayProperty=nameWithType> deve detectar a exceção.  
  
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
    <OperationContract> _
    Public Function Divide(a As Integer, b As Integer) As Integer
        If b = 0 Then Throw New DivideByZeroException("Division by zero!")
        Return a / b
    End Function
End Class
```
  
 No exemplo anterior, a operação pode retornar uma falha de SOAP personalizada que é específica para dividir por zero, uma falha personalizada que é específica para operações matemáticas, mas que contém informações específicas para dividir por zero, múltiplas falhas para várias diferentes situações de erro, ou nenhuma falha SOAP em tudo.  
  
### <a name="define-the-content-of-error-conditions"></a>Defina o conteúdo das condições de erro  
 Uma vez que uma condição de erro tenha sido identificada como aquela que pode retornar útilmente uma falha de SOAP personalizada, o próximo passo é definir o conteúdo dessa falha e garantir que a estrutura de conteúdo possa ser serializada. O exemplo de código na seção `Divide` anterior mostra um erro específico `Calculator` para uma operação, mas se houver outras operações no `Divide` serviço, então uma única falha de SOAP personalizada pode informar ao cliente todas as condições de erro da calculadora, incluídas. O exemplo de código a seguir mostra `MathFault`a criação de uma falha de `Divide`SOAP personalizada, que pode relatar erros cometidos usando todas as operações matemáticas, incluindo . Embora a classe possa especificar uma operação (a `Operation` propriedade) `ProblemType` e um valor que descreva o problema (a propriedade), a classe e essas propriedades devem ser serializáveis para serem transferidas ao cliente em uma falha de SOAP personalizada. Portanto, os <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> e atributos são usados para tornar o tipo e suas propriedades serializáveis e o mais interoperáveis possível.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Para obter mais informações sobre como garantir que seus dados sejam serializáveis, consulte [Especificando transferência de dados em contratos de serviço](./feature-details/specifying-data-transfer-in-service-contracts.md). Para obter uma lista do <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> suporte de serialização que fornece, consulte [Tipos suportados pelo Serializador de contrato de dados](./feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Marcar operações para estabelecer o contrato de falha  
 Uma vez definida uma estrutura de dados serializável que é devolvida como parte de uma falha de SOAP personalizada, o último passo é marcar seu contrato de operação como jogando uma falha SOAP desse tipo. Para fazer isso, <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> use o atributo e passe o tipo de tipo de dados personalizados que você construiu. O exemplo de código a <xref:System.ServiceModel.FaultContractAttribute> seguir mostra `Divide` como usar o atributo `MathFault`para especificar que a operação pode retornar uma falha SOAP do tipo . Outras operações baseadas em matemática agora `MathFault`também podem especificar que podem retornar um .  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Uma operação pode especificar que retorna mais de uma falha <xref:System.ServiceModel.FaultContractAttribute> personalizada marcando essa operação com mais de um atributo.  
  
 O próximo passo, para implementar o contrato de falha na implementação da operação, está descrito no tópico [Envio e Recebimento de Falhas](sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>Considerações sobre SABÃO, WSDL e Interoperabilidade  
 Em algumas circunstâncias, especialmente quando interoperam com outras plataformas, pode ser importante controlar a forma como uma falha aparece em uma mensagem SOAP ou a forma como ela é descrita nos metadados wsdl.  
  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo <xref:System.ServiceModel.FaultContractAttribute.Name%2A> tem uma propriedade que permite o controle do nome do elemento de falha WSDL que é gerado nos metadados para essa falha.  
  
 De acordo com o padrão SOAP, `Code`uma falha `Reason`pode ter um `Action`, a , e um . O `Action` é controlado <xref:System.ServiceModel.FaultContractAttribute.Action%2A> pela propriedade. A <xref:System.ServiceModel.FaultException.Code%2A> propriedade <xref:System.ServiceModel.FaultException.Reason%2A> e a propriedade <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> são ambas propriedades da classe, que é a classe pai do genérico. <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> A `Code` propriedade inclui <xref:System.ServiceModel.FaultCode.SubCode%2A> um membro.  
  
 Ao acessar não-serviços que geram falhas, existem certas limitações. O WCF suporta apenas falhas com tipos de detalhes que o esquema descreve e que são compatíveis com contratos de dados. Por exemplo, como mencionado acima, o WCF não suporta falhas que usam atributos XML em seus tipos de detalhes ou falhas com mais de um elemento de nível superior na seção de detalhes.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Especificando e lidando com falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md)
- [Enviando e recebendo falhas](sending-and-receiving-faults.md)
- [Como declarar falhas em contratos de serviço](how-to-declare-faults-in-service-contracts.md)
- [Noções básicas de nível de proteção](understanding-protection-level.md)
- [Como definir a propriedade ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Especificando transferência de dados em contratos de serviço](./feature-details/specifying-data-transfer-in-service-contracts.md)
