---
title: "Exceções de IdentityModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f38d09ef9b1ee2e620b42082a05c6832eec7c746
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="identitymodel-exceptions"></a>Exceções de IdentityModel
Este tópico lista todas as exceções geradas pelo IdentityModel.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres atual|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|O valor deste argumento deve ser um destes dois tipos.|  
|SAMLSubjectNameIdentifierRequiresNameValue|O 'nome' especificado para um SamlNameIdentifier não pode ser nulo ou de comprimento 0.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|O IssuanceTokenProvider concluiu a negociação de segurança.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Uma nova sessão de segurança chave foi emitida pelo servidor.|  
|SAMLAttributeMissingNameAttributeOnRead|O 'Name' SamlAttribute que está sendo lido está ausente ou tem comprimento 0.|  
|UnknownICryptoType|Não há suporte à implementação ICrypto.|  
|TraceCodeSecurityTokenProviderClosed|Provedor de Token de segurança foi fechado.|  
|SAMLUnableToLoadAdvice|Falha ao carregar o \<saml:advice > elemento.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|O atributo 'AuthenticationMethod ' que está sendo lido para um SamlAuthenticationStatement está ausente ou tem comprimento 0.|  
|UnsupportedTransformAlgorithm|Não há suporte para algoritmo de transformação ou conversão em formato canônico.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Um SamlAudienceRestrictionCondition deve conter pelo menos um público-alvo (URI).|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence deve referenciar pelo menos um SamlAssertion por Id ou referência.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|O SamlAudienceRestrictionCondition que está sendo lido está faltando um valor no elemento 'Audiência'.|  
|X509ChainBuildFail|Falha de criação da cadeia de certificado x. 509 específica. O certificado usado tem uma cadeia de confiança que não pode ser verificada. Substitua o certificado ou altere certificateValidationMode.|  
|XDCannotFindValueInDictionaryString|A id de valor específico não encontrada na cadeia de caracteres de dicionário.|  
|TraceCodeImportSecurityChannelBindingEntry|Iniciando ImportChannelBinding de segurança.|  
|PrivateKeyExchangeNotSupported|A chave privada não dá suporte a KeySpec de troca.|  
|TokenProviderUnableToGetToken|O provedor de token específico não pôde fornecer um token de segurança.|  
|SAMLEntityCannotBeNullOrEmpty|A entidade SamlAssertion específica não pode ser nulo ou vazio.|  
|SAMLAssertionRequireOneStatement|Um SamlAssertion requer pelo menos uma instrução. Certifique-se de que você adicionou ao menos um SamlStatement SamlAssertion que você está criando.|  
|AESInvalidInputBlockSize|O tamanho de entrada deve ser um múltiplo de bytes específicas.|  
|AESCryptAcquireContextFailed|Falha ao adquirir o contexto do CSP.|  
|SAMLAssertionRequireOneStatementOnRead|O SamlAssertion que está sendo lido não continha nenhum SamlStatement. Um SamlAssertion deve conter pelo menos um SamlStatement.|  
|TraceCodeSecuritySessionClosedFaultReceived|A sessão de segurança do cliente recebeu uma falha de sessão fechada do servidor.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|IssuanceTokenProvider aplicou um cabeçalho de redirecionamento.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Falha ao enviar uma sessão de segurança fechada falhas ao cliente.|  
|ValueMustBeZero|O valor deste argumento deve ser 0.|  
|SAMLUnableToResolveSignatureKey|Não é possível resolver a que classe SecurityKeyIdentifier encontrada na assinatura SamlAssertion. A assinatura de SamlAssertion não pode ser validada para o emissor específico.|  
|X509IsNotInTrustedStore|O certificado x. 509 específico não está no repositório de pessoas confiáveis.|  
|SAMLElementNotRecognized|Não há suporte para o elemento específico.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|O atributo 'Recurso' para o SamlAuthorizationDecisionStatement que está sendo lido está faltando ou de comprimento 0.|  
|SamlTokenMissingSignature|A classe SamlAssertion não está assinado. Possível assinar SamlAssertions definindo a propriedade SigningCredentials.|  
|ExpectedElementMissing|O elemento esperado com namespace específico está ausente.|  
|NoKeyIdentifierClauseFound|Nenhuma cláusula do tipo específico foi encontrada no SecurityKeyIdentifier.|  
|MissingPrivateKey|A chave privada não está presente no certificado x. 509.|  
|UnexpectedEOFFromReader|EOF inesperado do leitor XML.|  
|UnsupportedKeyDerivationAlgorithm|Não há suporte para o algoritmo de derivação de chave específico.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|O token especificado não oferece suporte à criação de cláusula de identificador de chave específico.|  
|LastMessageNumberExceeded|Foi detectada uma violação do protocolo de número de sequência.|  
|SymmetricKeyLengthTooShort|O comprimento da chave simétrica especificada é muito curto.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|O SamlAuthorityBinding que está sendo lido foi encontrado para conter um 'AuthorityKind' que estava ausente ou de comprimento 0.  Isso não é permitido.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer está vazio.|  
|InvalidXmlQualifiedName|Um nome qualificado Xml era esperado, mas um nome inválido foi encontrado.|  
|SAMLAuthorityKindMissingName|O XmlQualifiedName que representa o 'AuthorityKind' no SamlAuthorityBinding não pode ser nulo ou de comprimento 0.|  
|AESCryptEncryptFailed|Falha ao criptografar os dados específicos.|  
|AuthorizationContextCreated|Contexto de autorização com a id específica é criado.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|O SamlSerializer não contém um SecurityTokenSerializer capaz de ler SecurityKeyIdentifier. Se você estiver usando um SecurityKeyIdentifier personalizado, você deve fornecer um SecurityTokenSerializer personalizado.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|IssuanceTokenProvider reduzido o cache de token de serviço.|  
|TraceCodeSecurityTokenProviderOpened|Provedor de Token de segurança foi aberto.|  
|PublicKeyNotRSA|A chave pública não é uma chave RSA.|  
|InvalidReaderState|O estado específico é inválido para o leitor de entrada fornecido.|  
|UnableToResolveReferenceUriForSignature|Não é possível resolver o URI específico na assinatura para calcular o resumo.|  
|EmptyBase64Attribute|Um valor vazio foi encontrado para o nome do atributo de base64 necessária e o namespace.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|SubjectConfirmation o SAML requer um método de confirmação quando os dados de confirmação ou KeyInfo é especificado.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|O SamlAudienceRestrictionCondition que está sendo lido deve conter o valor de pelo menos um 'público'. Nenhum foi encontrado.|  
|TokenProviderUnableToRenewToken|O provedor de token específico foi possível renovar o token de segurança.|  
|AESIVLengthNotSupported|Não há suporte para o IV bits específicos. Há suporte para apenas IV de 128 bits.|  
|SAMLAuthorityBindingMissingAuthorityKind|Um SamlAuthorityBinding deve conter um 'AuthorityKind' que não seja null.|  
|TraceCodeSecuritySessionDemuxFailure|A mensagem de entrada não é parte de uma sessão de segurança existente.|  
|TokenRenewalNotSupported|O provedor de token não oferece suporte à renovação de token.|  
|AtLeastOneReferenceRequired|É necessário pelo menos uma referência em uma assinatura.|  
|SAMLSignatureAlreadyRead|A assinatura já foi lido na asserção SAML.|  
|AlgorithmAndPrivateKeyMisMatch|O algoritmo especificado e a chave privada não coincidem.|  
|EmptyTransformChainNotSupported|Não há suporte para a cadeia de transformação vazia.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper &#124;' offset' está fora do intervalo.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper &#124;' Tamanho ' está fora do intervalo. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = a segurança Gerenciador de token não é possível criar um autenticador de token para o requisito específico.|  
|UnableToCreateKeyedHashAlgorithm|Não é possível criar KeyedHashAlgorithm do valor específico para o algoritmo de assinatura específica.|  
|SAMLUnableToLoadAssertion|O \<saml:assertion > elemento falhou ao carregar.|  
|X509FindValueMismatchMulti|O X509FindType específicos requer que o tipo de findValue o argumento para ser um dos valores de 2. O argumento findValue é de outro tipo.|  
|TraceCodeSecurityIdentityDeterminationSuccess|A identidade foi determinada para um EndpointAddress.|  
|UndefinedUseOfPrefixAtElement|O prefixo específico que é usado no elemento não possui namespace definido.|  
|TraceCodeSecuritySessionResponderOperationFailure|Falha na operação de sessão de segurança no servidor.|  
|CannotFindCert|Não é possível localizar o certificado x. 509 usando os critérios de pesquisa específico: StoreName, StoreLocation, FindType, FindValue.|  
|X509InvalidUsageTime|O tempo de uso de certificado x. 509 específico é inválido. O tempo de uso não se encaixam entre a hora necessária de NotBefore e NotAfter.|  
|TraceCodeSecurityIdentityDeterminationFailure|A identidade não pode ser determinada para um EndpointAddress.|  
|AsyncObjectAlreadyEnded|O método End já foi chamado neste objeto de resultado assíncrono.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|O dicionário externo não contém definições para cadeias de caracteres necessárias. A cadeia de caracteres não está disponível no dicionário remoto.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|A sessão de segurança do cliente recebeu uma falha de renovação de chave do servidor.|  
|SAMLActionNameRequired|A cadeia de caracteres que representa o SamlAction não pode ser nulo ou de comprimento 0.|  
|SignatureVerificationFailed|Falha na verificação de assinatura.|  
|TraceCodeSecurityContextTokenCacheFull|O cache SecurityContextSecurityToken está cheio.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|MajorVersion para SamlAssertion que está sendo lido está ausente ou tem comprimento 0.|  
|SamlAttributeClaimRightShouldBePossessProperty|Este construtor SamlAttribute requer que a direita da declaração tenha o valor System.IdentityModel.Claims.Rights.PossessProperty.|  
|AuthorizationPolicyEvaluated|Diretiva com a id específica é avaliada.|  
|SAMLUnableToLoadCondtions|O \<saml:conditions > elemento falhou ao carregar.|  
|AESKeyLengthNotSupported|Não há suporte para a chave de bits específico. Somente 128, 192 e 256 chave de bits é suportado.|  
|UserNameCannotBeEmpty|O nome de usuário não pode ficar vazio.|  
|AlgorithmAndPublicKeyMisMatch|O algoritmo especificado e a chave pública não coincidem.|  
|SAMLUnableToLoadCondtion|O \<saml:conditions > elemento falhou ao carregar.|  
|SamlAssertionMissingSigningCredentials|SigningCredentials não foram definidas no SamlAssertion. SamlAssertions deve ser assinado, defina um SigningCredentials válido no SamlAssertion para continuar.|  
|SspiPayloadNotEncrypted|Os dados binários não foi criptografados com o contexto de segurança do SSPI.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|O SamlAuthorizationDecisionStatement que está sendo lido não contém nenhum SamlAction.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|O protocolo de segurança não pode proteger a mensagem de saída.|  
|UndefinedUseOfPrefixAtAttribute|O prefixo específico usado no atributo específico não possui namespace definido.|  
|NoInputIsSetForCanonicalization|Nenhuma entrada está definida para gravar a saída de conversão em formato canônico.|  
|TraceCodeSecurityPendingServerSessionAdded|Uma sessão de segurança pendente é adicionada ao servidor.|  
|AsyncCallbackException|Um AsyncCallback gerou uma exceção.|  
|PrivateKeyNotRSA|A chave privada não é uma chave RSA.|  
|TraceCodeSecurityClientSessionKeyRenewed|A sessão de segurança do cliente renovou a chave de sessão.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|A decisão para o SamlAuthorizationDecisionStatement que está sendo lido está faltando ou de comprimento 0.|  
|SAMLAttributeNameAttributeRequired|O 'nome' especificado para um SamlAttribute não pode ser nulo ou de comprimento 0.|  
|SamlSerializerRequiresExternalSerializers|O SamlSerializer requer um SecurityTokenSerializer serializar o SecurityKeyIdentifier presente no token.|  
|UnableToResolveKeyReference|O resolvedor de token é não é possível resolver a referência de chave de segurança específico.|  
|UnsupportedKeyWrapAlgorithm|Não há suporte para o algoritmo de codificação de chave específico.|  
|SAMLAssertionMissingIssuerAttributeOnRead|O 'emissor' para SamlAssertion que está sendo lido está ausente ou tem comprimento 0.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|O IssuanceTokenProvider usou o token de serviço em cache.|  
|AESCryptGetKeyParamFailed|Falha ao obter o parâmetro de chave específico.|  
|InvalidNamespaceForEmptyPrefix|O namespace é inválido para o prefixo vazio.|  
|AESCipherModeNotSupported|Não há suporte para o modo de codificação específico. CBC só tem suporte.|  
|ArgumentCannotBeEmptyString|O argumento deve ser uma cadeia de caracteres não vazia.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|MinorVersion para SamlAssertion que está sendo lido está ausente ou tem comprimento 0.|  
|SpecifiedStringNotAvailableInDictionary|A cadeia de caracteres especificada não é uma entrada no dicionário atual.|  
|KerberosApReqInvalidOrOutOfMemory|O AP-REQ é inválido ou o sistema não tem memória suficiente.|  
|FailLogonUser|Falha de LogonUser para o usuário especificado. Certifique-se de que o usuário tem uma conta válida do Windows.|  
|ValueMustBeNonNegative|O valor deste argumento deve ser não negativo.|  
|X509ValidationFail|Falha na validação de certificado x. 509 especificada.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|A operação de sessão de segurança foi concluída com êxito no cliente.|  
|SAMLActionNameRequiredOnRead|A cadeia de caracteres que é lida para o SamlAction está ausente ou tem comprimento 0.|  
|KerberosMultilegsNotSupported|Identidade é especificada como o UPN. Autenticar um serviço executado sob uma conta de usuário requer multi-trechos de Kerberos, a qual não há suporte.|  
|SAMLAssertionIdRequired|O 'assertionId' para um SamlAssertion não pode ser nulo ou vazio.|  
|InvalidOperationForWriterState|A operação especificada é inválida no estado XmlWriter especificado.|  
|CannotValidateSecurityTokenType|O autenticador de token de segurança especificado não é possível validar um token do tipo especificado.|  
|X509FindValueMismatch|O X509FindType especificado requer que o tipo de findValue o argumento para ser o valor especificado. O argumento findValue é de outro tipo.|  
|TraceCodeSecurityClientSessionCloseSent|Uma mensagem de fechamento foi enviada pela sessão de segurança do cliente.|  
|SuiteDoesNotAcceptAlgorithm|O algoritmo especificado não é aceito para a operação especificada, o conjunto de algoritmos especificado|  
|TraceCodeSecuritySessionRequestorOperationFailure|Falha na operação de sessão de segurança do cliente.|  
|SAMLUnableToLoadStatement|Falha ao carregar SamlStatement.|  
|InnerReaderMustBeAtElement|O leitor interno deve ser o elemento.|  
|UnableToCreateTokenReference|Não é possível criar uma referência de token de segurança.|  
|TraceCodeSecurityBindingIncomingMessageVerified|O protocolo de segurança verificou a mensagem de entrada.|  
|ObjectIsReadOnly|O objeto é somente leitura.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|A sessão de segurança do cliente descartou a chave de sessão anterior.|  
|SAMLTokenTimeInvalid|O SamlToken não é de tempo válido. O horário atual está fora do tempo de efetivação e expiração do token.|  
|TraceCodeSecurityIdentityVerificationSuccess|Êxito na verificação de identidade.|  
|SigningTokenHasNoKeys|O token de autenticação especificado não possui nenhuma chave.|  
|TraceCodeSecurityIdentityVerificationFailure|Falha na verificação de identidade.|  
|AESCryptImportKeyFailed|Falha ao importar o material da chave.|  
|FailInitializeSecurityContext|Falha no InitializeSecurityContent. Certifique-se de que o nome da entidade de serviço está correto.|  
|TraceCodeStreamSecurityUpgradeAccepted|A atualização de segurança de fluxo foi aceita com êxito.|  
|SAMLAuthorityBindingRequiresLocation|O atributo 'Local' que é especificado no SamlAuthorityBinding não pode ser nulo ou de comprimento 0.|  
|PublicKeyNotDSA|A chave pública não é uma chave DSA.|  
|ImpersonationLevelNotSupported|Os modos de autenticação usando o Kerberos não dão suporte para o nível de representação especificado. Especifica um nível de identificação ou representação válido.|  
|RequiredTargetNotSigned|O elemento com a id especificada é necessário para ser assinada, mas não era.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|O atributo 'AuthenticationInstant' está sendo lido para um SamlAuthenticationStatement está ausente ou tem comprimento 0.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|O SamlEvidence que está sendo lido não continha uma referência a ou um SamlAssertion incorporado.|  
|LengthOfArrayToConvertMustGreaterThanZero|O comprimento da matriz para converter para um inteiro deve ser maior que 0.|  
|InvalidAsyncResult|AsyncResult inválido.|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|O IssuanceTokenProvider removeu o token de serviço expirado.|  
|IncorrectUserNameFormat|O nome de usuário está em um formato inválido. O formato de nome de usuário deve estar no formato "nome de usuário ' ou ' domínio\\\username'.|  
|TraceCodeExportSecurityChannelBindingEntry|Iniciando ExportChannelBinding de segurança.|  
|UnsupportedInputTypeForTransform|Não há suporte para o tipo de entrada especificado para a transformação.|  
|CannotFindDocumentRoot|Não é possível localizar a raiz do documento.|  
|XmlBufferQuotaExceeded|O tamanho necessário para armazenar em buffer o conteúdo XML ultrapassou a cota de buffer.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|Falha ao enviar uma resposta de fechamento de sessão de segurança ao cliente.|  
|UnableToResolveReferenceInSamlSignature|Não é possível resolver a referência especificada na assinatura com AssertionID SAML.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|Um SamlSubject requer que um 'NameIdentifier' ou a 'propriedade ConfirmationMethod' ser especificado. Ambos estão ausentes.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|O Namespace' ' para o SamlAttribute que está sendo lido está faltando ou de comprimento 0.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|Uma propriedade 'ConfirmationMethod' não pode ser encontrada na classe SamlSubjectConfirmation que está sendo lido.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|O requisito de token tem um tipo inesperado para a propriedade especificada. O tipo de propriedade esperado é de outro valor.|  
|TraceCodeNegotiationTokenProviderAttached|O NegotiationTokenProvider foi anexado.|  
|TraceCodeSpnegoClientNegotiationCompleted|SpnegoTokenProvider concluiu a negociação SSPI.|  
|SAMLUnableToLoadUnknownElement|A classe SamlSerializer selecionada não é possível desserializar este elemento. Registre uma classe SamlSerializer personalizada para desserializar elementos personalizados.|  
|CreateSequenceRefused|A solicitação de criação de sequência foi recusada pelo destino RM.|  
|TraceCodeSecuritySessionRedirectApplied|A sessão de segurança do cliente foi redirecionada.|  
|SecurityTokenRequirementDoesNotContainProperty|O requisito de token não contém a propriedade especificada.|  
|SAMLAttributeValueCannotBeNull|Um dos attributeValues encontrados no SamlAttribute foi encontrado para ser um valor nulo. Certifique-se de que listas não forem nulas na criação de SamlAttribute.|  
|ValueMustBeGreaterThanZero|O valor deste argumento deve ser maior que 0.|  
|TraceCodeNegotiationAuthenticatorAttached|O NegotiationTokenAuthenticator foi anexado.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Um SamlAuthorizationDecisionStatement deve ter pelo menos um SamlAction.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Autenticador de Token de segurança foi fechado.|  
|TraceCodeSecurityAuditWrittenSuccess|O log de auditoria de segurança foi gravado com êxito.|  
|PrivateKeyNotDSA|A chave privada não é uma chave DSA.|  
|MessageNumberRollover|O número máximo de sequência para esta sequência foi excedido.|  
|AESPaddingModeNotSupported|O modo de preenchimento especificado não é suportado. Há suporte para apenas PKCS7 e ISO10126.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Obrigatório 'NameIdentifier' e os elementos de 'propriedade ConfirmationMethod' não foi encontrados para o SamlSubject sendo lido.|  
|TraceCodeSecurityAuditWrittenFailure|Ocorreu uma falha ao gravar no log de auditoria de segurança.|  
|UnsupportedCryptoAlgorithm|Não há suporte para o algoritmo de criptografia especificado neste contexto.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|O token de assinatura não tem chave que oferece suporte ao pacote de algoritmo especificado.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|A cadeia de caracteres 'Identificador' para o SamlNameIdentifier que está sendo lido está ausente.|  
|SAMLSubjectStatementRequiresSubject|Declaração do assunto SAML requer um assunto SAML seja especificado.|  
|TraceCodeSslClientCertMissing|O cliente SSL remoto falhou ao fornecer um certificado necessário.|  
|SAMLTokenVersionNotSupported|Não há suporte para a versão principal especificada e a versão secundária.|  
|TraceCodeConfigurationIsReadOnly|A configuração é somente leitura.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Falha ao enviar uma falha de renovação na chave de sessão de segurança ao cliente.|  
|TraceCodeSecurityInactiveSessionFaulted|Uma sessão de segurança inativa foi interrompida pelo servidor.|  
|SAMLUnableToLoadAttribute|Falha ao carregar SamlAttribute.|  
|Psha1KeyLengthInvalid|O comprimento da chave PSHA1 especificado é inválido.|  
|KeyIdentifierCannotCreateKey|Este identificador SecurityKeyIdentifier não tem nenhuma cláusula que pode criar uma chave.|  
|X509IsInUntrustedStore|O certificado x. 509 especificado está em um repositório de certificados não confiáveis.|  
|UnexpectedXmlChildNode|O nó filho XML especificado do tipo especificado é inesperado para o elemento especificado.|  
|TokenDoesNotMeetKeySizeRequirements|Os requisitos de tamanho de chave para o conjunto de algoritmos especificado não são atendidos pelo token especificado.|  
|TraceCodeSecuritySessionRequestorStartOperation|Uma operação de sessão de segurança foi iniciada no cliente.|  
|InvalidHexString|Formato de cadeia de caracteres hexadecimal inválido.|  
|SamlAttributeClaimResourceShouldBeAString|Este construtor SamlAttribute requer que o recurso da declaração do tipo 'string'.|  
|SamlSigningTokenNotFound|SamlAssertion está assinado, mas não é possível encontrar o token que assinou. Certifique-se de que a classe SecurityTokenResolver contém o token que assinou.|  
|TraceCodeSecuritySpnToSidMappingFailure|O ServicePrincipalName não pôde ser mapeado para um SecurityIdentifier.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Não é possível criar um formatador de assinatura para o algoritmo especificado a partir da criptografia assimétrica especificada.|  
|TraceCodeSecurityServerSessionClosedFaultSent|A sessão de segurança do servidor enviou uma falha de sessão fechada ao cliente.|  
|UnableToFindPrefix|Não é possível encontrar o prefixo para o prefixo usado visivelmente especificado no elemento especificado.|  
|TraceCodeSecurityTokenAuthenticatorOpened|Autenticador de Token de segurança foi aberto.|  
|RequiredAttributeMissing|O atributo especificado é necessário no elemento especificado.|  
|LocalIdCannotBeEmpty|O localId não pode ficar vazio. Especifique um 'localId' válido.|  
|ValueMustBeInRange|O valor deste argumento deve estar dentro do intervalo especificado.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|IssuanceTokenProvider iniciou uma nova negociação de segurança.|  
|InvalidNtMapping|O certificado x. 509 especificado não pode ser mapeado para uma conta do Windows. Nome alternativo da entidade UPN é necessário.|  
|AESCryptSetKeyParamFailed|Falha ao definir o parâmetro de chave especificado.|  
|TraceCodeSecuritySessionClosedResponseReceived|A sessão de segurança do cliente recebeu uma resposta fechada do servidor.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Não é possível criar um desformatador de assinatura para o algoritmo especificado a partir da criptografia assimétrica especificada.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Um retorno de chamada assíncrono lançou uma exceção.|  
|LengthMustBeGreaterThanZero|O comprimento deste argumento deve ser maior que 0.|  
|FoundMultipleCerts|Encontrados vários certificados x. 509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType, FindValue. Forneça um valor de localização mais específico.|  
|AtLeastOneTransformRequired|O elemento de transformações deve conter pelo menos uma transformação.|  
|SAMLTokenNotSerialized|A classe SamlAssertion não pôde ser serializado para XML. Consulte a exceção interna para obter detalhes.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|O protocolo de segurança protegeu a mensagem de saída.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Esta SecurityKeyIdentifierClause não oferece suporte a criação da chave.|  
|UnableToResolveTokenReference|O resolvedor de token é não é possível resolver a referência de token especificada.|  
|UnsupportedEncryptionAlgorithm|Não há suporte para o algoritmo de criptografia especificado.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|O SamlSerializer não contém um SecurityTokenSerializer capaz de serializar SecurityKeyIdentifier determinado. Se você estiver usando um SecurityKeyIdentifier personalizado, você deve fornecer um SecurityTokenSerializer personalizado.|  
|SAMLAttributeShouldHaveOneValue|Nenhum valor de atributo foi encontrado. Um atributo SamlAttribute deve ter pelo menos um valor de atributo.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Protocolo de segurança não é possível verificar a mensagem de entrada.|  
|SamlSigningTokenMissing|A classe SamlAssertion transmitida à classe SamlSecurityTokenAuthenticator não contém um token de assinatura.|  
|NoPrivateKeyAvailable|Nenhuma chave privada está disponível.|  
|ValueMustBeOne|O valor deste argumento deve ser 1.|  
|TraceCodeSecurityPendingServerSessionRemoved|Uma sessão de segurança pendente foi feita ativa pelo servidor.|  
|TraceCodeImportSecurityChannelBindingExit|ImportChannelBinding de segurança concluída.|  
|X509CertStoreLocationNotValid|StoreLocation deve ser LocalMachine ou CurrentUser.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|As configurações do gravador podem ser modificadas apenas quando o gravador está no estado inicial.|  
|ArgumentInvalidCertificate|O certificado é inválido.|  
|DigestVerificationFailedForReference|Falha na verificação de resumo para a referência especificada.|  
|SAMLAuthorityBindingRequiresBinding|O atributo 'Ligação' especificado no SamlAuthorityBinding não pode ser nulo ou de comprimento 0.|  
|AESInsufficientOutputBuffer|O buffer de saída deve ser maior que os bytes especificados.|  
|SAMLAuthorityBindingMissingBindingOnRead|A atributo 'Ligação' para o SamlAuthorityBinding que está sendo lido está faltando ou de comprimento 0.|  
|SAMLAuthorityBindingInvalidAuthorityKind|O SamlAuthorityBinding que está sendo lido tem um AuthorityKind inválido. O formato do AuthorityKind deve ser um QName.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|O NetworkCredentials fornecido para o Kerberos Token não tem um nome de usuário válido.|  
|SSPIPackageNotSupported|Não há suporte para o pacote SSPI especificado.|  
|TokenCancellationNotSupported|O provedor de token especificado não oferece suporte ao cancelamento de token.|  
|UnboundPrefixInQName|Um prefixo não acoplado é usado no nome qualificado especificado.|  
|SAMLAuthorizationDecisionResourceRequired|O 'recurso' especificado para o SamlAuthorizationDecisionStatement não pode ser nulo ou de comprimento 0.|  
|TraceCodeSecurityNegotiationProcessingFailure|Falha de processamento da negociação de segurança do serviço.|  
|SAMLAssertionIssuerRequired|O 'emissor' especificado para um SamlAssertion não pode ser nulo ou vazio.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Não é possível criar HashAlgorithm para o algoritmo especificado a partir da criptografia assimétrica especificada.|  
|SamlUnableToExtractSubjectKey|SecurityKeyIdentifier encontrado no SamlSubject não pode ser resolvido para um SecurityToken. A classe SecurityTokenResolver deve conter um SecurityToken que resolve SecurityKeyIdentifier.|  
|ChildNodeTypeMissing|O elemento XML especificado não tem um filho do tipo especificado.|  
|TraceCodeSecurityPendingServerSessionClosed|A sessão de segurança pendente foi fechada pelo servidor.|  
|TraceCodeSecuritySessionCloseResponseSent|A sessão de segurança do servidor enviou uma resposta de fechamento ao cliente.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|A porção HostName de um endereço de ponto de extremidade não pode ser normalizada.|  
|FailAcceptSecurityContext|Falha no AcceptSecurityContext.|  
|EmptyXmlElementError|O elemento especificado não pode ser vazio.|  
|PrefixNotDefinedForNamespace|Um prefixo para o namespace especificado não está definido neste contexto e não pode ser declarado.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|O SamlAuthorizationDecisionStatement que está sendo lido foi encontrado mais de uma evidência. Isso não é permitido.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|A classe SamlSecurityTokenAuthenticator apenas pode processar SamlSecurityTokens. O valor de SecurityTokenType especificado foi recebida.|  
|SAMLAttributeStatementMissingAttributeOnRead|O SamlAttributeStatement que está sendo lido não contém nenhum elemento 'SamlAttribute'. Isso não é permitido.|  
|CouldNotFindNamespaceForPrefix|Não é possível pesquisar o namespace para o prefixo especificado.|  
|TraceCodeExportSecurityChannelBindingExit|ExportChannelBinding de segurança concluída.|  
|AESCryptDecryptFailed|Falha ao descriptografar os dados especificados.|  
|SAMLAttributeNamespaceAttributeRequired|O 'Namespace' especificado para um SamlAttribute não pode ser nulo ou de comprimento 0.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator concluiu a negociação SSPI.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|A sessão de segurança do servidor enviou uma falha de renovação de chave para o cliente.|  
|AlgorithmMismatchForTransform|Ocorreu uma incompatibilidade no algoritmo para a transformação.|  
|UserNameAuthenticationFailed|Falha na autenticação de uma nome de usuário/senha usando o mecanismo especificado. Usuário não está autenticado.|  
|SamlInvalidSigningToken|O SamlAssertion foi assinado com um token de acordo com o protocolo, não foi validado. Se você estiver usando certificados x. 509, examine suas semânticas de validação.|  
|TraceCodeSecurityServerSessionKeyUpdated|A chave de sessão de segurança foi atualizada pelo servidor.|  
|TraceCodeSecurityServerSessionCloseReceived|A sessão de segurança do servidor recebeu uma mensagem de fechamento do cliente.|  
|SAMLAuthenticationStatementMissingSubject|O SamlAuthenticationStatement está faltando a classe de SamlSubjectStatement necessária.|  
|UnexpectedEndOfFile|Fim de arquivo inesperado.|  
|UnsupportedAlgorithmForCryptoOperation|Não há suporte para o algoritmo especificado para a operação especificada.|  
|XmlLangAttributeMissing|O atributo XML: lang obrigatório está ausente.|  
|TraceCodeSecurityImpersonationSuccess|Êxito de representação de segurança no servidor.|  
|SAMLAuthorityBindingMissingLocationOnRead|O atributo 'Local' para o SamlAuthorityBinding que está sendo lido está faltando ou de comprimento 0.|  
|SAMLAttributeStatementMissingSubjectOnRead|O elemento 'SamlSubject' para SamlAttributeStatement está ausente.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|O elemento 'SamlSubject' para SamlAuthorizationDecisionStatement que está sendo lido está ausente.|  
|SAMLBadSchema|Durante a leitura de um SamlAssertion esse elemento especificado foi encontrado não estar em conformidade com o esquema.|  
|SAMLAssertionIDIsInvalid|O 'assertionId' especificado para um SamlAssertion deve iniciar com uma letra ou '_'.|  
|TraceCodeSecurityActiveServerSessionRemoved|Uma sessão de segurança ativa foi removida pelo servidor.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Não é possível criar keyedHashAlgorithm para o algoritmo especificado a partir da criptografia simétrica especificada.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|O 'AuthenticationMethod' especificado para um SamlAuthenticationStatement não pode ser nulo ou de comprimento 0.|  
|TraceCodeSecurityImpersonationFailure|Falha na representação de segurança no servidor.|  
|Padrão|(Padrão)|  
|UnsupportedNodeTypeInReader|Não há suporte para o tipo de nó especificado com o nome especificado.|
