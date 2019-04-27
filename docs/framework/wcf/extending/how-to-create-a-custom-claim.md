---
title: 'Como: criar uma declaração personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 1892e910a86e01b7b2ee0f6a2403ad7af4688808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857772"
---
# <a name="how-to-create-a-custom-claim"></a>Como: criar uma declaração personalizada
A infraestrutura de modelo de identidade no Windows Communication Foundation (WCF) fornece um conjunto de tipos de declaração interna e direitos com as funções auxiliares para a criação de <xref:System.IdentityModel.Claims.Claim> instâncias com esses tipos e direitos. Essas declarações internas são projetadas para informações sobre o modelo encontrado em tipos de credencial de cliente WCF oferece suporte por padrão. Em muitos casos, as declarações internas são suficientes; No entanto, alguns aplicativos podem exigir declarações personalizadas. Uma declaração consiste o tipo de declaração, o recurso para o qual a declaração aplica-se a e à direita que é declarada por esse recurso. Este tópico descreve como criar uma declaração personalizada.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Para criar uma declaração personalizada que é baseada em um tipo de dados primitivo  
  
1. Criar uma declaração personalizada, passando o tipo de declaração, o valor do recurso e o direito do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> construtor.  
  
    1.  Escolha um valor exclusivo para o tipo de declaração.  
  
         O tipo de declaração é um identificador de cadeia de caracteres exclusiva. É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para o tipo de declaração é exclusivo. Para obter uma lista dos tipos de declaração que são definidas pelo WCF, consulte o <xref:System.IdentityModel.Claims.ClaimTypes> classe.  
  
    2.  Escolha o tipo de dados primitivo e o valor para o recurso.  
  
         Um recurso é um objeto. O tipo CLR do recurso pode ser um primitivo, tal como <xref:System.String> ou <xref:System.Int32>, ou qualquer tipo serializável. O tipo CLR do recurso deve ser serializável, porque as declarações são serializadas em vários pontos pelo WCF. Tipos primitivos são serializáveis.  
  
    3.  Escolha um direito que é definido pelo WCF ou um valor exclusivo para um direito personalizado.  
  
         Um direito é um identificador de cadeia de caracteres exclusiva. Os direitos que são definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.  
  
         É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para a direita é exclusivo.  
  
         O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/simplecustomclaim`, para um recurso chamado `Driver's License`e com o <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> à direita.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Para criar uma declaração personalizada que é baseada em um tipo de dados não primitivos  
  
1. Criar uma declaração personalizada, passando o tipo de declaração, o valor do recurso e o direito do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> construtor.  
  
    1.  Escolha um valor exclusivo para o tipo de declaração.  
  
         O tipo de declaração é um identificador de cadeia de caracteres exclusiva. É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para o tipo de declaração é exclusivo. Para obter uma lista dos tipos de declaração que são definidas pelo WCF, consulte o <xref:System.IdentityModel.Claims.ClaimTypes> classe.  
  
    2.  Escolha ou definir um tipo não primitivo serializável para o recurso.  
  
         Um recurso é um objeto. O tipo CLR do recurso deve ser serializável, porque as declarações são serializadas em vários pontos pelo WCF. Tipos primitivos já são serializáveis.  
  
         Quando um novo tipo é definido, aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> à classe. Também se aplicam a <xref:System.Runtime.Serialization.DataMemberAttribute> a todos os membros do novo tipo de que precisam ser serializados como parte da declaração de atributo.  
  
         O exemplo de código a seguir define um tipo de recurso personalizado chamado `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  Escolha um direito que é definido pelo WCF ou um valor exclusivo para um direito personalizado.  
  
         Um direito é um identificador de cadeia de caracteres exclusiva. Os direitos que são definidos pelo WCF são definidos na <xref:System.IdentityModel.Claims.Rights> classe.  
  
         É responsabilidade do designer de declaração personalizada para garantir que o identificador de cadeia de caracteres que é usado para a direita é exclusivo.  
  
         O exemplo de código a seguir cria uma declaração personalizada com um tipo de declaração de `http://example.org/claims/complexcustomclaim`, um tipo de recurso personalizado de `MyResourceType`e com o <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> à direita.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como criar uma declaração personalizada com um tipo de recurso primitivos e uma declaração personalizada com um tipo de recurso não primitivo.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
