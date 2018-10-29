---
title: Exceções de segurança
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: c1eeca9111837b9833de54ecafbc981d1c2b6343
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201368"
---
# <a name="security-exceptions"></a>Exceções de segurança
Este tópico lista todas as exceções de segurança.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|O serviço não permite que você faça logon anonimamente.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|A mensagem de solicitação deve ser protegida. Isso é necessário por uma operação de contrato especificado. A proteção deve ser fornecida pela associação especificada.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|A mensagem de resposta deve ser protegida. Isso é necessário por uma operação de contrato especificado. A proteção deve ser fornecida pela associação especificada.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|Somente uma assinatura principal é permitida em um cabeçalho de segurança.|  
|BadContextTokenFaultReason|O token de contexto de segurança expirou ou não é válido. A mensagem não foi processada.|  
|BadEncryptionState|O objeto EncryptedData ou EncryptedKey está em um estado inválido para esta operação.|  
|BasicHttpMessageSecurityRequiresCertificate|A associação BasicHttp requer que BasicHttpBinding.Security.Message.ClientCredentialType seja equivalente ao tipo de credencial BasicHttpMessageCredentialType para mensagens seguras. Selecione segurança de transporte ou de TransportWithMessageCredential para credenciais UserName.|  
|BasicTokenCannotBeWrittenWithoutEncryption|O token básico não pode ser escrito sem criptografia.|  
|BindingDoesNotSupportProtectionForRst|A associação especificada para o contrato especificado está configurada com SecureConversation, mas o modo de autenticação não é capaz de fornecer o necessário para a negociação de confidencialidade e integridade de baseadas em solicitação/resposta.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|A operação de contrato especificado requer a identidade do Windows para a representação automática. Uma identidade de Windows que representa o chamador não é fornecida pela associação especificada para o contrato especificado.|  
|CachedNegotiationStateQuotaReached|O serviço não pode armazenar em cache o estado de negociação como a capacidade especificada foi atingida. Repita a solicitação.|  
|CacheQuotaReached|O item não pode ser adicionado. O tamanho máximo do cache é especificado.|  
|CannotDetermineSPNBasedOnAddress|Cliente não pode determinar que o nome da entidade de serviço com base na identidade, o endereço de destino especificado com a finalidade de destinado a SspiNegotiation/Kerberos. A identidade de endereço de destino deve ser uma identidade UPN (como acmedomain\\\alice) ou uma identidade SPN (como host/bobs-machine).|  
|CannotFindCert|Não é possível localizar o certificado X.509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue.|  
|CannotFindCertForTarget|Não é possível localizar o certificado X.509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue para o destino especificado.|  
|CannotFindCorrelationStateForApplyingSecurity|Não é possível localizar o estado de correlação para a aplicação de segurança para responder em que o respondente.|  
|CannotFindNegotiationState|Não é possível localizar o estado de negociação para o contexto especificado.|  
|CannotFindSecuritySession|Não é possível encontrar a sessão de segurança com a ID especificada.|  
|CannotImportProtectionLevelForContract|A política para um processo de importação não é possível importar uma associação para o contrato especificado. Os requisitos de proteção para a associação não são compatíveis com uma associação já importada para o contrato. Você deve reconfigurar a associação.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Falha na importação da política de segurança. A política de segurança contém requisitos de token no escopo da operação de suporte. A descrição do contrato não especifica a ação para a mensagem de solicitação associada a esta operação.|  
|CannotIssueRstTokenType|Não é possível emitir o tipo de token ou especificado.|  
|CannotObtainIssuedTokenKeySize|Não é possível determinar o tamanho da chave do token emitido.|  
|CannotPerformImpersonationOnUsernameToken|Usando o token de cliente de representação não é possível. A associação especificada para o contrato especificado usa o Token de segurança do nome de usuário para autenticação de cliente com um provedor de associação registrado. Use um tipo diferente de token de segurança para o cliente.|  
|CannotPerformS4UImpersonationOnPlatform|A associação especificada para o contrato especificado dá suporte à representação somente em [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] e a versão mais recente do Windows. Use autenticação SspiNegotiated e uma associação com Secure Conversation com cancelamento habilitado.|  
|CannotReadKeyIdentifier|Não é possível ler o KeyIdentifier do elemento especificado com o namespace especificado.|  
|CannotReadToken|Não é possível ler o token do elemento especificado com o namespace especificado para BinarySecretSecurityToken, com um ValueType especificado. Se esse elemento deve ser válido, certifique-se de que a segurança é configurada para consumir tokens com o nome, namespace e tipo de valor especificado.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|Não há suporte para autenticação de cliente baseada em certificado no modo de segurança TransportCredentialOnly. Selecione o modo de segurança de transporte.|  
|ClaimTypeCannotBeEmpty|O claimType não pode ser uma cadeia de caracteres vazia.|  
|ClientCertificateNotProvided|O certificado para o cliente não foi fornecido. O certificado pode ser definido em ClientCredentials ou ServiceCredentials.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType não é válido para o modo de segurança TransportWithMessageCredential. Especifique um tipo de credencial ou use um modo de segurança diferente.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|O esquema de configuração é suficiente para descrever a configuração não padrão do seguinte elemento de associação de segurança:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|A chave derivada especificada geração e o comprimento de resultado em um deslocamento de derivação de chave que é maior que o deslocamento máximo permitido.|  
|DnsIdentityCheckFailedForIncomingMessage|Falha de verificação de identidade para mensagem de entrada. A identidade do DNS (sistema) do nome de domínio desejado do ponto de extremidade remota foi especificada. O ponto de extremidade remoto fornecido de declaração (DNS) do sistema de nomes de domínio especificado. Se esse for um ponto de extremidade remoto legítimo, você pode corrigir o problema com a especificação de identidade do sistema de nome de domínio como a propriedade identity de EndpointAddress ao criar um proxy de canal.|  
|DnsIdentityCheckFailedForOutgoingMessage|Falha de verificação de identidade para a mensagem que foi saem. O ponto de extremidade remoto deve ter tido a identidade de sistema de nome de domínio especificado. O ponto de extremidade remoto fornecido de declaração de sistema de nomes de domínio (DNS). Se esse for um ponto de extremidade remoto legítimo, você pode corrigir o problema especificando explicitamente identidade DNS como a propriedade Identity de EndpointAddress ao criar um proxy de canal.|  
|DuplicateIdInMessageToBeVerified|A id especificada ocorreu duas vezes na mensagem que é fornecida para verificação.|  
|EmptyBase64Attribute|Um valor vazio foi encontrado para o namespace e nome de atributo necessário de base 64.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Falha na exportação de política de segurança. A ligação contém AsymmetricSecurityBindingElement e um elemento de associação de transporte seguro. Não há suporte para exportação de política para essa associação.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Falha na exportação de política de segurança. A ligação contém SymmetricSecurityBindingElement e um elemento de associação de transporte seguro. Não há suporte para exportação de política para essa associação.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Falha na exportação de política de segurança. A associação contém TransportSecurityBindingElement, mas nenhum elemento de associação de transporte que implemente ITransportTokenAssertionProvider. Não há suporte para exportação de política para essa associação. Verifique se que o elemento de associação de transporte na associação implementa a interface ITransportTokenAssertionProvider.|  
|FoundMultipleCerts|Encontrados vários certificados X.509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue. Forneça um valor de localização mais específico.|  
|FoundMultipleCertsForTarget|Encontrados vários certificados X.509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue para o destino especificado. Forneça um valor de localização mais específico.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|SecurityVersion.WSSecurityJan2004 não oferece suporte a descriptografia de cabeçalho. Use SecurityVersion.WsSecurityXXX2005 e acima ou usar a segurança de transporte para criptografar a mensagem completa.|  
|IdentityCheckFailedForIncomingMessage|Falha de verificação de identidade para mensagem de entrada. A identidade esperada é especificada para o ponto de extremidade de destino.|  
|IdentityCheckFailedForOutgoingMessage|Falha de verificação de identidade para mensagem de saída. A identidade esperada é especificada para o ponto de extremidade de destino.|  
|IncorrectSpnOrUpnSpecified|Falha na autenticação da Interface de provedor de suporte (SSPI) de segurança. O servidor pode não estar executando em uma conta com a identidade especificada. Se o servidor estiver em execução em uma conta de serviço (serviço de rede, por exemplo), especifique ServicePrincipalName da conta como a identidade na classe EndpointAddress para o servidor. Se o servidor está em execução em uma conta de usuário, especifique UserPrincipalName da conta como identidade na classe EndpointAddress para o servidor.|  
|InvalidAttributeInSignedHeader|O cabeçalho assinado especificado contém o atributo especificado. O atributo esperado é especificado.|  
|InvalidCloseResponseAction|Uma resposta de fechamento de sessão de segurança foi recebida com a ação inválida especificada.|  
|InvalidQName|O QName é inválido.|  
|InvalidRenewResponseAction|Uma sessão de segurança renovar a resposta foi recebida com a ação inválida especificada.|  
|InvalidSspiNegotiation|Falha na negociação do Security Support Provider Interface.|  
|IssuerBindingNotPresentInTokenRequirement|O Gerenciador de token de segurança requer que o elemento de associação de segurança de inicialização a ser especificado no requisito de token que descreve a conversa segura. O requisito de token é especificado da seguinte maneira.|  
|KeyLengthMustBeMultipleOfEight|O comprimento da chave especificada não é um múltiplo de 8 para chaves simétricas.|  
|LsaAuthorityNotContacted|Erro interno de SSL (consulte o código de status Win32 para obter detalhes). Verifique o certificado do servidor para determinar se ele é capaz de troca de chaves.|  
|MaximumPolicyRedirectionsExceeded|A política recursiva buscando o limite foi atingida. Verifique se há um loop na cadeia de serviço de Federação.|  
|MessagePartSpecificationMustBeImmutable|Especificação de parte da mensagem deve ser feita constante antes de ser definido.|  
|MissingCustomCertificateValidator|X509CertificateValidationMode.Custom requer CustomCertificateValidator. Especifique a propriedade CustomCertificateValidator.|  
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode.Custom requer CustomUserNamePasswordValidator. Especifique a propriedade CustomUserNamePasswordValidator.|  
|MissingMembershipProvider|UserNamePasswordValidationMode requer MembershipProvider. Especifique a propriedade MembershipProvider.|  
|NoBinaryNegoToSend|Nenhuma negociação binária foi enviada para a outra parte.|  
|NoEncryptionPartsSpecified|Nenhuma parte de mensagem de criptografia foi especificada para mensagens com a ação especificada.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|O valor de KeyInfo não foi encontrado no item criptografado para localizar a descriptografia de token.|  
|NonceLengthTooShort|O nonce especificado é muito curto. O mínimo necessário de comprimento de nonce é de 4 bytes.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Nenhuma saída EndpointAddress está disponível para verificar a identidade em uma mensagem a ser enviada.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Nenhuma saída EndpointAddress está disponível para verificar a identidade em uma resposta recebida.|  
|NoPartsOfMessageMatchedPartsToSign|Nenhuma assinatura foi criada porque nenhuma parte da mensagem corresponde a especificação de parte da mensagem fornecida.|  
|NoPrincipalSpecifiedInAuthorizationContext|Nenhuma entidade de segurança personalizada é especificada no contexto de autorização.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Nenhuma assinatura está disponível no cabeçalho de segurança para fornecer o nonce para detecção de reprodução.|  
|NoSignaturePartsSpecified|Nenhuma parte de mensagem de assinatura foi especificada para mensagens com a ação especificada.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Nenhum token de assinatura está disponível para fazer uma verificação de identidade de entrada.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Não há carimbo de hora está disponível no cabeçalho de segurança para a detecção de reprodução.|  
|NoTransportTokenAssertionProvided|Falha na política de segurança especializada. A declaração de token de transporte fornecida do tipo especificado não tiver criado uma declaração de token de transporte para incluir a declaração de política de segurança SP: TransportBinding.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|O protocolo de segurança simétrica pode ser configurado com um provedor de token simétrico e um autenticador de token simétrico ou um provedor de token assimétrico. Ele não pode ser configurado com ambos.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Esta operação não pode ser feita nos cabeçalhos de segurança do receptor.|  
|OperationDoesNotAllowImpersonation|A operação de serviço especificado pertence ao contrato com o nome especificado e o namespace não permite a representação.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Política de segurança de mensagem para a ação especificada requer confidencialidade sem integridade. Não há suporte para confidencialidade sem integridade.|  
|PrimarySignatureIsRequiredToBeEncrypted|A assinatura principal deve ser criptografada.|  
|PropertySettingErrorOnProtocolFactory|A propriedade necessária na fábrica de protocolo de segurança especificado não está definida ou tem um valor inválido.|  
|ProtocolFactoryCouldNotCreateProtocol|A fábrica de protocolos não é possível criar um protocolo.|  
|PublicKeyNotRSA|A chave pública não é uma chave RSA.|  
|RequiredMessagePartNotEncrypted|A parte da mensagem necessária especificada não foi criptografada.|  
|RequiredMessagePartNotEncryptedNs|A parte da mensagem necessária especificada não foi criptografada.|  
|RequiredMessagePartNotSigned|A parte da mensagem necessária especificada não foi assinada.|  
|RequiredMessagePartNotSignedNs|A parte da mensagem necessária especificada não foi assinada.|  
|RequiredSecurityHeaderElementNotSigned|O elemento de cabeçalho de segurança especificado com a id especificada deve ser assinado.|  
|RequiredSecurityTokenNotEncrypted|Especificado ' token de segurança com o modo de anexo especificado deve ser criptografado.|  
|RequiredSecurityTokenNotSigned|O token de segurança especificado com o modo de anexo especificado deve ser assinado.|  
|RequiredSignatureMissing|A assinatura deve estar no cabeçalho de segurança.|  
|RequireNonCookieMode|A associação especificada com o namespace especificado está configurada para emitir tokens de contexto de segurança do cookie. COM+ Integration services não oferece suporte a tokens de contexto de segurança do cookie.|  
|RevertingPrivilegeFailed|Falha de operação de reversão com a exceção especificada.|  
|RSTRAuthenticatorIncorrect|O RequestSecurityTokenResponse CombinedHash está incorreto.|  
|SecureConversationCancelNotAllowedFaultReason|Um cancelamento de conversa segura não é permitido pela associação.|  
|SecureConversationDriverVersionDoesNotSupportSession|A versão configurada de SecureConversation não oferece suporte a sessões. Use WSSecureConversationFeb2005 ou superior.|  
|SecureConversationRequiredByReliableSession|Não é possível estabelecer uma sessão confiável sem conversa segura. Habilite a conversa segura.|  
|SecurityAuditFailToLoadDll|A biblioteca especificada de vínculo dinâmico (dll) falhou ao carregar.|  
|SecurityAuditNotSupportedOnChannelFactory|Não há suporte para SecurityAuditBehavior na fábrica de canais.|  
|SecurityAuditPlatformNotSupported|Não há suporte para gravar mensagens de auditoria no log de segurança na plataforma atual. Você deve escrever as mensagens de auditoria no log de aplicativo.|  
|SecurityBindingElementCannotBeExpressedInConfig|Uma política de segurança foi importada para o ponto de extremidade. A política de segurança contém requisitos que não podem ser representados em uma configuração do Windows Communication Foundation. Procure um comentário sobre os parâmetros SecurityBindingElement que são necessários no arquivo de configuração que foi gerado. Crie o elemento de associação correto com código. A configuração de associação que está no arquivo de configuração não é segura.|  
|SecurityBindingSupportsOneWayOnly|O SecurityBinding para a associação especificada para o contrato especificado dá suporte apenas a operação de OneWay.|  
|SecurityContextDoesNotAllowImpersonation|Não é possível iniciar representação porque SecurityContext para a função UltimateReceiver da mensagem de solicitação com a ação especificada não está mapeado para uma identidade do Windows.|  
|SecurityListenerClosing|O ouvinte não está aceitando novas conversas seguras porque está fechando.|  
|SecurityListenerClosingFaultReason|O servidor não está aceitando novas conversas seguras no momento porque está sendo fechada. Tente novamente mais tarde.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|A fábrica de protocolos de segurança deve ser definida antes que essa operação é executada.|  
|SecuritySessionAbortedFaultReason|A sessão de segurança foi encerrada. Isso pode ser porque nenhuma mensagem foram recebidas na sessão por muito tempo.|  
|SecuritySessionKeyIsStale|A chave de sessão deve ser renovada antes que possa proteger mensagens de aplicativo.|  
|SecuritySessionLimitReached|Não é possível criar uma sessão de segurança. Tente novamente mais tarde.|  
|SecuritySessionNotPending|Nenhuma sessão de segurança com a id especificada está pendente.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|A associação especificada é configurada com um parâmetro de token de segurança que tem o modo de inclusão de token de segurança incompatível especificado. Especifique um modo de inclusão de token de segurança alternativa.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|A associação especificada para o contrato especificado foi configurada com uma versão incompatível de segurança que não oferece suporte a referências desconectadas para EncryptedKeys. Use o valor especificado ou superior como a versão de segurança para a associação.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|O SecurityVersion especificado não oferece suporte a confirmação de assinatura. Use um SecurityVersion posterior.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|A associação especificada para o contrato especificado está configurada com uma versão de segurança que não oferece suporte a referências externas para tokens de x. 509 usando o valor de impressão digital do certificado. Use o valor especificado ou superior como a versão de segurança para a associação.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Parâmetros de token de segurança devem ser especificados com tokens de suporte para cada mensagem.|  
|ServerCertificateNotProvided|O destinatário não forneceu seu certificado. Este certificado é exigido pelo protocolo TLS. Ambas as partes devem ter acesso a seus certificados.|  
|SignatureConfirmationNotSupported|O SecurityVersion configurado não oferece suporte a confirmação de assinatura. Use WSSecurityXXX2005 ou superior.|  
|SignatureConfirmationRequiresRequestReply|A fábrica de protocolos deve oferecer suporte a segurança de solicitação/resposta para oferecer a confirmação de assinatura.|  
|SignatureNotExpected|Uma assinatura não é esperada para esta mensagem.|  
|SigningTokenHasNoKeys|O token de assinatura especificado não possui chaves. O token de segurança é usado em um contexto que precisa dele para executar operações de criptografia, mas o token não contém nenhuma chave de criptografia. Ou o tipo de token não oferece suporte a operações de criptografia ou a instância particular do token não contém chaves de criptografia. Verifique sua configuração para garantir que os tipos de token (por exemplo, UserNameSecurityToken) com criptografia desabilitada não são especificados em um contexto que exija operações de criptografia (por exemplo, um endosso token de suporte).|  
|SpnegoImpersonationLevelCannotBeSetToNone|A Interface de provedor de suporte de segurança não aceita representação 'None' nível. Especifique o nível de identificação, representação ou delegação.|  
|SslClientCertMustHavePrivateKey|O certificado especificado deve ter uma chave privada. O processo deve ter direitos de acesso para a chave privada.|  
|SslServerCertMustDoKeyExchange|O certificado especificado deve ter uma chave privada que é capaz de troca de chaves. O processo deve ter direitos de acesso para a chave privada.|  
|StandardsManagerCannotWriteObject|O serializador de token não é possível serializar o objeto especificado.  Se este for um tipo personalizado, você deve fornecer um serializador personalizado.|  
|TimeStampHasCreationAheadOfExpiry|O carimbo de hora de segurança é inválido porque sua hora de criação é maior que ou igual ao seu tempo de expiração.|  
|TimeStampHasCreationTimeInFuture|O carimbo de hora de segurança é inválido porque sua hora de criação está no futuro. Hora atual for especificada e a distorção horária permitida é especificada.|  
|TimeStampHasExpiryTimeInPast|O carimbo de hora de segurança é obsoleto porque sua hora de expiração está no passado. Hora atual for especificada e a distorção horária permitida é especificada.|  
|TimeStampWasCreatedTooLongAgo|O carimbo de hora de segurança é obsoleto porque sua hora de criação é muito distante no passado. Hora atual, o tempo de vida máximo do carimbo de hora e a distorção horária permitida são especificados.|  
|TokenProviderCannotGetTokensForTarget|O provedor de token não é possível obter tokens para o destino especificado.|  
|TooManyIssuedSecurityTokenParameters|Um trecho da cadeia de segurança federada contém vários IssuedSecurityTokenParameters. O sistema InfoCard só dá suporte a um IssuedSecurityTokenParameters para cada segmento.|  
|TransportDoesNotProtectMessage|A associação especificada para o contrato especificado está configurada com um modo de autenticação que requer confidencialidade e integridade de nível de transporte. No entanto, o transporte não pode fornecer confidencialidade e integridade.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 não oferece suporte para emitir certificados x. 509 ou EncryptedKeys. Use WsTrustFeb2005 ou posterior.|  
|TrustDriverVersionDoesNotSupportSession|A versão da confiança configurada não oferece suporte a sessões. Use WSTrustFeb2005 ou posterior.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Não é possível criar uma interface ICrypto do token especificado para verificação de assinatura.|  
|UnableToCreateSymmetricAlgorithmFromToken|Não é possível criar o algoritmo simétrico especificado do token.|  
|UnableToDeriveKeyFromKeyInfoClause|A cláusula KeyInfo especificada resolvida para o token especificado, o que não contém uma chave simétrica que pode ser usada para derivação.|  
|UnableToFindTokenAuthenticator|Não é possível encontrar um autenticador de token para o tipo de token especificado. Tokens desse tipo não podem ser aceito de acordo com as configurações de segurança atual.|  
|UnableToLoadCertificateIdentity|Não é possível carregar a identidade do certificado X.509 especificada na configuração.|  
|UnexpectedEmptyElementExpectingClaim|O elemento especificado do namespace especificado está vazio e não especifica uma declaração de identidade válida.|  
|UnknownEncodingInBinarySecurityToken|Codificação não reconhecida ocorreu ao ler o token de segurança binário.|  
|UnsecuredMessageFaultReceived|Uma falha protegida incorretamente ou não foi recebida da outra parte. Veja a FaultException interna para o código de falha e detalhes.|  
|UnsupportedPasswordType|O token de nome de usuário especificado tem um tipo de senha sem suporte.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Não é possível importar a política de segurança. Não há suporte para os requisitos de proteção para a associação de inicialização de conversa segura. Requisitos de proteção para a inicialização de conversa protegida devem exigir a solicitação e resposta sejam autenticados e criptografados.|  
|UnsupportedSecurityPolicyAssertion|Uma declaração de política de segurança sem suporte foi detectada durante a importação de política de segurança especificado.|
