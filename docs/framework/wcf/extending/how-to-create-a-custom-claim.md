---
title: "Como criar uma afirmação personalizada"
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
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92420b993a1959b03090181944a34a32ab500733
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-claim"></a>Como criar uma afirmação personalizada
A infraestrutura do modelo de identidade no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fornece um conjunto de direitos e tipos de declaração internas com as funções auxiliares para a criação de <xref:System.IdentityModel.Claims.Claim> instâncias com esses tipos de direitos. Essas declarações internas são projetadas para informações sobre o modelo encontrado no cliente de credencial tipos que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suporta por padrão. Em muitos casos, as declarações internas são suficientes; No entanto, alguns aplicativos podem exigir declarações personalizadas. Uma declaração consiste o tipo de declaração, o recurso para o qual a declaração aplica-se a e o direito que é declarada por esse recurso. Este tópico descreve como criar uma declaração personalizada.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Para criar uma declaração personalizada com base em um tipo de dados primitivo  
  
1.  Criar uma declaração personalizada, passando o tipo de declaração, o valor de recurso e o direito de <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> construtor.  
  
    1.  Escolha um valor exclusivo para o tipo de declaração.  
  
         O tipo de declaração é um identificador de cadeia de caracteres exclusiva. É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para o tipo de declaração é exclusivo. Para obter uma lista de tipos de declaração que são definidos por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte o <xref:System.IdentityModel.Claims.ClaimTypes> classe.  
  
    2.  Escolha o tipo de dados primitivo e o valor para o recurso.  
  
         Um recurso é um objeto. O tipo CLR do recurso pode ser um primitivo, como <xref:System.String> ou <xref:System.Int32>, ou qualquer tipo serializável. O tipo CLR do recurso deve ser serializável, porque as declarações são serializadas em vários pontos por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Tipos primitivos são serializáveis.  
  
    3.  Escolha um direito que é definido por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou um valor exclusivo para um direito personalizado.  
  
         Um direito é um identificador de cadeia de caracteres exclusiva. Os direitos que são definidos por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são definidos no <xref:System.IdentityModel.Claims.Rights> classe.  
  
         É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para a direita é exclusivo.  
  
         O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/simplecustomclaim`, para um recurso chamado `Driver's License`e com o <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> à direita.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Para criar uma declaração personalizada com base em um tipo de dados não primitivos  
  
1.  Criar uma declaração personalizada, passando o tipo de declaração, o valor de recurso e o direito de <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> construtor.  
  
    1.  Escolha um valor exclusivo para o tipo de declaração.  
  
         O tipo de declaração é um identificador de cadeia de caracteres exclusiva. É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para o tipo de declaração é exclusivo. Para obter uma lista de tipos de declaração que são definidos por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte o <xref:System.IdentityModel.Claims.ClaimTypes> classe.  
  
    2.  Escolha ou definir um tipo primitivo não serializável para o recurso.  
  
         Um recurso é um objeto. O tipo CLR do recurso deve ser serializável, porque as declarações são serializadas em vários pontos por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Tipos primitivos já são serializáveis.  
  
         Quando um novo tipo é definido, aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> à classe. Também se aplicam a <xref:System.Runtime.Serialization.DataMemberAttribute> a todos os membros do novo tipo que precisam ser serializados como parte da declaração de atributo.  
  
         O exemplo de código a seguir define um tipo de recurso personalizado chamado `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  Escolha um direito que é definido por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou um valor exclusivo para um direito personalizado.  
  
         Um direito é um identificador de cadeia de caracteres exclusiva. Os direitos que são definidos por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são definidos no <xref:System.IdentityModel.Claims.Rights> classe.  
  
         É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para a direita é exclusivo.  
  
         O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/complexcustomclaim`, um tipo de recurso personalizado de `MyResourceType`e com o <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> à direita.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como criar uma declaração personalizada com um tipo de recurso primitivo e uma declaração personalizada com um tipo de recurso não primitivos.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
