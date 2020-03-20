---
title: Como criar uma afirmação personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185613"
---
# <a name="how-to-create-a-custom-claim"></a>Como criar uma afirmação personalizada
A infra-estrutura do Modelo de Identidade na Windows Communication Foundation (WCF) fornece um <xref:System.IdentityModel.Claims.Claim> conjunto de tipos e direitos de reclamação incorporados com as funções de ajudante para criar instâncias com esses tipos e direitos. Essas reivindicações incorporadas são projetadas para modelar informações encontradas em tipos de credenciais de clientes que o WCF suporta por padrão. Em muitos casos, as reivindicações incorporadas são suficientes; no entanto, alguns aplicativos podem exigir reivindicações personalizadas. Uma reclamação consiste no tipo de sinistro, o recurso para o qual a reclamação se aplica e o direito que é afirmado sobre esse recurso. Este tópico descreve como criar uma reivindicação personalizada.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Para criar uma reivindicação personalizada que é baseada em um tipo de dados primitivo  
  
1. Crie uma reclamação personalizada passando o tipo de <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> reclamação, o valor do recurso e o direito ao construtor.  
  
    1. Decida sobre um valor único para o tipo de sinistro.  
  
         O tipo de reclamação é um identificador de string único. É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string usado para o tipo de sinistro seja único. Para obter uma lista de tipos de sinistro <xref:System.IdentityModel.Claims.ClaimTypes> definidos pelo WCF, consulte a classe.  
  
    2. Escolha o tipo de dados primitivo e o valor do recurso.  
  
         Um recurso é um objeto. O tipo CLR do recurso pode ser <xref:System.String> <xref:System.Int32>primitivo, como ou , ou qualquer tipo serializável. O tipo CLR do recurso deve ser serializável, porque as reivindicações são serializadas em vários pontos pelo WCF. Tipos primitivos são serializáveis.  
  
    3. Escolha um direito definido pelo WCF ou um valor único para um direito personalizado.  
  
         A direita é um identificador de string único. Os direitos definidos pelo WCF <xref:System.IdentityModel.Claims.Rights> são definidos na classe.  
  
         É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string que é usado para a direita seja único.  
  
         O exemplo de código a seguir cria `http://example.org/claims/simplecustomclaim`uma reclamação `Driver's License`personalizada com <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> um tipo de reclamação de , para um recurso chamado , e com o direito.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Para criar uma reivindicação personalizada baseada em um tipo de dados não primitivo  
  
1. Crie uma reclamação personalizada passando o tipo de <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> reclamação, o valor do recurso e o direito ao construtor.  
  
    1. Decida sobre um valor único para o tipo de sinistro.  
  
         O tipo de reclamação é um identificador de string único. É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string usado para o tipo de sinistro seja único. Para obter uma lista de tipos de sinistro <xref:System.IdentityModel.Claims.ClaimTypes> definidos pelo WCF, consulte a classe.  
  
    2. Escolha ou defina um tipo serializável não primitivo para o recurso.  
  
         Um recurso é um objeto. O tipo CLR do recurso deve ser serializável, porque as reivindicações são serializadas em vários pontos pelo WCF. Tipos primitivos já são serializáveis.  
  
         Quando um novo tipo for <xref:System.Runtime.Serialization.DataContractAttribute> definido, aplique o na classe. Também aplique <xref:System.Runtime.Serialization.DataMemberAttribute> o atributo a todos os membros do novo tipo que precisam ser serializados como parte da reivindicação.  
  
         O exemplo de código a seguir `MyResourceType`define um tipo de recurso personalizado chamado .  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. Escolha um direito definido pelo WCF ou um valor único para um direito personalizado.  
  
         A direita é um identificador de string único. Os direitos definidos pelo WCF <xref:System.IdentityModel.Claims.Rights> são definidos na classe.  
  
         É responsabilidade do designer de reivindicações personalizado garantir que o identificador de string que é usado para a direita seja único.  
  
         O exemplo de código a seguir cria `http://example.org/claims/complexcustomclaim`uma reclamação personalizada `MyResourceType`com um <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> tipo de reclamação de , um tipo de recurso personalizado de , e com o direito.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como criar uma reivindicação personalizada com um tipo de recurso primitivo e uma reivindicação personalizada com um tipo de recurso não primitivo.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Gerenciamento de declarações e autorizações com o modelo de identidade](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
