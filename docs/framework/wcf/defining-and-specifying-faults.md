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
ms.openlocfilehash: 24c05bf41152fba2f54636cd0c15dde6fa71aa2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299314"
---
# <a name="defining-and-specifying-faults"></a>Definindo e especificando falhas
Falhas de SOAP transmitem condição informações de erro de um serviço para um cliente e, no caso de duplex, de um cliente para um serviço de uma maneira interoperável. Este tópico discute quando e como definir o conteúdo de falha personalizado e especificar quais operações poderá retorná-los. Para obter mais informações sobre como um serviço ou cliente duplex, pode enviar essas falhas e como um aplicativo cliente ou serviço lida com essas falhas, consulte [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md). Para obter uma visão geral de tratamento de erros em aplicativos do Windows Communication Foundation (WCF), consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="overview"></a>Visão geral  
 Declarado falhas de SOAP são aquelas em que uma operação tem um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> que especifica um tipo personalizado de falhas SOAP. Falhas SOAP não declaradas são aqueles que não são especificados no contrato para uma operação. Este tópico ajuda você a identificar essas condições de erro e criar um contrato de falha para o serviço que os clientes podem usar para lidar adequadamente com essas condições de erro quando notificado pelo falhas SOAP personalizadas. As tarefas básicas são, em ordem:  
  
1. Defina as condições de erro que um cliente do seu serviço deve saber sobre.  
  
2. Defina o conteúdo personalizado das falhas de SOAP para essas condições de erro.  
  
3. Marca suas operações para que as falhas de SOAP específicas que eles geram são expostas aos clientes em WSDL.  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a>Definir condições de erro que os clientes devem saber sobre  
 Falhas de SOAP são descritas publicamente mensagens que carregam informações de falha de uma determinada operação. Porque eles são descritos juntamente com outras mensagens de operação no WSDL, os clientes saberem e, portanto, esperam lidar com tais falhas ao invocar uma operação. Mas, como os serviços do WCF são escritos em código gerenciado, decidir qual erro devem ser convertidas em falhas de condições em código gerenciado e retornado ao cliente fornece a oportunidade de separar as condições de erro e bugs em seu serviço de erro formal conversa com um cliente.  
  
 Por exemplo, o exemplo de código a seguir mostra uma operação que utiliza dois inteiros e retorna outro inteiro. Várias exceções podem ser geradas aqui, portanto, ao projetar o contrato de falha, você deve determinar quais condições de erro são importantes para seu cliente. Nesse caso, o serviço deve detectar o <xref:System.DivideByZeroException?displayProperty=nameWithType> exceção.  
  
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
  
 No exemplo anterior, a operação pode retornará uma falha SOAP personalizada específicas para a divisão por zero, uma falha personalizado que é específica para operações matemáticas, mas que contém informações específicas de divisão por zero, várias falhas para vários diferentes situações de erro, ou nenhuma falha SOAP em todas.  
  
### <a name="define-the-content-of-error-conditions"></a>Defina o conteúdo das condições de erro  
 Depois que uma condição de erro tiver sido identificada como um que utilmente pode retornar uma falha SOAP personalizada, a próxima etapa é definir o conteúdo do que falhas e certifique-se de que a estrutura de conteúdo pode ser serializada. O exemplo de código na seção anterior mostra um erro específico para um `Divide` operação, mas se houver outras operações no `Calculator` de serviço, em seguida, uma única falha SOAP personalizada pode informar ao cliente de todas as condições de erro de Calculadora, `Divide`incluído. O exemplo de código a seguir mostra a criação de uma falha SOAP personalizada, `MathFault`, que podem relatar erros feitos usando todas as operações matemáticas, incluindo `Divide`. Embora a classe pode especificar uma operação (o `Operation` propriedade) e um valor que descreve o problema (o `ProblemType` propriedade), a classe e essas propriedades devem ser serializáveis sejam transferidos para o cliente em uma falha SOAP personalizado. Portanto, o <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> e <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atributos são usados para tornar o tipo e suas propriedades serializável e tão interoperável quanto possível.  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 Para obter mais informações sobre como garantir que seus dados é serializável, consulte [especificando a transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Para obter uma lista da serialização dar suporte a isso <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> fornece, consulte [tipos com suporte pelo serializador de contrato de dados](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a>Operações de marca para estabelecer o contrato de falha  
 Depois que uma estrutura de dados serializáveis que é retornada como parte de uma falha SOAP personalizada é definida, a última etapa é marcar seu contrato de operação como uma falha SOAP desse tipo de lançamento. Para fazer isso, use o <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> de atributo e passe o tipo do tipo de dados personalizado que você construiu. O exemplo de código a seguir mostra como usar o <xref:System.ServiceModel.FaultContractAttribute> atributo para especificar que o `Divide` operação pode retornar uma falha SOAP do tipo `MathFault`. Outras operações com base em matemática agora também podem especificar que pode retornar um `MathFault`.  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 Uma operação pode especificar que ele retorna mais de uma falha personalizada ao marcar essa operação com mais de um <xref:System.ServiceModel.FaultContractAttribute> atributo.  
  
 A próxima etapa, para implementar o contrato de falha em sua implementação de operação, é descrita no tópico [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a>SOAP, WSDL e considerações de interoperabilidade  
 Em algumas circunstâncias, especialmente ao interoperar com outras plataformas, pode ser importante controlar a maneira que uma falha é exibido em uma mensagem SOAP ou a maneira como ele é descrito nos metadados de WSDL.  
  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo tem um <xref:System.ServiceModel.FaultContractAttribute.Name%2A> propriedade que permite controlar o nome do elemento de falha WSDL é gerado nos metadados para essa falha.  
  
 Segundo o padrão SOAP, uma falha pode ter um `Action`, um `Code`e um `Reason`. O `Action` é controlado pelo <xref:System.ServiceModel.FaultContractAttribute.Action%2A> propriedade. O <xref:System.ServiceModel.FaultException.Code%2A> propriedade e <xref:System.ServiceModel.FaultException.Reason%2A> propriedade são ambas as propriedades da <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> classe, que é a classe pai de genérica <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>. O `Code` propriedade inclui um <xref:System.ServiceModel.FaultCode.SubCode%2A> membro.  
  
 Ao acessar não serviços que a geram falhas, existem certas limitações. O WCF oferece suporte somente a falhas com tipos de detalhes que descreve o esquema e que são compatíveis com contratos de dados. Por exemplo, conforme mencionado acima, o WCF não suporta falhas que usam atributos XML em seus tipos de detalhes ou falhas com mais de um elemento de nível superior na seção de detalhes.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Especificando e lidando com falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md)
- [Como: Declarar falhas em contratos de serviço](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)
- [Noções básicas de nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md)
- [Como: Defina a propriedade ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Especificando transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
