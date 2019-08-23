---
title: 'Como: definir a propriedade ProtectionLevel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 222fda180923cdc7b0d7b7ab413c151c69add259
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950974"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Como: definir a propriedade ProtectionLevel
Você pode definir o nível de proteção aplicando um atributo apropriado e configurando a propriedade. Você pode definir a proteção no nível de serviço para afetar todas as partes de cada mensagem ou pode definir a proteção em níveis cada vez mais granulares, de métodos a partes de mensagens. Para obter mais informações sobre `ProtectionLevel` a propriedade, consulte [noções básicas](../../../docs/framework/wcf/understanding-protection-level.md)sobre o nível de proteção.  
  
> [!NOTE]
> Você pode definir níveis de proteção somente no código, não na configuração.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Para assinar todas as mensagens de um serviço  
  
1. Crie uma interface para o serviço.  
  
2. Aplique o <xref:System.ServiceModel.ServiceContractAttribute> atributo ao serviço e defina a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriedade <xref:System.Net.Security.ProtectionLevel.Sign>como, conforme mostrado no código a seguir (o nível padrão é <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Para assinar todas as partes da mensagem para uma operação  
  
1. Crie uma interface para o serviço e aplique o <xref:System.ServiceModel.ServiceContractAttribute> atributo à interface.  
  
2. Adicione uma declaração de método à interface.  
  
3. Aplique o <xref:System.ServiceModel.OperationContractAttribute> atributo ao método e defina a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriedade <xref:System.Net.Security.ProtectionLevel.Sign>como, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Protegendo mensagens de falha  
 As exceções que são geradas em um serviço podem ser enviadas a um cliente como falhas de SOAP. Para obter mais informações sobre como criar falhas com rigidez de tipos, consulte [especificando e manipulando falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) e [como: Declare falhas em contratos](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)de serviço.  
  
#### <a name="to-protect-a-fault-message"></a>Para proteger uma mensagem de falha  
  
1. Crie um tipo que representa a mensagem de falha. O exemplo a seguir cria uma classe `MathFault` chamada com dois campos.  
  
2. Aplique o <xref:System.Runtime.Serialization.DataContractAttribute> atributo ao tipo e um <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a cada campo que deve ser serializado, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. Na interface que retornará a falha, aplique o <xref:System.ServiceModel.FaultContractAttribute> atributo ao método que retornará a falha e defina o `detailType` parâmetro como o tipo da classe Fault.  
  
4. Também no construtor, defina a <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>Propriedade como, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Protegendo partes da mensagem  
 Use um contrato de mensagem para proteger partes de uma mensagem. Para obter mais informações sobre os contratos de mensagem, consulte [usando contratos de mensagem](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Para proteger um corpo de mensagem  
  
1. Crie um tipo que representa a mensagem. O exemplo a seguir cria `Company` uma classe com dois `CompanyName` campos e `CompanyID`.  
  
2. Aplique o <xref:System.ServiceModel.MessageContractAttribute> atributo à classe e defina a <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> Propriedade como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3. Aplique o <xref:System.ServiceModel.MessageHeaderAttribute> atributo a um campo que será expresso como um cabeçalho de mensagem e defina a `ProtectionLevel` Propriedade como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4. Aplique o <xref:System.ServiceModel.MessageBodyMemberAttribute> a qualquer campo que será expresso como parte do corpo da mensagem e defina a `ProtectionLevel` propriedade <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>como, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define `ProtectionLevel` a propriedade de várias classes de atributo em vários locais em um serviço.  
  
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
- [Noções básicas de nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md)
