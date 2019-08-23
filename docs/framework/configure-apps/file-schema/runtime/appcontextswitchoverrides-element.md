---
title: Elemento <AppContextSwitchOverrides>
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a71277c6e5183f855ef07a6fc3a20e29b06998f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920919"
---
# <a name="appcontextswitchoverrides-element"></a>\<Elemento de > AppContextSwitchOverrides
Define uma ou mais opções usadas pela classe <xref:System.AppContext> para fornecer um mecanismo de recusa de uma nova funcionalidade.  
  
 \<configuration>  
 \<runtime>  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`value`|Atributo obrigatório.<br /><br /> Define um ou mais nomes de comutador e seus valores Boolianos associados.|  
  
### <a name="value-attribute"></a>Atributo de valor  
  
|Valor|Descrição|  
|-----------|-----------------|  
|"name=value"|Um nome de opção predefinido junto com seu`true` valor `false`(ou). Vários pares de nome/valor de comutador são separados por ponto e vírgula (";"). Para obter uma lista de nomes de comutador predefinidos com suporte pelo .NET Framework, consulte a seção comentários.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 A partir do .NET Framework 4,6, o `<AppContextSwitchOverrides>` elemento em um arquivo de configuração permite que os chamadores de uma API determinem se seu aplicativo pode aproveitar a nova funcionalidade ou preservar a compatibilidade com versões anteriores de uma biblioteca. Por exemplo, se o comportamento de uma API tiver sido alterado entre duas versões de uma biblioteca, `<AppContextSwitchOverrides>` o elemento permitirá que os chamadores dessa API recusem o novo comportamento nas versões da biblioteca que dão suporte à nova funcionalidade. Para aplicativos que chamam APIs no .NET Framework, o `<AppContextSwitchOverrides>` elemento também pode permitir chamadores cujos aplicativos se destinam a uma versão anterior do .NET Framework para aceitar novas funcionalidades se seu aplicativo estiver em execução em uma versão do .NET Framework que inclui essa função.  
  
 O `value` atributo`<AppContextSwitchOverrides>` do elemento consiste em uma única cadeia de caracteres que consiste em um ou mais pares de nome/valor delimitados por ponto e vírgula.  Cada nome identifica uma opção de compatibilidade e seu valor correspondente é um booliano`true` ( `false`ou) que indica se a opção está definida. Por padrão, o comutador `false`é, e as bibliotecas fornecem a nova funcionalidade. Eles só fornecem a funcionalidade anterior se a opção for definida (ou seja, seu valor for `true`). Isso permite que as bibliotecas forneçam um novo comportamento para uma API existente, permitindo aos chamadores que dependem do comportamento anterior para recusar a nova funcionalidade.  
  
 O .NET Framework dá suporte às seguintes opções:  
  
|Nome do comutador|Descrição|Incluída|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Controla se Windows Presentation Foundation usa um algoritmo herdado para o layout de controle. Para obter mais informações, confira [Mitigação: Layout](../../../migration-guide/mitigation-wpf-layout.md)do WPF.|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Controla se o algoritmo padrão usado para assinar partes de um pacote por PackageDigitalSignatureManager é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Quando definido como `false`, permite a depuração de projetos de fluxo de trabalho baseados em XAML com o Visual Studio quando o FIPS está habilitado. Sem ele, um <xref:System.NullReferenceException> é lançado em chamadas para métodos no assembly System. Activities.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Controla se a soma de verificação de uma instância de fluxo de trabalho no depurador usa MD5 ou SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Controla se o hash de soma de verificação do fluxo de trabalho usa o algoritmo SHA1 introduzido como`true`o padrão no .NET Framework 4,7 (), ou se ele usa o algoritmo SHA256 padrão introduzido como`false`o padrão em .NET Framework 4,8 ().<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Controla se os rastreamentos de pilha obtêm ao usar PDBs portáteis podem incluir informações de arquivo e linha de origem. `false`para incluir informações de arquivo e linha de origem; caso contrário `true`,.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Controla se o <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> método gera uma exceção quando um <xref:System.Drawing.Icon> objeto tem quadros png. Para obter mais informações, confira [Mitigação: Quadros PNG em objetos](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)Icon.|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Determina se <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> os <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> objetos são descartados corretamente quando adicionados à coleção pelo método. `true`para manter o comportamento herdado; `false` para descartar todos os objetos de fonte privada. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Controla se o desempenho do <xref:System.Windows.Forms.PrintPreviewDialog> é otimizado para impressoras de rede. Para obter mais informações, consulte [visão geral do controle PrintPreviewDialog](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Controla se o intervalo de ano verifica se o calendário japonês apagar está imposto. `true`para impor verificações de intervalo de ano `false` e para desabilitá-las (o comportamento padrão). Para obter mais informações, consulte [trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Controla se apenas "1" é reconhecido como o primeiro ano de uma era do calendário japonês em operações de análise. `true`para reconhecer apenas "1"; `false` para reconhecer "1" ou Gannen (o comportamento padrão). Para obter mais informações, consulte [trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Controla se o primeiro ano de uma era do calendário japonês é representado como "1" ou Gannen nas operações de formatação. `true`para formatar o primeiro ano da era como "1"; `false` para formatá-lo como Gannen (o comportamento padrão). Para obter mais informações, consulte [trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Controla se as operações assíncronas não fluem do contexto do thread de chamada. Para obter mais informações, consulte o [fluxo CurrentCulture e CurrentUICulture entre as tarefas](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Controla se o <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> método tenta corresponder ao tipo de declaração somente com a última entrada DNS. Para obter mais informações, confira [Mitigação: Método](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)X509CertificateClaimSet. FindClaims.|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Controla se o AuthorizationContext. Empty deve ser permitido para retornar um objeto mutável.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Controla se os caminhos com `MAX_PATH` mais de (260 caracteres) <xref:System.IO.PathTooLongException>lançam um. Para obter mais informações, consulte [suporte de caminho longo](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Controla se as <xref:System.IO.Compression.DeflateStream> rotinas de sistema operacional nativas são usadas para descompactação pela classe. `false`para usar APIs nativas; para usar a <xref:System.IO.Compression.DeflateStream>implementação. `true`|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Usa a barra invertida (\\"") em vez da barra "/") como o separador de caminho <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> na propriedade. Para obter mais informações, [consulte mitigação: Separador](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)de caminho ZipArchiveEntry. FullName.|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Controla se as exceções do sistema operacional que são geradas em threads em segundo plano criados com <xref:System.IO.Ports.SerialPort> fluxos encerram o processo.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Controla se a normalização de caminho herdado é usada e caminhos de <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> URI são suportados pelos métodos e. <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> Para obter mais informações, confira [Mitigação: Normalização](../../../migration-guide/mitigation-path-normalization.md) e mitigação de [caminho: Verificações](../../../migration-guide/mitigation-path-colon-checks.md)de ponto-e-vírgula.|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Controla se um teste de igualdade compara a <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> propriedade de um objeto com a <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> Propriedade do segundo objeto. Para obter mais informações, consulte [implementação incorreta de MemberDescriptor. Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Desabilita a validação de OID (identificador de objeto) de EKU (uso avançado de chave). Uma extensão de EKU (uso avançado de chave) é uma coleção de OIDs (identificadores de objeto) que indicam os aplicativos que usam a chave.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Desabilita a mitigação de navegador TLS 1.0 contra atenuação de SSL/TLS (fera) ao desabilitar o uso de SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Controla se as <xref:System.Net.ServicePointManager?displayProperty=nameWithType> classes <xref:System.Net.Security.SslStream?displayProperty=nameWithType> e podem usar o protocolo SSL 3,0. Para obter mais informações, confira [Mitigação: protocolos TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Desabilita as versões do SystemDefault TLS retornando de volta para um padrão de Tls12, Tls11, TLS.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Desabilita os alertas do lado do servidor SslStream TLS.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Controla se os parâmetros de ByRef SafeArray em eventos de interoperabilidade com fazem`false`marshaling de volta para o código nativo () ou se`true`o marshaling de volta para o código nativo está desabilitado ().|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Controla se o [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializa alguns caracteres de controle com base nos padrões do ECMAScript V6 e do V8. Para obter mais informações, confira [Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Controla se o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dá suporte a vários ajustes ou apenas a um único ajuste para um fuso horário. Se `true`, ele usa o <xref:System.TimeZoneInfo> tipo para serializar e desserializar dados de data e hora; caso contrário, <xref:System.TimeZone> ele usa o tipo, que não dá suporte a várias regras de ajuste.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Controla se <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> o usa um tamanho de matriz maior durante a serialização e a desserialização do objeto. Defina essa opção como `true` para melhorar o desempenho de serialização e desserialização de grafos de objeto grande por tipos <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>como. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Controla se o <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> construtor define a propriedade do <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> novo objeto com uma referência de objeto existente. Para obter mais informações, confira [Mitigação: Construtor](../../../migration-guide/mitigation-claimsidentity-constructor.md)ClaimsIdentity.|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Controla se a tentativa de reutilizar <xref:System.Security.Cryptography.AesCryptoServiceProvider> um descriptografador <xref:System.Security.Cryptography.CryptographicException>gera um. Para obter mais informações, consulte [o descriptografador AesCryptoServiceProvider fornece uma transformação](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)reutilizável.|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Controla se o valor da propriedade [CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) é um [IntPtr](xref:System.IntPtr) que representa o local da memória de um identificador de janela ou se é um identificador de janela (um HWND). Para obter mais informações, confira [Mitigação: CspParameters. ParentWindowHandle espera um HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Controla se o uso de classes de criptografia gerenciadas no modo FIPS <xref:System.Security.Cryptography.CryptographicException> gera`true`um () ou se baseia na implementação das bibliotecas do`false`sistema ().|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Determina se o padrão para algumas operações SignedCMS é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Controla se o <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> método manipula corretamente todas as curvas nomeadas com suporte pelo sistema`false`operacional () ou reverte para o comportamento herdado.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Determina se o padrão para algumas operações SignedXML é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Determina se o `TransportWithMessageCredential` modo de segurança permite mensagens com um cabeçalho "para" não assinado. Essa é uma opção opcional. Para obter mais informações, consulte [alterações de tempo de execução no .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Controla se o <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Construtor gera um <xref:System.ArgumentException> se um dos elementos é `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Determina se a tentativa de usar certificados X509 com um provedor de armazenamento de chaves CSG gera uma exceção. Para obter mais informações, consulte a [segurança de transporte do WCF dá suporte a certificados armazenados usando a CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Ao usar o transporte HTTP com um serviço hospedado internamente, definir esse valor como `true` faz com que o WCF ignore um aplicativo adicionando o `Connection: close` cabeçalho aos cabeçalhos de resposta de uma solicitação. Definir esse valor como `false` permite adicionar o `Connection: close` cabeçalho aos cabeçalhos de resposta, o que resulta no fechamento do soquete de solicitação depois que uma resposta é enviada.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Manipula deadlocks que resultam da restrição de instâncias de um serviço reentrante para um único thread de execução de cada vez.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Juntamente com `Switch.System.Net.DontEnableSchUseStrongCrypto`o, o determina se a segurança de mensagens do WCF usa TLS 1,1 e TLS 1,2.|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Um valor `false` define a configuração padrão para permitir que o sistema operacional escolha o protocolo. Um valor de `true` define o padrão para o protocolo mais alto disponível. (Também disponível no Branch de manutenção das versões anteriores do Framework)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Determina se o algoritmo de assinatura de mensagem padrão para mensagens MSMQ no WCF é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Controla se o WCF usa um hash SHA1 ou SHA256 para gerar nomes aleatórios para pipes nomeados.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Controla se uma [NullReferenceException](xref:System.NullReferenceException) é lançada quando a mensagem de exceção é nula.|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Controla se as exceções geradas na inicialização do serviço são propagadas para <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> o chamador do método.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Controla se <xref:System.Threading.Timer> as instâncias aproveitam as melhorias de desempenho para ambientes de grande escala. Se `true`as melhorias de desempenho estiverem habilitadas; `false` se (o valor padrão), elas serão desabilitadas.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Determina se determinados caracteres codificados por porcentagem, às vezes decodificados, agora são codificados sempre à esquerda. Se `true`eles forem decodificados; caso contrário, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Determina a manipulação de caracteres bidirecionais Unicode em URIs. `true`para stripá-los de URIs; `false` para preservar e codificar por porcentagem.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Determina se Windows Presentation Foundation aplica um algoritmo antigo (`true`) ou um novo algoritmo (`false`) na alocação de espaço \*para colunas. Para obter mais informações, confira [Mitigação: Alocação de espaço do controle de grade para colunas](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns)em estrela. |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Controla se um seletor ou um controle guia sempre atualiza o valor de sua propriedade de valor selecionado antes de gerar o evento de alteração de seleção.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Determina se a renderização de seleção não baseada em adorno está disponível <xref:System.Windows.Controls.TextBox> para <xref:System.Windows.Controls.PasswordBox> os controles e para evitar texto`false`obstruído () ou se o texto é renderizado apenas na camada`true`de adorno ().|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Controla se os`false``true` indexadoresdeIListpersonalizadossãousadosincorretamente()oucorretamente(<xref:System.Windows.Data.Binding?displayProperty=nameWithType> ) pela classe.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Determina se as alterações de DPI ocorrem em um por sistema (um valor `false`) ou base por monitor (um valor de `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Controla se os aprimoramentos no dimensionamento de <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> controles em um quando o WPF é executado no modo de reconhecimento por`true`monitor são desabilitados`false`() ou habilitados ().|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Determina se o desenvolvedor precisa lidar especialmente com a <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ação quando o texto de controle está presente. `true`para lidar com <xref:System.Windows.Forms.DomainUpDown.UpButton> a ação; para que <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> as <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ações e sejam corretamente sincronizadas. `false`|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Opta pelo código que permite uma implementação personalizada <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> para filtrar mensagens com segurança sem lançar uma exceção quando o <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> método é chamado. Para obter mais informações, confira [Mitigação: Implementações](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)personalizadas de IMessageFilter. PreFilterMessage.|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Determina se a <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriedade retorna o controle do código-fonte quando o usuário abre o menu <xref:System.Windows.Forms.ToolStripMenuItem> a partir de um controle aninhado. `true`para retornar `null`, o comportamento herdado; `false` para retornar o controle do código-fonte.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Controla se o suporte à chamada de dica de`true`ferramenta está desabilitado`false`() ou habilitado (). Habilitar o suporte à invocação de ToolTip também requer recursos de `Switch.UseLegacyAccessibilityFeatures`acessibilidade `Switch.UseLegacyAccessibilityFeatures.2`herdados `Switch.UseLegacyAccessibilityFeatures.3` definidos por, e todos eles `false`serão desabilitados (definido como).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Determina se uma pilha `WM_POINTER`de toque/caneta baseada em opcional está habilitada em aplicativos do WPF. Para obter mais informações, confira [Mitigação: Toque com base em ponteiro e suporte à caneta](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Determina se o algoritmo de hash padrão usado para somas de verificação`false`é SHA256 ()`true`ou SHA1 ().<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Controla se uma [NullReferenceException](xref:System.NullReferenceException) herdada é lançada em vez da exceção que indica mais especificamente a causa da exceção (como um [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) ou um [FileNotFoundException](xref:System.IO.FileNotFoundException). Ele é destinado ao uso pelo código que depende da manipulação da [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Controla se o hash de soma de verificação de arquivos xoml em compilações do projeto de`true`fluxo de trabalho usa o algoritmo MD5 () ou se eles usam o algoritmo SHA256 introduzido como padrão no .NET Framework 4,8.<br>Devido a problemas de colisão com o MD5, a Microsoft recomenda o SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Controla se o hash de soma de verificação pelo SqlTrackingService usa o algoritmo`true`MD5 () para cadeias de caracteres em cache ou se ele usa o algoritmo SHA256 introduzido como padrão no .NET Framework 4,8.<br>Devido a problemas de colisão com o MD5, a Microsoft recomenda o SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Controla se o hash de soma de verificação pelo tempo de execução do fluxo`true`de trabalho usa o algoritmo MD5 () para definições de fluxo de trabalho em cache ou se ele usa o algoritmo SHA256 introduzido como padrão no .NET Framework 4,8.<br>Devido a problemas de colisão com o MD5, a Microsoft recomenda o SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Controla se os recursos de acessibilidade disponíveis a partir do .NET Framework 4.7.1 estão habilitados ou desabilitados. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Controla se os recursos de acessibilidade disponíveis no .NET Framework 4.7.2 estão`false`habilitados ()`true`ou desabilitados (). Se `true` `true` , `Switch.UseLegacyAccessibilityFeatures` também deve ser para habilitar os recursos de acessibilidade do .NET Framework 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Controla se os recursos de acessibilidade introduzidos no .NET Framework 4,8`false`estão habilitados (`true`) ou desabilitados (). Se `true`e tambémdevem`true`ser. `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Controla se tooltips são exibidas quando um usuário passa o cursor do mouse sobre um controle WPF (`true`), ou se eles são exibidos no foco do teclado e por meio da tecla de`false`atalho do teclado (, o comportamento padrão). Para aplicativos em execução no .NET Framework 4,8, mas que visam versões anteriores do .NET Framework, habilitar o foco do teclado e o `Switch.UseLegacyAccessibilityFeatures`suporte `Switch.UseLegacyAccessibilityFeatures.2`à tecla de atalho requer que `false`, e `Switch.UseLegacyAccessibilityFeatures.3` todos estejam definidos como.|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Controla se as sequências de chaves vazias em chaves compostas são ignoradas pela validação de esquema XSD. Para obter mais informações, confira [Mitigação: Validação](../../../migration-guide/mitigation-xml-schema-validation.md)de esquema XML.|.NET Framework 4.6|  
  
> [!NOTE]
> Em vez de adicionar `AppContextSwitchOverrides` um elemento a um arquivo de configuração de aplicativo, você também pode definir as opções programaticamente C#chamando o `Shared` `static` método (in) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> ou (no Visual Basic).  
  
 Os desenvolvedores de biblioteca também podem definir opções personalizadas para permitir que os chamadores recusem a funcionalidade alterada introduzida em versões posteriores de suas bibliotecas. Para obter mais informações, consulte a classe <xref:System.AppContext>.  
  
## <a name="switches-in-aspnet-applications"></a>Opções em aplicativos ASP.NET

Você pode configurar um aplicativo ASP.net para usar as configurações de compatibilidade adicionando um [ \<elemento add >](../appsettings/add-element-for-appsettings.md) à [ \<seção appSettings >](../appsettings/index.md) do arquivo Web. config. 

O exemplo a seguir usa `<add>` o elemento para adicionar duas configurações `<appSettings>` à seção de um arquivo Web. config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Exemplo

 O exemplo a seguir usa `AppContextSwitchOverrides` o elemento para definir uma única opção de compatibilidade `Switch.System.Globalization.NoAsyncCurrentCulture`de aplicativo,, que impede que a cultura flua entre threads em chamadas de método assíncronas.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 O exemplo a seguir usa `AppContextSwitchOverrides` o elemento para definir duas `Switch.System.Globalization.NoAsyncCurrentCulture` opções de compatibilidade de `Switch.System.IO.BlockLongPaths`aplicativos e. Observe que um ponto e vírgula separa os dois pares de nome/valor.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<Elemento de > de tempo de execução](runtime-element.md)
- [Elemento \<configuration>](../configuration-element.md)
