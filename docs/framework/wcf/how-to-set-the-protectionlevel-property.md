---
title: Como definir a propriedade ProtectionLevel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 4ff835f767852da586a3a35b7f4ce2edf99db283
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320907"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Como definir a propriedade ProtectionLevel
Você pode definir o nível de proteção aplicando um atributo apropriado e configurando a propriedade. Você pode definir a proteção no nível de serviço para afetar todas as partes de cada mensagem ou pode definir a proteção em níveis cada vez mais granulares, de métodos a partes de mensagens. Para obter mais informações sobre a propriedade `ProtectionLevel`, consulte [noções básicas sobre nível de proteção](understanding-protection-level.md).  
  
> [!NOTE]
> Você pode definir níveis de proteção somente no código, não na configuração.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Para assinar todas as mensagens de um serviço  
  
1. Crie uma interface para o serviço.  
  
2. Aplique o atributo <xref:System.ServiceModel.ServiceContractAttribute> ao serviço e defina a propriedade <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.Sign>, conforme mostrado no código a seguir (o nível padrão é <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Para assinar todas as partes da mensagem para uma operação  
  
1. Crie uma interface para o serviço e aplique o atributo <xref:System.ServiceModel.ServiceContractAttribute> à interface.  
  
2. Adicione uma declaração de método à interface.  
  
3. Aplique o atributo <xref:System.ServiceModel.OperationContractAttribute> ao método e defina a propriedade <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.Sign>, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Protegendo mensagens de falha  
 As exceções que são geradas em um serviço podem ser enviadas a um cliente como falhas de SOAP. Para obter mais informações sobre como criar falhas com rigidez de tipos, consulte [especificando e tratando falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md) e [como declarar falhas em contratos de serviço](how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Para proteger uma mensagem de falha  
  
1. Crie um tipo que representa a mensagem de falha. O exemplo a seguir cria uma classe chamada `MathFault` com dois campos.  
  
2. Aplique o atributo <xref:System.Runtime.Serialization.DataContractAttribute> ao tipo e um atributo <xref:System.Runtime.Serialization.DataMemberAttribute> a cada campo que deve ser serializado, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. Na interface que retornará a falha, aplique o atributo <xref:System.ServiceModel.FaultContractAttribute> ao método que retornará a falha e defina o parâmetro `detailType` como o tipo da classe de falha.  
  
4. Também no construtor, defina a propriedade <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Protegendo partes da mensagem  
 Use um contrato de mensagem para proteger partes de uma mensagem. Para obter mais informações sobre os contratos de mensagem, consulte [usando contratos de mensagem](./feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Para proteger um corpo de mensagem  
  
1. Crie um tipo que representa a mensagem. O exemplo a seguir cria uma classe `Company` com dois campos, `CompanyName` e `CompanyID`.  
  
2. Aplique o atributo <xref:System.ServiceModel.MessageContractAttribute> à classe e defina a propriedade <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3. Aplique o atributo <xref:System.ServiceModel.MessageHeaderAttribute> a um campo que será expresso como um cabeçalho de mensagem e defina a propriedade `ProtectionLevel` como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4. Aplique o <xref:System.ServiceModel.MessageBodyMemberAttribute> a qualquer campo que será expresso como parte do corpo da mensagem e defina a propriedade `ProtectionLevel` como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define a propriedade `ProtectionLevel` de várias classes de atributo em vários locais em um serviço.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O código a seguir mostra os namespaces necessários para compilar o código de exemplo.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [Noções básicas de nível de proteção](understanding-protection-level.md)
