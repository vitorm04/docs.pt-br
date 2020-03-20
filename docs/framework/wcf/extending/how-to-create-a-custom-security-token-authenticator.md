---
title: 'Como: criar um autenticador de token de segurança personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
ms.openlocfilehash: 7bbe59958f59f76046c0a112463cfa64d09c14d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185582"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Como: criar um autenticador de token de segurança personalizado
Este tópico mostra como criar um autenticador de token de segurança personalizado e como integrá-lo com um gerenciador de tokens de segurança personalizado. Um autenticador de token de segurança valida o conteúdo de um token de segurança fornecido com uma mensagem recebida. Se a validação for bem-sucedida, <xref:System.IdentityModel.Policy.IAuthorizationPolicy> o autenticador retorna uma coleção de instâncias que, quando avaliadas, retorna um conjunto de reclamações.  
  
 Para usar um autenticador de token de segurança personalizado no Windows Communication Foundation (WCF), você deve primeiro criar credenciais personalizadas e implementações de gerenciadores de tokens de segurança. Para obter mais informações sobre a criação de credenciais personalizadas e um gerenciador de tokens de segurança, consulte [Passo a Passo: Criando credenciais personalizadas de clientes e serviços.](walkthrough-creating-custom-client-and-service-credentials.md)
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Para criar um autenticador de token de segurança personalizado  
  
1. Defina uma nova classe <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> derivada da classe.  
  
2. Substituir o método <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A>. O método `true` `false` retorna ou dependendo se o autenticador personalizado pode validar ou não o tipo de token de entrada.  
  
3. Substituir o método <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A>. Este método precisa validar o conteúdo do token adequadamente. Se o token passar pela etapa de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> validação, ele retorna uma coleção de instâncias. O exemplo a seguir usa uma implementação de política de autorização personalizada que será criada no próximo procedimento.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 O código anterior devolve uma coleção <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> de políticas de autorização no método. O WCF não fornece uma implementação pública desta interface. O procedimento a seguir mostra como fazê-lo para suas próprias necessidades.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Para criar uma política de autorização personalizada  
  
1. Defina uma nova <xref:System.IdentityModel.Policy.IAuthorizationPolicy> classe implementando a interface.  
  
2. Implemente <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> a propriedade somente leitura. Uma maneira de implementar essa propriedade é gerar um identificador globalmente único (GUID) no construtor de classe e devolvê-lo toda vez que o valor para esta propriedade for solicitado.  
  
3. Implemente <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> a propriedade somente leitura. Essa propriedade precisa devolver um emissor dos conjuntos de sinistros que são obtidos a partir do token. Este emissor deve corresponder ao emissor do token ou a uma autoridade responsável pela validação do conteúdo do token. O exemplo a seguir usa a reivindicação do emissor que passou para esta classe a partir do autenticador de token de segurança personalizado criado no procedimento anterior. O autenticador de token de segurança personalizado usa o <xref:System.IdentityModel.Claims.ClaimSet.System%2A> conjunto de reclamações fornecido pelo sistema (devolvido pela propriedade) para representar o emissor do token de nome de usuário.  
  
4. Implementar o método de <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> . Esse método preenche uma <xref:System.IdentityModel.Policy.EvaluationContext> instância da classe (aprovada como argumento) com alegações baseadas no conteúdo do token de segurança de entrada. O método `true` retorna quando é feito com a avaliação. Nos casos em que a implementação se baseia na presença de outras `false` políticas de autorização que forneçam informações adicionais ao contexto de avaliação, esse método pode retornar se as informações necessárias ainda não estarem presentes no contexto de avaliação. Nesse caso, o WCF chamará o método novamente após avaliar todas as outras políticas de autorização geradas para a mensagem recebida se pelo menos uma dessas políticas de autorização modificar o contexto de avaliação.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [Passo a passo: A criação de credenciais personalizadas de clientes e serviços](walkthrough-creating-custom-client-and-service-credentials.md) descreve como criar credenciais personalizadas e um gerenciador de tokens de segurança personalizado. Para usar o autenticador de token de segurança personalizado criado aqui, uma implementação do <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> gerenciador de tokens de segurança é modificada para devolver o autenticador personalizado do método. O método retorna um autenticador quando um requisito de token de segurança apropriado é aprovado.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Para integrar um autenticador de token de segurança personalizado com um gerenciador de tokens de segurança personalizado  
  
1. Anular o <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> método na implementação do gerenciador de tokens de segurança personalizado.  
  
2. Adicione lógica ao método para permitir que ele retorne seu <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> autenticador de token de segurança personalizado com base no parâmetro. O exemplo a seguir retorna um autenticador de token de segurança personalizado se <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> o tipo de token requisitos de token for um nome <xref:System.ServiceModel.Description.MessageDirection.Input> de usuário (representado pela propriedade) e a direção de mensagem para a qual o autenticador de token de segurança está sendo solicitado é a entrada (representada pelo campo).  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  

## <a name="see-also"></a>Confira também

- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.UserNameSecurityToken>
- [Passo a passo de criação de credenciais de serviço e cliente personalizados](walkthrough-creating-custom-client-and-service-credentials.md)
- [Como criar um fornecedor de token de segurança personalizado](how-to-create-a-custom-security-token-provider.md)
