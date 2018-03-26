---
title: Ferramentas
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5badbb9142261fc1dc6c2b2d5af3c89c7af776b6
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="tools"></a>Ferramentas
Este tópico lista todas as exceções geradas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ferramentas.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|ParametersTarget|\<enum>|  
|ParametersToolConfig|\<configFile>|  
|ErrInvalidPath|Especificado é um caminho inválido. Verifique se o argumento especificado.|  
|ParametersReference|\<caminho do arquivo >|  
|WrnCannotLoadConfigFileForValidation|Erro ao processar o arquivo de configuração carregados do local especificado. Serviços que estão definidos no arquivo de configuração não podem ser validados.|  
|MoreHelp|Para obter mais ajuda, digite "svcutil" com os argumentos especificados.|  
|HelpMergeConfig|Faz com que a configuração gerada ser mesclados em um arquivo existente em vez de substituir o arquivo existente.|  
|ErrCannotWriteFile|Não é possível gravar em um arquivo de saída.|  
|ErrInvalidNamespaceArgument|O valor especificado de inválido foi passado para a opção especificada. Especifique um par de namespace do CLR e o namespace de destino separados por vírgulas.|  
|HelpImportXmlType|Configura o serializador DataContract para importar os tipos não DataContract como IXmlSerializable tipos.|  
|ErrExclusiveOptionsSpecified|A opção especificada não pode ser usada quando a opção de especificado tiver sido especificada.|  
|WrnHttpGetFailed|OBTER erro de HTTP com o URI especificado.|  
|ErrInputFileNotAssemblyOrMetadata|O arquivo no local especificado lido por meio do argumento de entrada especificado não parece ser um arquivo de metadados XML ou um assembly válido.|  
|WrnUnknownMetadataFound|Não é possível salvar o documento de metadados não reconhecida do tipo especificado.|  
|ErrDirectoryContainsInvalidCharacters|O valor especificado de inválido foi passado para a opção especificada. O caractere especificado não é permitido em um caminho.|  
|WrnCannotResolveServiceForValidation|Não é possível carregar um serviço com o configName especificado. Para validar um serviço, forneça o assembly que contém o tipo de serviço e um executável com a configuração para este serviço.|  
|ErrUnexpectedValue|A opção especificada não dá suporte a todos os valores.|  
|#InvalidArg|Especificado contém um argumento inválido.|  
|ParametersExcludeType|\<type>|  
|HelpXmlSerializer|Gere tipos de dados que usam o XmlSerializer para serialização e desserialização.|  
|#|---------------------------------------------------------------------------------------------------------------------=|  
|ErrUnexpectedError|Ocorreu um erro na ferramenta.|  
|HelpNologo|A mensagem de direitos autoral e faixa é suprimida.|  
|ErrInputConflictsWithTarget|Não há suporte para o tipo de leitura de entrada especificado com a opção especificada definida como o valor especificado.|  
|WrnCannotLoadServiceForExport|Ocorreu um erro ao carregar o tipo de serviço a ser exportado.|  
|HelpMetadataDownloadCategory|-= DOWNLOAD DE METADADOS =-|  
|WrnNoServiceContractTypes|Não é possível gerar o XmlSerializer tipos para o assembly especificado. Nenhum tipo de contrato de serviço foram encontrado.|  
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|Ocorreu um erro ao carregar tipos em um assembly que foi carregado especificado. Alguns tipos no assembly não podem ser carregados e não estão disponíveis para a ferramenta.|  
|ErrDirectoryPointsToAFile|O valor especificado de inválido foi passado para a opção especificada. O valor especificado é um caminho para um arquivo.|  
|Erro|Erro:|  
|ErrDuplicateReferenceValues|O assembly especificado foi carregado de duas vezes com a opção especificada. Um assembly só pode ser referência uma vez.|  
|WrnNoXmlSerializerOperationBehavior|Não é possível gerar o XmlSerializer para o assembly especificado. Nenhum contrato de serviço no assembly tem uma operação com XmlSerializerOperationBehavior.|  
|ErrCannotCreateDirectory|Não é possível criar o diretório especificado.|  
|ErrCouldNotLoadTypesFromAssemblyAt|Não é possível carregar todos os tipos no assembly especificado.|  
|ErrUnknownSwitch|A chave especificada é uma opção reconhecida.|  
|Logo|O logotipo da ferramenta é "Ferramenta de metadados do Microsoft® serviço modelo" com a versão.|  
|NoCodeWasGenerated|Nenhum código foi gerado.<br /><br /> Se você tentar gerar um cliente, isso pode ocorrer porque os documentos de metadados não continha nenhum contrato válido ou os serviços<br /><br /> ou, porque todos os contratos/serviços foram descobertos existam em assemblies de referência. Verifique se que todos os documentos de metadados é passado para a ferramenta.|  
|WrnUnableToLoadContractForSGen|Ocorreu um erro ao carregar um tipo de contrato. Não é possível gerar o tipo de XmlSerializer para este contrato. O tipo e os detalhes são especificados.|  
|WrnOptionConflictsWithInput|A opção especificada não pode ser usada com vários assemblies de entrada. A opção especificada é ignorada.|  
|ErrUnableToImportMetadata|Ocorreu um erro crítico ao tentar importar metadados.|  
|ErrInvalidSerializer|Um valor de serializador inválido foi passado para a opção especificada. Os serializadores com suporte são especificados.|  
|SavingDownloadedMetadata|Salvando arquivos de metadados baixado...|  
|WrnNoConfigForServices|Nenhum dos assemblies passados foram executáveis com o arquivo de configuração ou nenhum dos serviços de arquivos contidos de configuração com o nome de configuração especificado.|  
|ErrInputConflictsWithOption|A entrada de leitura especificado não pode ser usada com a opção especificada porque eles implicam diferentes modos de operação da ferramenta.|  
|ErrUnableToExportEndpoints|Ocorreu um erro ao exportar o tipo de serviço especificado.|  
|ErrInputSchemaParseError|Um esquema XML ao analisar o erro ocorreu durante a leitura especificado. Verifique se o XML está bem formado e válido.|  
|ErrInputPolicyParseError|Ocorreu um erro de análise do WS-Policy ao ler especificado. Verifique se o XML está bem formado e válido.|  
|ErrUnableToLoadReferenceType|Ocorreu um erro ao carregar um tipo de contrato referenciado. Esse tipo especificado será ignorado.|  
|WrnCannotLoadServiceForValidation|Ocorreu um erro ao carregar o serviço a ser validado. O tipo e os detalhes são especificados.|  
|HelpCodeGenerationCategory|-= GERAÇÃO DE CÓDIGO =-|  
|RetreivingMetadataWithMexAndDisco|Tentativa de fazer o download de metadados especificado usando o WS-Metadata Exchange ou DISCO.|  
|ErrGeneralSchemaValidation|Ocorreu um erro ao verificar se os esquemas XML que foram gerados durante a exportação.|  
|ParametersDirectory|\<directory>|  
|ErrCannotLoadSpecifiedType|Nenhum tipo pode ser carregado para o valor especificado foi passado para a opção especificada. Certifique-se de que o assembly que pertence este tipo é especificado usando a opção especificada.|  
|ErrOptionModeConflict|A opção especificada não pode ser usada com a opção especificada porque eles implicam tipos de saída diferente.|  
|ErrIsNotAnAssembly|Não é possível carregar especificado como um assembly. Verifique se esse arquivo é um assembly .NET.|  
|ErrInputConflictsWithMode|A entrada de leitura especificado é inconsistente com outras opções.|  
|ErrDuplicateValuePassedToTypeArg|O valor especificado foi passado para a opção especificada várias vezes. Cada tipo pode ser especificado somente uma vez.|  
|ErrInputEPRFileParseError|Não é possível ler a referência de ponto de extremidade especificado. Verifique se o XML está bem formado e válido.|  
|ErrCouldNotCreateCodeProvider|Um provedor de código não pode ser criado para o valor especificado, que foi passado para o argumento /{1}. Verifique se o provedor de código está instalado e configurado corretamente.|  
|ErrPathTooLongDirOnly|O caminho especificado resultante é muito longo. Examine o argumento especificado.|  
|HelpDataContractSerializer|Gere tipos de dados que usam o serializador DataContract para serialização e desserialização.|  
|ErrUnableToExportEndpoint|Ocorreu um erro ao exportar o nome do ponto de extremidade especificado no namespace especificado no tipo de serviço especificado encontrado no arquivo de configuração carregado para o assembly.|  
|HelpUsage1|Exibe a ajuda uso.|  
|HelpUsage2|Exibe a ajuda uso.|  
|HelpUsage3|Exibe a ajuda uso.|  
|HelpUsage4|Exibe a ajuda uso.|  
|HelpUsage5|Exibe a ajuda uso.|  
|ErrDirectoryNotFound|O diretório especificado não foi encontrado. Verifique se o diretório existe e se você tem as permissões apropriadas para lê-lo.|  
|ErrUnableToLoadFile|Não é possível ler o arquivo especificado.|  
|ErrNoFilesFound|O caminho de entrada especificado não parece se referir a arquivos existentes.|  
|ParametersConfig|\<configFile>|  
|ErrDirectoryInsteadOfFile|O caminho de entrada especificado parece ser um diretório. Entrada deve ser URLs ou caminhos de arquivo.|  
|HelpConfig|Instrui as ferramentas para gerar um arquivo de configuração com o nome fornecido. Padrão: Output.|  
|ErrSingleUseSwitch|A opção especificada não pode ser especificada várias vezes.|  
|Aviso|Aviso:|  
|WrnAmbiguousServiceConfig|Foram encontradas várias configurações de serviço com o nome de configuração especificado, os seguintes assemblies são especificados.|  
|ErrInvalidInputPath|O caminho de entrada especificado não parece se referir a arquivos existentes e não parece ser um URI válido.|  
|ErrUnableToLoadInputs|Ocorreu um erro ao ler os metadados carregado.|  
|GeneratingSerializer|Gerando serializadores XML...|  
|HelpToolConfig|Arquivo de configuração personalizada para usar no lugar do arquivo de configuração do aplicativo. Isso pode ser usado para alterar a configuração de metadados ou registrar extensões de configuração sem alterar o arquivo de configuração da ferramenta.|  
|ErrValidateInvalidUse|A opção especificada não pode ser usada com a opção especificada.|  
|WrnWSMExFailed|Erro do WS-Metadata Exchange com o URI especificado.|  
|HelpNoconfig|Não gere configuração.|  
|HelpCodeGenerationDescription|Especificado pode gerar tipos de dados, os clientes e contratos de serviço de documentos de metadados.|  
|HelpTargetMetadata|Metadados de saída. Se a entrada for uma URL, Svcutil.exe salva os metadados no disco e não gerar código. Se a entrada é um ou mais assemblies, Svcutil.exe gera metadados de tipos em assemblies.|  
|ErrAmbiguousOptionModeConflict|A opção especificada está em conflito com outras opções. Analise o uso da ferramenta.|  
|ErrNotLanguageOrCodeDomType|O valor especificado foi passado para o argumento especificado não representa um idioma definido e ele não pode ser carregado como um tipo CLR totalmente qualificado.|  
|ErrUnableToUniquifyFilename|Não é possível criar nome de arquivo de saída. Número excessivo de arquivos está sendo criado com o prefixo especificado.|  
|ErrCannotCreateFile|Não é possível criar o arquivo de saída especificado.|  
|ErrExpectedValue|A opção especificada requer que um valor seja especificado.|  
|ErrCannotDisambiguateSpecifiedTypes|Mais de um tipo com o mesmo nome existe no conjunto de assemblies referenciados. Use nomes de assembly qualificado para distinguir entre os tipos especificados para a opção especificada.|  
|RetreivingMetadataWithMexOnly|Tentando fazer o download de metadados do local especificado usando o WS-Metadata Exchange. Essa URL não oferece suporte a DISCO.|  
|ErrInvalidTarget|O destino especificado é inválido quando especificado usando a opção especificada. Os destinos com suporte são especificados.|  
|ErrPathTooLong|O caminho resultante é muito longo. Examine os argumentos especificados.|  
|HelpCommonOptionsCategory|-= OPÇÕES COMUNS =-|  
|ParametersServiceName|\<serviceConfigName>|  
|ErrNoValidInputFilesSpecified|Nenhum arquivo de entrada válido especificado. Especifique documentos de metadados ou arquivos de assembly.|  
|ParametersLanguage|\<language>|  
|ErrUnableToLoadMetadataDocument|Ocorreu um erro ao ler os metadados de um dos documentos carregados. O identificador do documento é especificado.|  
|ErrConflictingInputs|Os conflitos de argumento de entrada especificado com especificado porque eles implicam diferentes modos de operação da ferramenta.|  
|WrnUnableToLoadContractForValidation|Ocorreu um erro ao carregar um tipo de contrato. O tipo e os detalhes são especificados.|  
|WrnAttributeReflectionErrors|Reflexão falhou para alguns dos tipos no assembly que foram carregados do atributo especificado. Verifique se que este assembly pode ser carregado nesse local com os privilégios de segurança correta.|  
|HelpMetadataExportCategory|-= EXPORTAÇÃO DE METADADOS =-|  
|HelpValidationCategory|-= VALIDAÇÃO DE SERVIÇO =-|  
|ValidationError|Erro de validação:|  
|GeneratingFiles|Gerando arquivos...|  
|ErrCannotSpecifyMultipleMappingsForNamespace|Um valor inválido foi passado para a opção especificada. O namespace de destino especificado não pode ser mapeado para vários namespaces CLR, conforme especificado.|  
|ErrCouldNotLoadReferenceAssemblyAt|Não é possível carregar o assembly de referência especificado.|  
|ParametersOut|\<file>|  
|NoCodeWasGeneratedSuggestDCOnly|Para gerar contratos de esquemas, use a opção especificada.|  
|ErrUnableToLoadInputConfig|Não é possível carregar o arquivo de configuração especificado.|  
|ErrUnexpectedDelimiter|Um delimitador de argumento inválido (': ' ou '=') não é possível iniciar a opção.|  
|ErrMergeConfigUsedWithoutConfig|Não é possível usar a opção especificada sem especificar a outra opção especificada.|  
|ErrUnableToExportContract|Erro ao exportar o contrato de carregados do tipo especificado.|  
|GeneratingMetadata|Gerando arquivos de metadados...|  
|ErrNotCodeDomType|O tipo especificado que foi passado para o argumento especificado não é da classe derivada especificada.|  
|WrnNoTypeForServices|Nenhum dos assemblies que foram transmitidos a tipos de serviço independentes com o nome de configuração especificado.|  
|ErrAssemblyLoadFailed|Não é possível carregar o arquivo especificado como um Assembly. Verifique o FusionLogs para obter mais informações.|  
|NoMetadataWasGenerated|Nenhum arquivo de metadados foram gerado. Nenhum contrato de serviço foram exportado.<br /><br /> Para exportar um serviço, use a opção especificada. Para exportar os contratos de dados, especifique a opção.|  
|WrnCannotResolveServiceForExport|Não é possível carregar um serviço com o configName especificado. Para exportar um serviço, forneça o assembly que contém o tipo de serviço e um executável com a configuração para este serviço.|  
|ParametersCollectionType|\<type>|  
|ErrOptionConflictsWithTarget|Não há suporte para o uso da opção especificada com a opção especificada definida como o valor especificado.|  
|ErrCodegenError|Ocorreu um erro ao gerar o código no idioma especificado.<br /><br /> O idioma não oferece suporte a todos os elementos de código que está sendo gerados. Outro idioma deve ser usado.|  
|ErrInputWsdlParseError|Ocorreu um erro de análise de WSDL ao ler especificado. Verifique se o XML está bem formado e válido.|  
|ErrCouldNotCreateInstance|Não é possível criar uma instância do tipo especificado que foi passado para o argumento especificado.|  
|ParametersNamespace|\<cadeia de caracteres, cadeia de caracteres >|  
|HelpNostdlib|Não faça referência a bibliotecas padrão (por padrão mscorlib.dll e system.servicemodel.dll são referenciadas.)|  
|WrnCannotLoadConfigFileForExport|Ocorreu um erro ao processar o arquivo de configuração que foi carregado especificado. Serviços que estão definidos no arquivo de configuração não podem ser carregados.|  
|WrnUnableToLoadContractForExport|Ocorreu um erro ao carregar um tipo de contrato. Esse tipo especificado não pode ser exportado.|
