---
title: "Noções básicas de nível de proteção"
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
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f107e4d1a9779c04a33060af34ee1fc873305eab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="understanding-protection-level"></a>Noções básicas de nível de proteção
O `ProtectionLevel` propriedade é encontrada em muitas classes diferentes, como o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> classes. A propriedade controla como uma parte (ou inteiro) de uma mensagem é protegido. Este tópico explica o [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] recurso e como ele funciona.  
  
 Para obter instruções sobre como definir o nível de proteção, consulte [como: definir a propriedade ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Níveis de proteção podem ser definidos apenas em código, não na configuração.  
  
## <a name="basics"></a>Noções básicas  
 Para entender o recurso de nível de proteção, as instruções básicas a seguir se aplicam:  
  
-   Existem três níveis básico de proteção para qualquer parte de uma mensagem. A propriedade (onde ele ocorre) é definida como um do <xref:System.Net.Security.ProtectionLevel> valores de enumeração. Em ordem crescente de proteção, elas incluem:  
  
    -   `None`.  
  
    -   `Sign`. A parte protegida foi assinada digitalmente. Isso garante que a detecção de adulteração a parte da mensagem protegida.  
  
    -   `EncryptAndSign`. A parte da mensagem é criptografada para garantir a confidencialidade antes que ele está assinado.  
  
-   Você pode definir requisitos de proteção somente para *dados de aplicativo* com esse recurso. Por exemplo, cabeçalhos de WS-Addressing são dados de infraestrutura e, portanto, não são afetados pelo `ProtectionLevel`.  
  
-   Quando o modo de segurança é definido como `Transport`, a mensagem inteira é protegida pelo mecanismo de transporte. Portanto, definindo um nível de proteção separados para diferentes partes de uma mensagem não tem nenhum efeito.  
  
-   O `ProtectionLevel` é uma maneira para que o desenvolvedor definir o *nível mínimo* que deve estar de acordo com uma associação. Quando um serviço é implantado, a associação real especificada na configuração pode não dar suporte ou o nível mínimo. Por exemplo, por padrão, o <xref:System.ServiceModel.BasicHttpBinding> classe não oferece segurança (embora ela pode ser habilitada). Portanto, o uso com um contrato com qualquer configuração diferente de `None` fará com que uma exceção seja lançada.  
  
-   Se o serviço exigir que o mínimo `ProtectionLevel` para todas as mensagens é `Sign`, um cliente (talvez criado por uma não -[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tecnologia) pode criptografar e assinar todas as mensagens (que é maior que o mínimo necessário). Nesse caso, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] não gerará uma exceção porque o cliente fez mais do que o mínimo. No entanto, observe que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos (serviços ou clientes) não excesso protege uma parte da mensagem se possível, mas estejam em conformidade com o nível mínimo. Observe também que, ao usar `Transport` como o modo de segurança, o transporte excesso pode o proteger o fluxo de mensagem porque ele é inerentemente não é possível proteger em um nível mais granular.  
  
-   Se você definir o `ProtectionLevel` explicitamente como `Sign` ou `EncryptAndSign`, em seguida, você deve usar uma associação com segurança habilitada ou uma exceção será lançada.  
  
-   Se você selecionar uma associação que habilita a segurança e você não definir o `ProtectionLevel` propriedade em qualquer lugar no contrato, todos os aplicativos de dados serão criptografados e assinados.  
  
-   Se você selecionar uma associação que não tem segurança ativada (por exemplo, o `BasicHttpBinding` classe possui segurança desativada por padrão) e o `ProtectionLevel` não for explicitamente definida, em seguida, nenhum dos dados do aplicativo serão protegidos.  
  
-   Se você estiver usando uma associação que se aplica a segurança no nível de transporte, todos os dados de aplicativo serão protegidos de acordo com os recursos do transporte.  
  
-   Se você usar uma associação que se aplica a segurança no nível da mensagem, dados de aplicativo serão protegidos acordo com os níveis de proteção definida no contrato. Se você não especificar um nível de proteção, em seguida, todos os dados de aplicativo nas mensagens serão criptografados e assinados.  
  
-   O `ProtectionLevel` pode ser definido em diferentes níveis de escopo. Há uma hierarquia associada com o escopo, que é explicada na próxima seção.  
  
## <a name="scoping"></a>Definição de escopo  
 Definindo o `ProtectionLevel` a API do mais alto define o nível para todos os níveis abaixo dele. Se o `ProtectionLevel` é definido como um valor diferente em um nível inferior, todas as APIs abaixo que nível na hierarquia agora será redefinido para o novo nível (APIs acima dele, no entanto, ainda serão afetados por um nível mais alto). A hierarquia é da seguinte maneira. Atributos do mesmo nível são correspondentes.  
  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
 <xref:System.ServiceModel.FaultContractAttribute>  
  
 <xref:System.ServiceModel.MessageContractAttribute>  
  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
## <a name="programming-protectionlevel"></a>Programação ProtectionLevel  
 Programa de `ProtectionLevel` em qualquer ponto na hierarquia, basta definir a propriedade para um valor apropriado ao aplicar o atributo. Para obter exemplos, consulte [como: definir a propriedade ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Definindo a propriedade falhas e contratos exige a compreensão de como funcionam os recursos de mensagem. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Como: definir a propriedade ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) e [usando contratos de mensagem](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
## <a name="ws-addressing-dependency"></a>Dependência de WS-Addressing.  
 Na maioria dos casos, usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gerar um cliente garante que os contratos de serviço e cliente são idênticos. No entanto, aparentemente idênticos contratos podem causar o cliente lançar uma exceção. Isso ocorre sempre que uma associação não oferece suporte a especificação WS-Addressing e vários níveis de proteção são especificados no contrato. Por exemplo, a <xref:System.ServiceModel.BasicHttpBinding> classe não oferece suporte à especificação ou se você criar uma associação personalizada que não oferece suporte, WS-Addressing. O `ProtectionLevel` recurso baseia-se na especificação WS-Addressing para habilitar diferentes níveis de proteção em um único contrato. Se a associação não oferece suporte a especificação WS-Addressing, todos os níveis serão definidos para o mesmo nível de proteção. Definirá o nível de proteção efetivo para todos os escopos no contrato para o nível mais alto de proteção usado no contrato.  
  
 Isso pode causar um problema que é difícil de depurar a princípio. É possível criar um contrato de cliente (uma interface) que inclui métodos para mais de um serviço. Ou seja, a mesma interface é usada para criar um cliente que se comunica com vários serviços, e a única interface contém métodos para todos os serviços. O desenvolvedor deve observar neste cenário raro para invocar somente os métodos que são aplicáveis para cada serviço específico. Se a associação é o <xref:System.ServiceModel.BasicHttpBinding> classe, proteção de vários níveis não tem suporte. No entanto, um serviço de resposta para o cliente pode responder a um cliente com um nível de proteção menor do que o necessário. Nesse caso, o cliente lançará uma exceção porque ele espera um nível mais alto de proteção.  
  
 Um exemplo de código que ilustra o problema. O exemplo a seguir mostra um serviço e um contrato de cliente. Suponha que a associação é o [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento. Portanto, todas as operações em um contrato tem o mesmo nível de proteção. Esse nível de proteção uniforme é determinado como o nível de proteção máximo em todas as operações.  
  
 O contrato de serviço é:  
  
 [!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
 [!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]  
  
 O código a seguir mostra o cliente a interface de contrato. Observe que ele inclui um `Tax` método se destina a ser usado com um serviço diferente:  
  
 [!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
 [!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]  
  
 Quando o cliente chama o `Price` método, ele gerará uma exceção quando ele recebe uma resposta do serviço. Isso ocorre porque o cliente não especificar um `ProtectionLevel` no `ServiceContractAttribute`, e, portanto, o cliente usa o padrão (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) para todos os métodos, incluindo o `Price` método. No entanto, o serviço retornará o valor usando o <xref:System.Net.Security.ProtectionLevel.Sign> porque o contrato de serviço define um único método que tem seu nível de proteção definido como <xref:System.Net.Security.ProtectionLevel.Sign>. Nesse caso, o cliente gerará um erro ao validar a resposta do serviço.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 <xref:System.Net.Security.ProtectionLevel>  
 [Securing Services](../../../docs/framework/wcf/securing-services.md) (Protegendo serviços)  
 [How to: Set the ProtectionLevel Property](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) (Como definir a propriedade ProtectionLevel)  
 [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) (Especificando e lidando com falhas em contratos e serviços)  
 [Usando contratos de mensagem](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
