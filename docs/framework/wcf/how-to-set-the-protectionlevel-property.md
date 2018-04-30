---
title: Como definir a propriedade ProtectionLevel
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abb1d3cc64b7992b9983e81c5f8a5c30c2343f30
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-set-the-protectionlevel-property"></a>Como definir a propriedade ProtectionLevel
Você pode definir o nível de proteção, aplicando um atributo apropriado e definindo a propriedade. Você pode configurar a proteção no nível de serviço para afetar todas as partes de todas as mensagens, ou você pode definir a proteção nos níveis de cada vez mais granulares de métodos para partes da mensagem. Para obter mais informações sobre o `ProtectionLevel` propriedade, consulte [Noções básicas sobre nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Você pode definir níveis de proteção somente no código, não na configuração.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Para assinar todas as mensagens para um serviço  
  
1.  Crie uma interface para o serviço.  
  
2.  Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> de atributo para o serviço e defina o <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriedade <xref:System.Net.Security.ProtectionLevel.Sign>, conforme mostrado no código a seguir (o nível padrão é <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Para assinar todas as partes da mensagem para uma operação  
  
1.  Criar uma interface para o serviço e aplicar o <xref:System.ServiceModel.ServiceContractAttribute> de atributo para a interface.  
  
2.  Adicione uma declaração de método na interface.  
  
3.  Aplicar o <xref:System.ServiceModel.OperationContractAttribute> de atributo para o método e definir o <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriedade <xref:System.Net.Security.ProtectionLevel.Sign>, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Proteger as mensagens de falha  
 Exceções que são geradas em um serviço podem ser enviadas a um cliente, como falhas de SOAP. Para obter mais informações sobre como criar fortemente tipada falhas, consulte [especificando e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) e [como: declarar falhas em contratos de serviço](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Para proteger uma mensagem de falha  
  
1.  Crie um tipo que representa a mensagem de falha. O exemplo a seguir cria uma classe denominada `MathFault` com dois campos.  
  
2.  Aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> para o tipo de atributo e um <xref:System.Runtime.Serialization.DataMemberAttribute> de atributo para cada campo que deve ser serializado, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  A interface que retornará a falha, se aplicam a <xref:System.ServiceModel.FaultContractAttribute> de atributo para o método que retorna a falha e definir o `detailType` parâmetro para o tipo da classe falha.  
  
4.  Também no construtor, definir o <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> propriedade <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Proteger partes da mensagem  
 Use um contrato de mensagem para proteger partes de uma mensagem. Para obter mais informações sobre contratos de mensagem, consulte [usando contratos de mensagem](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Para proteger um corpo de mensagem  
  
1.  Crie um tipo que representa a mensagem. O exemplo a seguir cria um `Company` classe com dois campos, `CompanyName` e `CompanyID`.  
  
2.  Aplicar o <xref:System.ServiceModel.MessageContractAttribute> para a classe de atributo e definir o <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> propriedade <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3.  Aplicar o <xref:System.ServiceModel.MessageHeaderAttribute> de atributo para um campo que será expresso como um cabeçalho de mensagem e defina o `ProtectionLevel` propriedade <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4.  Aplicar o <xref:System.ServiceModel.MessageBodyMemberAttribute> para qualquer campo que expressa como parte do corpo da mensagem e defina o `ProtectionLevel` propriedade <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o `ProtectionLevel` propriedade de várias classes de atributo em vários locais em um serviço.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O código a seguir mostra os namespaces necessários para compilar o código de exemplo.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [Noções básicas de nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md)
