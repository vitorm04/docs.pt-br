---
title: "Exceções de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0c1b3e921714d104ab2bb5018184a9517c7ad345
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-exceptions"></a>Exceções de segurança
Este tópico lista todas as exceções de segurança.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|O serviço não permite fazer logon anonimamente.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|A mensagem de solicitação deve ser protegida. Isso é necessário por uma operação do contrato especificado. A proteção deve ser fornecida pela associação especificada.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|A mensagem de resposta deve ser protegida. Isso é necessário por uma operação do contrato especificado. A proteção deve ser fornecida pela associação especificada.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|Somente uma assinatura principal é permitida em um cabeçalho de segurança.|  
|BadContextTokenFaultReason|O token de contexto de segurança expirou ou não é válido. A mensagem não foi processada.|  
|BadEncryptionState|O objeto EncryptedData ou EncryptedKey está em um estado inválido para esta operação.|  
|BasicHttpMessageSecurityRequiresCertificate|A associação BasicHttp requer que BasicHttpBinding.Security.Message.ClientCredentialType seja equivalente ao tipo de credencial BasicHttpMessageCredentialType para mensagens seguras. Selecione a segurança de Transport ou de TransportWithMessageCredential para credenciais UserName.|  
|BasicTokenCannotBeWrittenWithoutEncryption|O token básico não pode ser gravado sem criptografia.|  
|BindingDoesNotSupportProtectionForRst|A associação especificada para o contrato especificado é configurada com SecureConversation, mas o modo de autenticação não é capaz de fornecer a integridade baseado em solicitação/resposta e a confidencialidade exigidas para a negociação.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|A operação do contrato especificado requer a identidade do Windows para representação automática. Uma identidade do Windows que representa o chamador não é fornecida pela associação especificada para o contrato especificado.|  
|CachedNegotiationStateQuotaReached|O serviço não pode armazenar em cache o estado da negociação como a capacidade especificada foi atingida. Repita a solicitação.|  
|CacheQuotaReached|O item não pode ser adicionado. O tamanho máximo do cache é especificado.|  
|CannotDetermineSPNBasedOnAddress|Cliente não é possível determinar que o nome da entidade de serviço com base na identidade no endereço de destino especificado com a finalidade de SspiNegotiation/Kerberos. A identidade do endereço de destino deve ser uma identidade UPN (como acmedomain\\\alice) ou uma identidade SPN (como host/bobs-machine).|  
|CannotFindCert|Não é possível localizar o certificado x. 509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue.|  
|CannotFindCertForTarget|Não é possível localizar o certificado x. 509 a usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue para o destino especificado.|  
|CannotFindCorrelationStateForApplyingSecurity|Não é possível localizar o estado de correlação para aplicação de segurança à resposta no Respondente.|  
|CannotFindNegotiationState|Não é possível localizar o estado de negociação para o contexto especificado.|  
|CannotFindSecuritySession|Não é possível encontrar a sessão de segurança com a ID especificada.|  
|CannotImportProtectionLevelForContract|A diretiva para importar um processo não pode importar uma associação para o contrato especificado. Os requisitos de proteção para a associação não são compatíveis com uma associação já importada para o contrato. É necessário reconfigurar a associação.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Falha na importação da política de segurança. A política de segurança contém requisitos de token no escopo da operação de suporte. A descrição do contrato não especifica a ação para a mensagem de solicitação associada a esta operação.|  
|CannotIssueRstTokenType|Não é possível emitir o tipo de token ou especificado.|  
|CannotObtainIssuedTokenKeySize|Não é possível determinar o tamanho da chave do token emitido.|  
|CannotPerformImpersonationOnUsernameToken|Representação usando o token de cliente não é possível. A associação especificada para o contrato especificado usa o Token de segurança do nome de usuário para autenticação de cliente com um provedor de associação registrado. Use um tipo diferente de token de segurança para o cliente.|  
|CannotPerformS4UImpersonationOnPlatform|A associação especificada para o contrato especificado oferece suporte a representação somente em [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] e a versão mais recente do Windows. Use a autenticação SspiNegotiated e uma associação com conversa segura e cancelamento habilitado.|  
|CannotReadKeyIdentifier|Não é possível ler o KeyIdentifier do elemento especificado com o namespace especificado.|  
|CannotReadToken|Não é possível ler o token do elemento especificado com o namespace especificado para BinarySecretSecurityToken, com um ValueType especificado. Se esse elemento deve ser válido, certifique-se de que a segurança é configurada para consumir tokens com o nome, tipo de namespace e o valor especificado.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|Não há suporte para autenticação de cliente baseada em certificado no modo de segurança TransportCredentialOnly. Selecione o modo de segurança de transporte.|  
|ClaimTypeCannotBeEmpty|ClaimType não pode ser uma cadeia de caracteres vazia.|  
|ClientCertificateNotProvided|O certificado para o cliente não foi fornecido. O certificado pode ser definido em ClientCredentials ou ServiceCredentials.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType não é válido para o modo de segurança TransportWithMessageCredential. Especifique um tipo de credencial ou usar um modo de segurança diferente.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|O esquema de configuração não é suficiente para descrever a configuração não padrão do seguinte elemento de associação de segurança:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|A chave derivada especificado resultado da geração e o comprimento em um deslocamento que seja maior que o deslocamento máximo permitido.|  
|DnsIdentityCheckFailedForIncomingMessage|Falhou a verificação de identidade para mensagem de entrada. A identidade do DNS (sistema) do nome de domínio esperado do ponto de extremidade remota foi especificada. O ponto de extremidade remoto forneceu uma declaração de sistema de nomes de domínio especificado (DNS). Se esse for um ponto de extremidade legítimo, você pode corrigir o problema especificando a identidade do sistema de nome de domínio como a propriedade identity de EndpointAddress ao criar um proxy de canal.|  
|DnsIdentityCheckFailedForOutgoingMessage|A verificação de identidade falhou para a mensagem que foi saem. O ponto de extremidade remoto deveria ter a identidade de sistema de nome de domínio especificado. O ponto de extremidade remoto forneceu uma declaração de sistema de nomes de domínio (DNS). Se esse for um ponto de extremidade legítimo, você pode corrigir o problema especificando explicitamente a identidade do DNS como a propriedade Identity de EndpointAddress ao criar um proxy de canal.|  
|DuplicateIdInMessageToBeVerified|A id especificada ocorreu duas vezes na mensagem que é fornecida para verificação.|  
|EmptyBase64Attribute|Um valor vazio foi encontrado para o namespace e nome de atributo necessário de base 64.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Falha na exportação de diretivas de segurança. A ligação contém AsymmetricSecurityBindingElement e um elemento de associação de transporte seguro. Não há suporte para exportação de política para essa associação.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Falha na exportação de diretivas de segurança. A ligação contém SymmetricSecurityBindingElement e um elemento de associação de transporte seguro. Não há suporte para exportação de política para essa associação.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Falha na exportação de diretivas de segurança. A associação contém TransportSecurityBindingElement, mas nenhum elemento de associação de transporte que implemente ITransportTokenAssertionProvider. Não há suporte para exportação de política para essa associação. Verifique se que o elemento de associação de transporte na associação implemente a interface ITransportTokenAssertionProvider.|  
|FoundMultipleCerts|Encontrados vários certificados x. 509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue. Forneça um valor de localização mais específico.|  
|FoundMultipleCertsForTarget|Encontrados vários certificados x. 509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue para o destino especificado. Forneça um valor de localização mais específico.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|Wssecurityjan2004 não oferece suporte a descriptografia de cabeçalho. Use SecurityVersion.WsSecurityXXX2005 e posterior ou use a segurança de transporte para criptografar a mensagem completa.|  
|IdentityCheckFailedForIncomingMessage|Falhou a verificação de identidade para mensagem de entrada. A identidade esperada é especificada para o ponto de extremidade de destino.|  
|IdentityCheckFailedForOutgoingMessage|Falhou a verificação de identidade para mensagem de saída. A identidade esperada é especificada para o ponto de extremidade de destino.|  
|IncorrectSpnOrUpnSpecified|Falha na autenticação da Interface de provedor de suporte (SSPI) de segurança. O servidor pode não estar executando em uma conta com a identidade especificada. Se o servidor estiver em execução em uma conta de serviço (serviço de rede, por exemplo), especifique ServicePrincipalName da conta como identidade na classe EndpointAddress para o servidor. Se o servidor está em execução em uma conta de usuário, especifique UserPrincipalName da conta como identidade na classe EndpointAddress para o servidor.|  
|InvalidAttributeInSignedHeader|O cabeçalho assinado especificado contém o atributo especificado. O atributo esperado é especificado.|  
|InvalidCloseResponseAction|Foi recebida uma resposta de fechamento de sessão de segurança com a ação inválida especificada.|  
|InvalidQName|QName é inválido.|  
|InvalidRenewResponseAction|Resposta de renovação de uma sessão de segurança foi recebida com a ação inválida especificada.|  
|InvalidSspiNegotiation|Falha na negociação de Interface de provedor de suporte de segurança.|  
|IssuerBindingNotPresentInTokenRequirement|O Gerenciador de token de segurança requer que o elemento de associação de segurança de inicialização será necessário especificar o requisito de token que descreve a conversa segura. O requisito de token é especificado da seguinte maneira.|  
|KeyLengthMustBeMultipleOfEight|O comprimento de chave especificado não é um múltiplo de 8 para chaves simétricas.|  
|LsaAuthorityNotContacted|Erro SSL interno (consulte o código de status Win32 para obter detalhes). Verifica o certificado do servidor para determinar se ele é capaz de troca de chaves.|  
|MaximumPolicyRedirectionsExceeded|A política recursiva buscando o limite foi atingida. Verifique se há um loop na cadeia de serviço de Federação.|  
|MessagePartSpecificationMustBeImmutable|Especificação da parte de mensagem deve se tornar constante antes de ser definido.|  
|MissingCustomCertificateValidator|X509CertificateValidationMode. Custom requer CustomCertificateValidator. Especifique a propriedade CustomCertificateValidator.|  
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode. Custom requer CustomUserNamePasswordValidator. Especifique a propriedade CustomUserNamePasswordValidator.|  
|MissingMembershipProvider|UserNamePasswordValidationMode. MembershipProvider requer MembershipProvider. Especifique a propriedade MembershipProvider.|  
|NoBinaryNegoToSend|Nenhuma negociação binária foi enviada à outra parte.|  
|NoEncryptionPartsSpecified|Nenhuma parte de mensagem de criptografia foi especificada para mensagens com a ação especificada.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|O valor de KeyInfo não foi encontrado no item criptografado para localizar a descriptografia de token.|  
|NonceLengthTooShort|O nonce especificado é muito curto. O requisito mínimo de comprimento de nonce é de 4 bytes.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Não há EndpointAddress de saída está disponível para verificar a identidade em uma mensagem a ser enviada.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Não há EndpointAddress de saída está disponível para verificar a identidade em uma resposta recebida.|  
|NoPartsOfMessageMatchedPartsToSign|Nenhuma assinatura foi criada porque nenhuma parte da mensagem correspondeu a especificação da parte de mensagem fornecida.|  
|NoPrincipalSpecifiedInAuthorizationContext|Nenhuma entidade de segurança personalizada está especificada no contexto de autorização.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Nenhuma assinatura está disponível no cabeçalho de segurança a ser fornecido ao nonce para detecção de repetição.|  
|NoSignaturePartsSpecified|Nenhuma parte de mensagem de assinatura foi especificada para mensagens com a ação especificada.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Nenhum token de assinatura está disponível para realizar uma verificação de identidade de entrada.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Nenhum timestamp está disponível no cabeçalho de segurança para fazer a detecção de repetição.|  
|NoTransportTokenAssertionProvided|A política de segurança especializada falha. A declaração de token de transporte fornecida do tipo especificado não criou uma declaração de token de transporte para incluir a declaração de política de segurança sp:TransportBinding.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|O protocolo de segurança simétrica pode ser configurado com um provedor de token simétrico e um autenticador de token simétrico ou um provedor de token assimétrico. Ele não pode ser configurado com ambos.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Esta operação não pode ser feita nos cabeçalhos de segurança do destinatário.|  
|OperationDoesNotAllowImpersonation|A operação de serviço especificado pertence ao contrato com o nome especificado e o namespace não permite representação.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Política de segurança de mensagem para a ação especificada requer confidencialidade sem integridade. Não há suporte para confidencialidade sem integridade.|  
|PrimarySignatureIsRequiredToBeEncrypted|A assinatura principal deve ser criptografada.|  
|PropertySettingErrorOnProtocolFactory|A propriedade necessária na fábrica de protocolo de segurança especificado não está definida ou possui um valor inválido.|  
|ProtocolFactoryCouldNotCreateProtocol|A fábrica de protocolo não pode criar um protocolo.|  
|PublicKeyNotRSA|A chave pública não é uma chave RSA.|  
|RequiredMessagePartNotEncrypted|A parte da mensagem necessária especificada não foi criptografada.|  
|RequiredMessagePartNotEncryptedNs|A parte da mensagem necessária especificada não foi criptografada.|  
|RequiredMessagePartNotSigned|A parte da mensagem necessária especificada não foi assinada.|  
|RequiredMessagePartNotSignedNs|A parte da mensagem necessária especificada não foi assinada.|  
|RequiredSecurityHeaderElementNotSigned|O elemento de cabeçalho de segurança especificada com a id especificada deve ser assinado.|  
|RequiredSecurityTokenNotEncrypted|Especificado ' token de segurança com o modo de anexo especificado deve ser criptografado.|  
|RequiredSecurityTokenNotSigned|O token de segurança especificada com o modo de anexo especificado deve ser assinado.|  
|RequiredSignatureMissing|A assinatura deve estar no cabeçalho de segurança.|  
|RequireNonCookieMode|A associação especificada com o namespace especificado está configurada para emitir tokens de contexto de segurança do cookie. Serviços de integração de COM+ não oferece suporte a tokens de contexto de segurança do cookie.|  
|RevertingPrivilegeFailed|Falha na operação de reversão com a exceção especificada.|  
|RSTRAuthenticatorIncorrect|CombinedHash de RequestSecurityTokenResponse está incorreto.|  
|SecureConversationCancelNotAllowedFaultReason|Um cancelamento de conversa segura não é permitido pela associação.|  
|SecureConversationDriverVersionDoesNotSupportSession|A versão configurada de SecureConversation não oferece suporte a sessões. Use WSSecureConversationFeb2005 ou superior.|  
|SecureConversationRequiredByReliableSession|Não é possível estabelecer uma sessão confiável sem conversa segura. Habilite a conversa segura.|  
|SecurityAuditFailToLoadDll|Especificado biblioteca de vínculo dinâmico (dll) não pôde ser carregado.|  
|SecurityAuditNotSupportedOnChannelFactory|Não há suporte para SecurityAuditBehavior na fábrica de canais.|  
|SecurityAuditPlatformNotSupported|Não há suporte para a gravação de mensagens de auditoria no log de segurança na plataforma atual. Você deve gravar mensagens de auditoria no log de aplicativo.|  
|SecurityBindingElementCannotBeExpressedInConfig|Uma política de segurança foi importada para o ponto de extremidade. A política de segurança contém requisitos que não podem ser representados em uma configuração do Windows Communication Foundation. Pesquise um comentário sobre os parâmetros SecurityBindingElement que são necessários no arquivo de configuração que foi gerado. Crie o elemento de associação correto com código. A configuração de associação no arquivo de configuração não é segura.|  
|SecurityBindingSupportsOneWayOnly|A SecurityBinding para a associação especificada para o contrato especificado só dá suporte a uma operação OneWay.|  
|SecurityContextDoesNotAllowImpersonation|Não é possível iniciar representação porque SecurityContext para a função UltimateReceiver da mensagem de solicitação com a ação especificada não está mapeada para uma identidade do Windows.|  
|SecurityListenerClosing|O ouvinte não está aceitando novas conversas seguras porque está fechando.|  
|SecurityListenerClosingFaultReason|O servidor não está aceitando novas conversas seguras atualmente porque está fechando. Tente novamente mais tarde.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|A fábrica de protocolo de segurança deve ser definida antes desta operação é executada.|  
|SecuritySessionAbortedFaultReason|A sessão de segurança foi terminada. Isso pode ocorrer porque não há mensagens recebidas na sessão por muito tempo.|  
|SecuritySessionKeyIsStale|A chave de sessão deve ser renovada para que possa proteger as mensagens de aplicativo.|  
|SecuritySessionLimitReached|Não é possível criar uma sessão de segurança. Tente novamente mais tarde.|  
|SecuritySessionNotPending|Nenhuma sessão de segurança com a id especificada está pendente.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|A associação especificada está configurada com um parâmetro de token de segurança que tem o modo de inclusão de token de segurança incompatível especificado. Especifique um modo de inclusão de token de segurança alternativa.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|A associação especificada para o contrato especificado foi configurada com uma versão incompatível de segurança que não oferece suporte a referências não anexadas a EncryptedKeys. Use o valor especificado ou superior como a versão de segurança para a associação.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|O SecurityVersion especificado não oferece suporte a confirmação de assinatura. Use uma SecurityVersion posterior.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|A associação especificada para o contrato especificado está configurada com uma versão de segurança que não oferece suporte a referências externas para tokens x. 509 usando o valor de impressão digital do certificado. Use o valor especificado ou superior como a versão de segurança para a associação.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Parâmetros de token de segurança devem ser especificados com os tokens de suporte para cada mensagem.|  
|ServerCertificateNotProvided|O destinatário não forneceu seu certificado. Este certificado é exigido pelo protocolo TLS. Ambas as partes devem ter acesso a seus certificados.|  
|SignatureConfirmationNotSupported|O SecurityVersion configurado não oferece suporte a confirmação de assinatura. Use WSSecurityXXX2005 ou superior.|  
|SignatureConfirmationRequiresRequestReply|A fábrica de protocolos deve oferecer suporte a segurança de solicitação/resposta para oferecer confirmação de assinatura.|  
|SignatureNotExpected|Uma assinatura não é esperada para esta mensagem.|  
|SigningTokenHasNoKeys|O token de autenticação especificado não possui nenhuma chave. O token de segurança é usado em um contexto que requer que sejam realizadas operações de criptografia, mas o token não contém nenhuma chave de criptografia. Ou o tipo de token não oferece suporte a operações de criptografia ou a instância particular do token não contém chaves de criptografia. Verifique a configuração para garantir que tipos de token (por exemplo, UserNameSecurityToken) com criptografia desabilitada não são especificados em um contexto que exija operações de criptografia (por exemplo, um um token de suporte).|  
|SpnegoImpersonationLevelCannotBeSetToNone|A Interface de provedor de suporte de segurança não aceita representação 'None' nível. Especifique o nível de identificação, representação ou delegação.|  
|SslClientCertMustHavePrivateKey|O certificado especificado deve ter uma chave privada. O processo deve ter direitos de acesso para a chave privada.|  
|SslServerCertMustDoKeyExchange|O certificado especificado deve ter uma chave privada que é capaz de troca de chaves. O processo deve ter direitos de acesso para a chave privada.|  
|StandardsManagerCannotWriteObject|O serializador de token não é possível serializar o objeto especificado.  Se este for um tipo personalizado, você deve fornecer um serializador personalizado.|  
|TimeStampHasCreationAheadOfExpiry|O carimbo de hora de segurança é inválido porque sua hora de criação é maior que ou igual a seu tempo de expiração.|  
|TimeStampHasCreationTimeInFuture|O carimbo de hora de segurança é inválido porque sua hora de criação é no futuro. Hora atual for especificada e a defasagem horária permitida é especificada.|  
|TimeStampHasExpiryTimeInPast|O carimbo de hora de segurança é obsoleto porque seu tempo de expiração está no passado. Hora atual for especificada e a defasagem horária permitida é especificada.|  
|TimeStampWasCreatedTooLongAgo|O carimbo de hora de segurança é obsoleto porque sua hora de criação é muito distante no passado. Hora atual, o tempo de vida máximo de carimbo de hora e a defasagem horária permitida são especificados.|  
|TokenProviderCannotGetTokensForTarget|O provedor de token não pode obter tokens para o destino especificado.|  
|TooManyIssuedSecurityTokenParameters|Um trecho da cadeia de segurança federada contém vários IssuedSecurityTokenParameters. O sistema InfoCard apenas oferece suporte a um IssuedSecurityTokenParameters para cada trecho.|  
|TransportDoesNotProtectMessage|A associação especificada para o contrato especificado está configurada com um modo de autenticação que requer confidencialidade e a integridade de nível de transporte. No entanto, o transporte não pode fornecer integridade e confidencialidade.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 não oferece suporte para a emissão de certificados x. 509 ou EncryptedKeys. Use WsTrustFeb2005 ou superior.|  
|TrustDriverVersionDoesNotSupportSession|A versão de confiança configurada não oferece suporte a sessões. Use WSTrustFeb2005 ou superior.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Não é possível criar uma interface ICrypto do token especificado para verificação de assinatura.|  
|UnableToCreateSymmetricAlgorithmFromToken|Não é possível criar o algoritmo simétrico especificado do token.|  
|UnableToDeriveKeyFromKeyInfoClause|A cláusula KeyInfo especificada resolvida para o token especificado, o que não contém uma chave simétrica que pode ser usada para derivação.|  
|UnableToFindTokenAuthenticator|Não é possível encontrar um autenticador de token para o tipo de token especificado. Tokens desse tipo não podem ser aceitos de acordo com as configurações de segurança atual.|  
|UnableToLoadCertificateIdentity|Não é possível carregar a identidade de certificado x. 509 especificada na configuração.|  
|UnexpectedEmptyElementExpectingClaim|O elemento especificado do namespace especificado está vazio e não especifica uma declaração de identidade válida.|  
|UnknownEncodingInBinarySecurityToken|Codificação não reconhecida ao tentar ler o token de segurança binário.|  
|UnsecuredMessageFaultReceived|Uma falha protegida incorretamente ou não foi recebida da outra parte. Veja a FaultException interna para o código de falha e os detalhes.|  
|UnsupportedPasswordType|O token de nome de usuário especificado tem um tipo de senha sem suporte.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Não é possível importar a política de segurança. Não há suporte para os requisitos de proteção para a associação de inicialização de conversa segura. Requisitos de proteção para a inicialização de conversa segura devem exigir a solicitação e a resposta sejam autenticados e criptografados.|  
|UnsupportedSecurityPolicyAssertion|Uma declaração de política de segurança sem suporte foi detectada durante a importação da política de segurança especificados.|
