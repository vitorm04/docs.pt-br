---
title: Exceções de IdentityModel
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: ee0b5537a415e1ea53c653ae8e8485e94cc713fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998511"
---
# <a name="identitymodel-exceptions"></a>Exceções de IdentityModel
Este tópico lista todas as exceções geradas pelas IdentityModel.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres atual|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|O valor deste argumento deve ser um destes dois tipos.|  
|SAMLSubjectNameIdentifierRequiresNameValue|O 'nome' especificado para um SamlNameIdentifier não pode ser nulo ou tem comprimento 0.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|O IssuanceTokenProvider concluiu a negociação de segurança.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Uma nova sessão de segurança chave foi emitida pelo servidor.|  
|SAMLAttributeMissingNameAttributeOnRead|O 'nome' para o SamlAttribute sendo lida está ausente ou tem comprimento 0.|  
|UnknownICryptoType|Não há suporte para a implementação ICrypto.|  
|TraceCodeSecurityTokenProviderClosed|Provedor de Token de segurança foi fechado.|  
|SAMLUnableToLoadAdvice|Falha ao carregar o \<SAML: advice > elemento.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|O atributo 'AuthenticationMethod' que está sendo lido para um SamlAuthenticationStatement está ausente ou tem comprimento 0.|  
|UnsupportedTransformAlgorithm|Não há suporte para algoritmo de canonicalização ou transformação.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Um SamlAudienceRestrictionCondition deve conter pelo menos um público-alvo (URI).|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence deve referenciar pelo menos uma SamlAssertion por Id ou referência.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Um valor no elemento 'Público' está ausente no SamlAudienceRestrictionCondition que está sendo lido.|  
|X509ChainBuildFail|A cadeia de certificados x. 509 específica criando com falha. O certificado que foi usado tem uma cadeia de confiança que não pode ser verificada. Substitua o certificado ou altere o certificateValidationMode.|  
|XDCannotFindValueInDictionaryString|A id de valor específico não encontrada na cadeia de caracteres de dicionário.|  
|TraceCodeImportSecurityChannelBindingEntry|Iniciando ImportChannelBinding de segurança.|  
|PrivateKeyExchangeNotSupported|A chave privada não oferece suporte o KeySpec exchange.|  
|TokenProviderUnableToGetToken|O provedor de token específico não pôde fornecer um token de segurança.|  
|SAMLEntityCannotBeNullOrEmpty|A entidade SamlAssertion específica não pode ser nulo ou vazio.|  
|SAMLAssertionRequireOneStatement|Uma SamlAssertion exige pelo menos uma instrução. Certifique-se de que você tenha adicionado pelo menos uma SamlStatement à SamlAssertion que você está criando.|  
|AESInvalidInputBlockSize|O tamanho de entrada deve ser um múltiplo de bytes específicas.|  
|AESCryptAcquireContextFailed|Falha ao adquirir o contexto CSP.|  
|SAMLAssertionRequireOneStatementOnRead|A SamlAssertion lida não continha nenhuma SamlStatement. Uma SamlAssertion deve conter pelo menos uma SamlStatement.|  
|TraceCodeSecuritySessionClosedFaultReceived|A sessão de segurança do cliente recebeu uma falha de sessão fechada do servidor.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|IssuanceTokenProvider aplicou um cabeçalho de redirecionamento.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Falha ao enviar uma sessão de segurança fechada falha para o cliente.|  
|ValueMustBeZero|O valor deste argumento deve ser 0.|  
|SAMLUnableToResolveSignatureKey|Não é possível resolver o que SecurityKeyIdentifier encontrado na assinatura da SamlAssertion. A assinatura da SamlAssertion não pode ser validada para o emissor específico.|  
|X509IsNotInTrustedStore|O certificado X.509 específico não está no repositório de pessoas confiáveis.|  
|SAMLElementNotRecognized|Não há suporte para o elemento específico.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|O atributo 'Recurso' para o SamlAuthorizationDecisionStatement que está sendo lido está ausente ou tem comprimento 0.|  
|SamlTokenMissingSignature|A SamlAssertion não está assinada. SamlAssertions podem ser assinadas definindo as SigningCredentials.|  
|ExpectedElementMissing|O elemento esperado com o namespace específico está ausente.|  
|NoKeyIdentifierClauseFound|Nenhuma cláusula do tipo específico foi encontrada no SecurityKeyIdentifier.|  
|MissingPrivateKey|A chave privada não está presente no certificado x. 509.|  
|UnexpectedEOFFromReader|EOF inesperado do leitor de XML.|  
|UnsupportedKeyDerivationAlgorithm|Não há suporte para o algoritmo de derivação de chave específico.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|O token especificado não suporta a criação de cláusula de identificador de chave específico.|  
|LastMessageNumberExceeded|Foi detectada uma violação do protocolo de número de sequência.|  
|SymmetricKeyLengthTooShort|O comprimento da chave simétrica especificada é muito curto.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|O SamlAuthorityBinding que está sendo lido foi encontrado para conter um 'AuthorityKind' que estava ausente ou tem comprimento 0.  Isso não é permitido.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer está vazio.|  
|InvalidXmlQualifiedName|Um nome qualificado Xml era esperado, mas um nome inválido foi encontrado.|  
|SAMLAuthorityKindMissingName|O XmlQualifiedName que representa o 'AuthorityKind' SamlAuthorityBinding não pode ser nulo ou tem comprimento 0.|  
|AESCryptEncryptFailed|Falha ao criptografar os dados específicos.|  
|AuthorizationContextCreated|Contexto de autorização com a id específica é criado.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|O SamlSerializer não contém um SecurityTokenSerializer que pode ler o SecurityKeyIdentifier. Se você estiver usando um SecurityKeyIdentifier personalizado, você deve fornecer um SecurityTokenSerializer personalizado.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|IssuanceTokenProvider reduzido o cache de token de serviço.|  
|TraceCodeSecurityTokenProviderOpened|Provedor de Token de segurança foi aberto.|  
|PublicKeyNotRSA|A chave pública não é uma chave RSA.|  
|InvalidReaderState|O estado específico é inválido para o leitor de entrada fornecido.|  
|UnableToResolveReferenceUriForSignature|Não é possível resolver o URI específico na assinatura para calcular o resumo.|  
|EmptyBase64Attribute|Um valor vazio foi encontrado para o nome do atributo de base64 necessária e o namespace.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|O SubjectConfirmation SAML requer um método de confirmação quando os dados de confirmação ou KeyInfo é especificado.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|O SamlAudienceRestrictionCondition que está sendo lido deve conter o valor de pelo menos um 'público'. Nenhum foi encontrado.|  
|TokenProviderUnableToRenewToken|O provedor de token específico não pôde renovar o token de segurança.|  
|AESIVLengthNotSupported|Não há suporte para o IV bits específicos. Há suporte para apenas 128 bits IV.|  
|SAMLAuthorityBindingMissingAuthorityKind|Um SamlAuthorityBinding deve conter um 'AuthorityKind' que não seja null.|  
|TraceCodeSecuritySessionDemuxFailure|A mensagem de entrada não é parte de uma sessão de segurança existente.|  
|TokenRenewalNotSupported|O provedor de token específico não suporta renovação de tokens.|  
|AtLeastOneReferenceRequired|Pelo menos uma referência é necessária uma assinatura.|  
|SAMLSignatureAlreadyRead|A assinatura já foi lida na asserção SAML.|  
|AlgorithmAndPrivateKeyMisMatch|O algoritmo especificado e a chave privada não coincidem.|  
|EmptyTransformChainNotSupported|Não há suporte para a cadeia de transformação vazio.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper&#124;'offset' está fora do intervalo.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper&#124;'size' está fora do intervalo. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = a segurança do Gerenciador de token não é possível criar um autenticador de token para o requisito específico.|  
|UnableToCreateKeyedHashAlgorithm|Não é possível criar KeyedHashAlgorithm do valor específico para o algoritmo de assinatura específica.|  
|SAMLUnableToLoadAssertion|O \<SAML: Assertion > Falha ao carregar o elemento.|  
|X509FindValueMismatchMulti|O X509FindType específicos requer que o tipo de findValue o argumento para ser um dos valores de 2. O argumento findValue é de outro tipo.|  
|TraceCodeSecurityIdentityDeterminationSuccess|A identidade foi determinada para um EndpointAddress.|  
|UndefinedUseOfPrefixAtElement|O prefixo específico que é usado para o elemento não tem namespace definido.|  
|TraceCodeSecuritySessionResponderOperationFailure|Falha na operação de sessão de segurança no servidor.|  
|CannotFindCert|Não é possível localizar o certificado X.509 usando os critérios de pesquisa específicos: StoreName, StoreLocation, FindType ', FindValue.|  
|X509InvalidUsageTime|A hora de uso de certificado x. 509 específica é inválida. O tempo de uso não está entre a hora necessária de NotBefore e NotAfter.|  
|TraceCodeSecurityIdentityDeterminationFailure|A identidade não pode ser determinada para um EndpointAddress.|  
|AsyncObjectAlreadyEnded|O método End já foi chamado neste objeto de resultado assíncrono.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|O dicionário externo não contém definições para cadeias de caracteres necessárias. A cadeia de caracteres não está disponível no dicionário remoto.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|A sessão de segurança do cliente recebeu uma falha de renovação de chave do servidor.|  
|SAMLActionNameRequired|A cadeia de caracteres que representa o SamlAction não pode ser nulo ou tem comprimento 0.|  
|SignatureVerificationFailed|Falha na verificação de assinatura.|  
|TraceCodeSecurityContextTokenCacheFull|O cache SecurityContextSecurityToken está cheio.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|A MajorVersion da SamlAssertion lida está ausente ou tem comprimento 0.|  
|SamlAttributeClaimRightShouldBePossessProperty|Este construtor SamlAttribute requer que o direito da declaração têm o valor System.IdentityModel.Claims.Rights.PossessProperty.|  
|AuthorizationPolicyEvaluated|A política com a id específica é avaliada.|  
|SAMLUnableToLoadCondtions|O \<SAML: Conditions > Falha ao carregar o elemento.|  
|AESKeyLengthNotSupported|Não há suporte para a chave de bits específicos. Apenas 128, a chave de bits de 192 e 256 tem suporte.|  
|UserNameCannotBeEmpty|O nome de usuário não pode ficar vazio.|  
|AlgorithmAndPublicKeyMisMatch|O algoritmo especificado e a chave pública não coincidem.|  
|SAMLUnableToLoadCondtion|O \<SAML: Conditions > Falha ao carregar o elemento.|  
|SamlAssertionMissingSigningCredentials|SigningCredentials não foram definidas na SamlAssertion. As SamlAssertions devem ser assinadas defina SigningCredentials válidas na SamlAssertion para continuar.|  
|SspiPayloadNotEncrypted|Os dados binários não foi criptografados com o contexto de segurança SSPI.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|O SamlAuthorizationDecisionStatement que está sendo lido não contém nenhum SamlAction.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|O protocolo de segurança não pode proteger a mensagem de saída.|  
|UndefinedUseOfPrefixAtAttribute|O prefixo específico usado em um atributo específico não tem namespace definido.|  
|NoInputIsSetForCanonicalization|Nenhuma entrada é definida para gravar a saída canonizada.|  
|TraceCodeSecurityPendingServerSessionAdded|Uma sessão de segurança pendente é adicionada ao servidor.|  
|AsyncCallbackException|Um AsyncCallback emitiu uma exceção.|  
|PrivateKeyNotRSA|A chave privada não é uma chave RSA.|  
|TraceCodeSecurityClientSessionKeyRenewed|A sessão de segurança do cliente renovou a chave de sessão.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|A decisão para o SamlAuthorizationDecisionStatement que está sendo lido está ausente ou tem comprimento 0.|  
|SAMLAttributeNameAttributeRequired|O 'nome' especificado para um SamlAttribute não pode ser nulo ou tem comprimento 0.|  
|SamlSerializerRequiresExternalSerializers|O SamlSerializer exige um SecurityTokenSerializer para serializar o SecurityKeyIdentifier presente no token.|  
|UnableToResolveKeyReference|O resolvedor de token é não é possível resolver a referência de chave de segurança específicos.|  
|UnsupportedKeyWrapAlgorithm|Não há suporte para o algoritmo de encapsulamento de chave específico.|  
|SAMLAssertionMissingIssuerAttributeOnRead|O 'emissor' da SamlAssertion lida está ausente ou tem comprimento 0.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|IssuanceTokenProvider usou o token de serviço em cache.|  
|AESCryptGetKeyParamFailed|Falha ao obter o parâmetro de chave específico.|  
|InvalidNamespaceForEmptyPrefix|O namespace é inválido para o prefixo vazio.|  
|AESCipherModeNotSupported|Não há suporte para o modo de codificação específico. Há suporte para apenas CBC.|  
|ArgumentCannotBeEmptyString|O argumento deve ser uma cadeia de caracteres não vazia.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|A MinorVersion da SamlAssertion que está sendo lido está ausente ou tem comprimento 0.|  
|SpecifiedStringNotAvailableInDictionary|A cadeia de caracteres especificada não é uma entrada no dicionário atual.|  
|KerberosApReqInvalidOrOutOfMemory|O AP-REQ é inválido ou o sistema não tem memória suficiente.|  
|FailLogonUser|Falha de LogonUser para o usuário especificado. Certifique-se de que o usuário tem uma conta válida do Windows.|  
|ValueMustBeNonNegative|O valor deste argumento deve ser não negativo.|  
|X509ValidationFail|Falha a validação do certificado X.509 especificada.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|A operação de sessão de segurança foi concluída com êxito no cliente.|  
|SAMLActionNameRequiredOnRead|A cadeia de caracteres que é lido para o SamlAction está ausente ou tem comprimento 0.|  
|KerberosMultilegsNotSupported|Identidade é especificada como o UPN. Autenticar um serviço executado sob uma conta de usuário requer legs várias do Kerberos, que não tem suporte.|  
|SAMLAssertionIdRequired|A 'assertionId' de uma SamlAssertion não pode ser nulo ou vazio.|  
|InvalidOperationForWriterState|A operação especificada é inválida no estado XmlWriter especificado.|  
|CannotValidateSecurityTokenType|O autenticador de token de segurança especificado não é possível validar um token do tipo especificado.|  
|X509FindValueMismatch|O X509FindType especificado requer que o tipo de findValue o argumento para ser o valor especificado. O argumento findValue é de outro tipo.|  
|TraceCodeSecurityClientSessionCloseSent|Uma mensagem de fechamento foi enviada pela sessão de segurança do cliente.|  
|SuiteDoesNotAcceptAlgorithm|O algoritmo especificado não é aceito para a operação especificada pela suíte de algoritmo especificado|  
|TraceCodeSecuritySessionRequestorOperationFailure|A operação de sessão de segurança do cliente falhou.|  
|SAMLUnableToLoadStatement|Falha ao carregar uma SamlStatement.|  
|InnerReaderMustBeAtElement|O leitor interno deve ser o elemento.|  
|UnableToCreateTokenReference|Não é possível criar uma referência de token de segurança.|  
|TraceCodeSecurityBindingIncomingMessageVerified|O protocolo de segurança verificou a mensagem de entrada.|  
|ObjectIsReadOnly|O objeto é somente leitura.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|A sessão de segurança do cliente descartou a chave de sessão anterior.|  
|SAMLTokenTimeInvalid|O SamlToken não é um tempo válido. O horário atual está fora do tempo de efetivação e expiração do token.|  
|TraceCodeSecurityIdentityVerificationSuccess|Verificação de identidade foi bem-sucedida.|  
|SigningTokenHasNoKeys|O token de assinatura especificado não possui chaves.|  
|TraceCodeSecurityIdentityVerificationFailure|Falha na verificação de identidade.|  
|AESCryptImportKeyFailed|Falha ao importar o material da chave.|  
|FailInitializeSecurityContext|No InitializeSecurityContent. Verifique se que o nome da entidade de serviço está correto.|  
|TraceCodeStreamSecurityUpgradeAccepted|A atualização de segurança de fluxo foi aceita com êxito.|  
|SAMLAuthorityBindingRequiresLocation|O atributo 'Local' que é especificado no SamlAuthorityBinding não pode ser nulo ou tem comprimento 0.|  
|PublicKeyNotDSA|A chave pública não é uma chave DSA.|  
|ImpersonationLevelNotSupported|Os modos de autenticação usando Kerberos não dão suporte para o nível de representação especificado. Especifica um nível de identificação ou a representação válido.|  
|RequiredTargetNotSigned|O elemento com a id especificada é necessário a ser assinada, mas não era.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|O atributo 'AuthenticationInstant' que está sendo lido para um SamlAuthenticationStatement está ausente ou tem comprimento 0.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|O SamlEvidence que está sendo lido não continha uma referência ao ou um SamlAssertion incorporado.|  
|LengthOfArrayToConvertMustGreaterThanZero|O comprimento da matriz a ser convertido em um inteiro deve ser maior que 0.|  
|InvalidAsyncResult|AsyncResult inválido.|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|IssuanceTokenProvider removeu o token de serviço expirado.|  
|IncorrectUserNameFormat|O nome de usuário está em um formato inválido. O formato de nome de usuário deve ser na forma de "nome de usuário ' ou ' domínio\\\username'.|  
|TraceCodeExportSecurityChannelBindingEntry|Iniciando ExportChannelBinding de segurança.|  
|UnsupportedInputTypeForTransform|Não há suporte para o tipo de entrada especificado para a transformação.|  
|CannotFindDocumentRoot|Não é possível localizar a raiz do documento.|  
|XmlBufferQuotaExceeded|O tamanho necessário para armazenar em buffer o conteúdo XML excedeu a cota de buffer.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|Ocorreu uma falha ao enviar uma resposta de fechamento de sessão de segurança para o cliente.|  
|UnableToResolveReferenceInSamlSignature|Não é possível resolver a referência especificada na assinatura com AssertionID SAML.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|Um SamlSubject requer que um 'NameIdentifier' ou a 'propriedade ConfirmationMethod' seja especificado. Os dois estavam ausentes.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|O Namespace' ' para SamlAttribute sendo lida está ausente ou tem comprimento 0.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|Uma propriedade 'ConfirmationMethod' não pode ser encontrada na classe SamlSubjectConfirmation que está sendo lido.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|O requisito de token tem um tipo inesperado para a propriedade especificada. O tipo de propriedade esperado é de outro valor.|  
|TraceCodeNegotiationTokenProviderAttached|O NegotiationTokenProvider foi anexado.|  
|TraceCodeSpnegoClientNegotiationCompleted|SpnegoTokenProvider concluiu a negociação SSPI.|  
|SAMLUnableToLoadUnknownElement|O SamlSerializer selecionado não pôde desserializar este elemento. Registre um SamlSerializer personalizado para desserializar elementos personalizados.|  
|CreateSequenceRefused|A solicitação de sequência de criação foi recusada pelo destino RM.|  
|TraceCodeSecuritySessionRedirectApplied|A sessão de segurança do cliente foi redirecionada.|  
|SecurityTokenRequirementDoesNotContainProperty|O requisito de token não contém a propriedade especificada.|  
|SAMLAttributeValueCannotBeNull|Um dos attributeValues encontrados no SamlAttribute foi encontrado para ser um valor nulo. Certifique-se de que listas não são nulas na criação de SamlAttribute.|  
|ValueMustBeGreaterThanZero|O valor deste argumento deve ser maior que 0.|  
|TraceCodeNegotiationAuthenticatorAttached|O NegotiationTokenAuthenticator foi anexado.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Um SamlAuthorizationDecisionStatement deve ter pelo menos um SamlAction.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Autenticador de Token de segurança foi fechado.|  
|TraceCodeSecurityAuditWrittenSuccess|O log de auditoria de segurança é gravado com êxito.|  
|PrivateKeyNotDSA|A chave privada não é uma chave DSA.|  
|MessageNumberRollover|O número máximo de sequência para esta sequência foi excedido.|  
|AESPaddingModeNotSupported|Não há suporte para o modo de preenchimento especificado. Há suporte para apenas PKCS7 e ISO10126.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|O 'NameIdentifier' necessário e os elementos de 'propriedade ConfirmationMethod' não foram encontrados para o SamlSubject que está sendo lido.|  
|TraceCodeSecurityAuditWrittenFailure|Ocorreu uma falha ao gravar no log de auditoria de segurança.|  
|UnsupportedCryptoAlgorithm|Não há suporte para o algoritmo de criptografia especificado neste contexto.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|O token de assinatura tem nenhuma chave que oferece suporte ao pacote de algoritmo especificado.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|A cadeia de caracteres 'Identifier' para o SamlNameIdentifier que está sendo lido está ausente.|  
|SAMLSubjectStatementRequiresSubject|Declaração do assunto SAML requer um assunto SAML a ser especificado.|  
|TraceCodeSslClientCertMissing|O cliente SSL remoto falhou ao fornecer um certificado necessário.|  
|SAMLTokenVersionNotSupported|Não há suporte para a versão principal especificada e a versão secundária.|  
|TraceCodeConfigurationIsReadOnly|A configuração é somente leitura.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Ocorreu uma falha ao enviar uma falha de renovação na chave de sessão de segurança para o cliente.|  
|TraceCodeSecurityInactiveSessionFaulted|Uma sessão de segurança inativa foi interrompida pelo servidor.|  
|SAMLUnableToLoadAttribute|Falha ao carregar SamlAttribute.|  
|Psha1KeyLengthInvalid|O comprimento da chave PSHA1 especificado é inválido.|  
|KeyIdentifierCannotCreateKey|Este SecurityKeyIdentifier não tem nenhuma cláusula que pode criar uma chave.|  
|X509IsInUntrustedStore|O certificado X.509 especificado está em um repositório de certificados não confiáveis.|  
|UnexpectedXmlChildNode|O nó filho XML especificado do tipo especificado é inesperado para o elemento especificado.|  
|TokenDoesNotMeetKeySizeRequirements|Os requisitos de tamanho de chave para o pacote de algoritmos especificado não forem atendidos pelo token especificado.|  
|TraceCodeSecuritySessionRequestorStartOperation|Uma operação de sessão de segurança foi iniciada no cliente.|  
|InvalidHexString|Formato de cadeia de caracteres hexadecimal inválida.|  
|SamlAttributeClaimResourceShouldBeAString|Este construtor SamlAttribute requer que o recurso da declaração é do tipo 'string'.|  
|SamlSigningTokenNotFound|A SamlAssertion está assinada, mas o token que assinou a SamlAssertion não pode ser encontrado. Verifique se o SecurityTokenResolver contém o token que assinou a SamlAssertion.|  
|TraceCodeSecuritySpnToSidMappingFailure|ServicePrincipalName não pôde ser mapeado para um SecurityIdentifier.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Não é possível criar um formatador de assinatura para o algoritmo especificado a partir da criptografia assimétrica especificada.|  
|TraceCodeSecurityServerSessionClosedFaultSent|A sessão de segurança do servidor enviou uma falha de sessão fechada ao cliente.|  
|UnableToFindPrefix|Não é possível localizar o prefixo para o prefixo usado visivelmente especificado no elemento especificado.|  
|TraceCodeSecurityTokenAuthenticatorOpened|Autenticador de Token de segurança foi aberto.|  
|RequiredAttributeMissing|O atributo especificado é necessária no elemento especificado.|  
|LocalIdCannotBeEmpty|A localId não pode ficar vazia. Especifique uma 'localId' válida.|  
|ValueMustBeInRange|O valor deste argumento deve estar dentro do intervalo especificado.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|IssuanceTokenProvider iniciado uma nova negociação de segurança.|  
|InvalidNtMapping|O certificado X.509 especificado não pode ser mapeado para uma conta do Windows. Nome alternativo da entidade UPN é necessário.|  
|AESCryptSetKeyParamFailed|Falha ao definir o parâmetro de chave especificado.|  
|TraceCodeSecuritySessionClosedResponseReceived|A sessão de segurança do cliente recebeu uma resposta fechada do servidor.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Não é possível criar um desformatador de assinatura para o algoritmo especificado a partir da criptografia assimétrica especificada.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Um retorno de chamada assíncrono emitiu uma exceção.|  
|LengthMustBeGreaterThanZero|O comprimento deste argumento deve ser maior que 0.|  
|FoundMultipleCerts|Encontrados vários certificados X.509 usando os critérios de pesquisa especificados: StoreName, StoreLocation, FindType ', FindValue. Forneça um valor de localização mais específico.|  
|AtLeastOneTransformRequired|O elemento de transformações deve conter pelo menos uma transformação.|  
|SAMLTokenNotSerialized|Não foi possível serializar a SamlAssertion para XML. Consulte a exceção interna para obter detalhes.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|O protocolo de segurança protegido a mensagem de saída.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Esta SecurityKeyIdentifierClause não dá suporte a criação da chave.|  
|UnableToResolveTokenReference|O resolvedor de token é não é possível resolver a referência de token especificada.|  
|UnsupportedEncryptionAlgorithm|Não há suporte para o algoritmo de criptografia especificado.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|O SamlSerializer não contém um SecurityTokenSerializer que pode serializar o SecurityKeyIdentifier. Se você estiver usando um SecurityKeyIdentifier personalizado, você deve fornecer um SecurityTokenSerializer personalizado.|  
|SAMLAttributeShouldHaveOneValue|Nenhum valor de atributo foi encontrado. Um atributo SamlAttribute deve ter pelo menos um valor de atributo.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Protocolo de segurança não é possível verificar a mensagem de entrada.|  
|SamlSigningTokenMissing|A SamlAssertion passada para a classe SamlSecurityTokenAuthenticator não contém um token de assinatura.|  
|NoPrivateKeyAvailable|Nenhuma chave privada está disponível.|  
|ValueMustBeOne|O valor deste argumento deve ser 1.|  
|TraceCodeSecurityPendingServerSessionRemoved|Uma sessão de segurança pendente foi feita Active Directory pelo servidor.|  
|TraceCodeImportSecurityChannelBindingExit|ImportChannelBinding de segurança concluída.|  
|X509CertStoreLocationNotValid|StoreLocation deve ser LocalMachine ou CurrentUser.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|As configurações do gravador podem ser modificadas somente quando o gravador está no estado inicial.|  
|ArgumentInvalidCertificate|O certificado é inválido.|  
|DigestVerificationFailedForReference|Falha na verificação de resumo para a referência especificada.|  
|SAMLAuthorityBindingRequiresBinding|O atributo 'Binding' especificado no SamlAuthorityBinding não pode ser nulo ou tem comprimento 0.|  
|AESInsufficientOutputBuffer|O buffer de saída deve ser maior que os bytes especificados.|  
|SAMLAuthorityBindingMissingBindingOnRead|A associação de atributo para o SamlAuthorityBinding que está sendo lido está ausente ou tem comprimento 0.|  
|SAMLAuthorityBindingInvalidAuthorityKind|O SamlAuthorityBinding que está sendo lido tem um AuthorityKind inválido. O formato do AuthorityKind deve ser um QName.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|As NetworkCredentials fornecidas para o Kerberos Token não tem um nome de usuário válido.|  
|SSPIPackageNotSupported|Não há suporte para o pacote SSPI especificado.|  
|TokenCancellationNotSupported|O provedor de token especificado não oferece suporte ao cancelamento de token.|  
|UnboundPrefixInQName|Um prefixo não associado é usado no nome qualificado especificado.|  
|SAMLAuthorizationDecisionResourceRequired|O 'recurso' especificado para o SamlAuthorizationDecisionStatement não pode ser nulo ou tem comprimento 0.|  
|TraceCodeSecurityNegotiationProcessingFailure|Falha de processamento de negociação de segurança do serviço.|  
|SAMLAssertionIssuerRequired|O 'emissor' especificado para uma SamlAssertion não pode ser nulo ou vazio.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Não é possível criar HashAlgorithm para o algoritmo especificado a partir da criptografia assimétrica especificada.|  
|SamlUnableToExtractSubjectKey|O SecurityKeyIdentifier encontrado no SamlSubject não pode ser resolvido em um SecurityToken. O SecurityTokenResolver deve conter um SecurityToken que resolve o SecurityKeyIdentifier.|  
|ChildNodeTypeMissing|O elemento XML especificado não tem um filho do tipo especificado.|  
|TraceCodeSecurityPendingServerSessionClosed|A sessão de segurança pendente foi fechada pelo servidor.|  
|TraceCodeSecuritySessionCloseResponseSent|A sessão de segurança do servidor enviou uma resposta de fechamento para o cliente.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|A parte do nome do host de um endereço de ponto de extremidade não pode ser normalizada.|  
|FailAcceptSecurityContext|Falha de AcceptSecurityContext.|  
|EmptyXmlElementError|O elemento especificado não pode ser vazio.|  
|PrefixNotDefinedForNamespace|Um prefixo para o namespace especificado não está definido neste contexto e não pode ser declarado.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|O SamlAuthorizationDecisionStatement que está sendo lido encontrado para conter mais de uma evidência. Isso não é permitido.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|A classe SamlSecurityTokenAuthenticator apenas pode processar SamlSecurityTokens. O valor de SecurityTokenType especificado foi recebida.|  
|SAMLAttributeStatementMissingAttributeOnRead|O SamlAttributeStatement que está sendo lido não contém quaisquer elementos 'SamlAttribute'. Isso não é permitido.|  
|CouldNotFindNamespaceForPrefix|Não é possível pesquisar o namespace para o prefixo especificado.|  
|TraceCodeExportSecurityChannelBindingExit|ExportChannelBinding de segurança concluída.|  
|AESCryptDecryptFailed|Falha ao descriptografar os dados especificados.|  
|SAMLAttributeNamespaceAttributeRequired|O 'Namespace' especificado para um SamlAttribute não pode ser nulo ou tem comprimento 0.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator concluiu a negociação SSPI.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|A sessão de segurança do servidor enviou uma falha de renovação de chave para o cliente.|  
|AlgorithmMismatchForTransform|Ocorreu uma incompatibilidade no algoritmo para a transformação.|  
|UserNameAuthenticationFailed|Falha na autenticação de um nome de usuário/senha usando o mecanismo especificado. Usuário não está autenticado.|  
|SamlInvalidSigningToken|A SamlAssertion foi assinada com um token de acordo com o protocolo, não foi validado. Se você estiver usando certificados x. 509, examine suas semânticas de validação.|  
|TraceCodeSecurityServerSessionKeyUpdated|A chave de sessão de segurança foi atualizada pelo servidor.|  
|TraceCodeSecurityServerSessionCloseReceived|A sessão de segurança do servidor recebeu uma mensagem de fechamento do cliente.|  
|SAMLAuthenticationStatementMissingSubject|O SamlAuthenticationStatement está faltando a classe de SamlSubjectStatement necessária.|  
|UnexpectedEndOfFile|Fim inesperado do arquivo.|  
|UnsupportedAlgorithmForCryptoOperation|Não há suporte para o algoritmo especificado para a operação especificada.|  
|XmlLangAttributeMissing|O atributo XML: lang necessário está ausente.|  
|TraceCodeSecurityImpersonationSuccess|Representação de segurança bem-sucedida no servidor.|  
|SAMLAuthorityBindingMissingLocationOnRead|O atributo 'Local' para o SamlAuthorityBinding que está sendo lido está ausente ou tem comprimento 0.|  
|SAMLAttributeStatementMissingSubjectOnRead|O elemento 'SamlSubject' para SamlAttributeStatement está ausente.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|O elemento 'SamlSubject' para SamlAuthorizationDecisionStatement que está sendo lida está ausente.|  
|SAMLBadSchema|Durante a leitura de uma SamlAssertion esse elemento especificado foi encontrado não estar em conformidade com o esquema.|  
|SAMLAssertionIDIsInvalid|A 'assertionId' especificada para uma SamlAssertion deve começar com uma letra ou um '_'.|  
|TraceCodeSecurityActiveServerSessionRemoved|Uma sessão de segurança do Active Directory foi removida pelo servidor.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Não é possível criar keyedHashAlgorithm para o algoritmo especificado a partir da criptografia simétrica especificada.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|O 'AuthenticationMethod' especificado para um SamlAuthenticationStatement não pode ser nulo ou tem comprimento 0.|  
|TraceCodeSecurityImpersonationFailure|Falha na representação de segurança no servidor.|  
|Padrão|(Padrão)|  
|UnsupportedNodeTypeInReader|Não há suporte para o tipo de nó especificado com o nome especificado.|
