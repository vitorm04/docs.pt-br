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
ms.openlocfilehash: 39060d503a006ab292818b58a6fa71f44dee68a0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423326"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides > elemento
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
|`value`|Atributo obrigatório.<br /><br /> Define um ou mais nomes de comutador e seus valores associados de boolianos.|  
  
### <a name="value-attribute"></a>valor de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|"name=value"|Um nome de comutador predefinidos, juntamente com seu valor (`true` ou `false`). Vários pares de nome/valor de opção são separados por ponto e vírgula (";"). Para obter uma lista de nomes de comutador predefinidas compatíveis com o .NET Framework, consulte a seção comentários.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 4.6, o `<AppContextSwitchOverrides>` elemento em um arquivo de configuração permite que os chamadores de uma API para determinar se o seu aplicativo pode tirar proveito da nova funcionalidade ou preservar a compatibilidade com versões anteriores de uma biblioteca. Por exemplo, se o comportamento de uma API foi alterado entre duas versões de uma biblioteca, o `<AppContextSwitchOverrides>` elemento permite que os chamadores dessa API para recusar o novo comportamento em versões da biblioteca que dão suporte a nova funcionalidade. Para aplicativos que chamam as APIs no .NET Framework, o `<AppContextSwitchOverrides>` elemento também pode permitir que os chamadores cujos aplicativos direcionam uma versão anterior do .NET Framework para aceitar novas funcionalidades se seu aplicativo estiver em execução em uma versão do .NET Framework que inclui que funcionalidade.  
  
 O `value` atributo do `<AppContextSwitchOverrides>` elemento consiste em uma única cadeia de caracteres que consiste em um ou mais pares de nome/valor delimitados por ponto e vírgula.  Cada nome identifica uma opção de compatibilidade e seu valor correspondente é um valor booliano (`true` ou `false`) que indica se a opção estiver definida. Por padrão, o comutador é `false`, e as bibliotecas fornecem a nova funcionalidade. Eles só fornecem a funcionalidade anterior se a opção é definida (isto é, seu valor é `true`). Isso permite que as bibliotecas fornecer o novo comportamento para uma API existente, permitindo que os chamadores que dependem do comportamento anterior para recusar a nova funcionalidade.  
  
 O .NET Framework suporta as seguintes opções:  
  
|Nome do comutador|Descrição|Introduzido|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Controla se o Windows Presentation Foundation usa herdado de um algoritmo para controlar o layout. Para obter mais informações, confira [Mitigação: Layout de WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Controla se o algoritmo padrão usado para assinar partes de um pacote por PackageDigitalSignatureManager é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Quando definido como `false`, permite a depuração de projetos de fluxo de trabalho baseado em XAML com o Visual Studio quando o FIPS está habilitado. Sem ele, um <xref:System.NullReferenceException> é gerada em chamadas para métodos no assembly System. Activities.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Controla se a soma de verificação para uma instância de fluxo de trabalho no depurador usa MD5 ou SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Controla se o hash de soma de verificação de fluxo de trabalho usa o algoritmo SHA1 introduzido como padrão no .NET Framework 4.7 (`true`), ou se ele usa o algoritmo padrão de SHA256 introduzido como padrão no .NET Framework 4.8 (`false`).<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Controla se os rastreamentos de pilha obtém ao usar PDBs portáteis pode incluir informações de arquivo e de linha de código-fonte. `false` para incluir informações de arquivo e de linha de código-fonte; Caso contrário, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Controles se o <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> método gera uma exceção quando um <xref:System.Drawing.Icon> objeto tiver quadros PNG. Para obter mais informações, confira [Mitigação: Quadros PNG em objetos de ícone](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Determina se <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> objetos sejam descartados corretamente quando adicionado à coleção, o <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> método. `true` para manter o comportamento herdado; `false` para descartar todos os objetos de fontes privadas. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Controles se o desempenho do <xref:System.Windows.Forms.PrintPreviewDialog> é otimizado para impressoras de rede. Para obter mais informações, consulte [visão geral do controle PrintPreviewDialog](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Controla se o intervalo de anos verifica para o calendário japonês eras são impostas. `true` para impor o intervalo de ano verifica, e `false` desabilitá-los (o comportamento padrão). Para obter mais informações, consulte [trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Controla se apenas "1" é reconhecido como o primeiro ano da era calendário japonês em operações de análise. `true` para reconhecer apenas de "1"; `false` reconhecer Gannen (o comportamento padrão) ou "1". Para obter mais informações, consulte [trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Controla se o primeiro ano da era calendário japonês é representado como "1" ou Gannen em operações de formatação. `true` Para formatar o primeiro ano do era como "1"; `false` formatá-lo como Gannen (o comportamento padrão). Para obter mais informações, consulte [trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Controla se as operações assíncronas não fluem do contexto do thread de chamada. Para obter mais informações, consulte [fluxo CurrentCulture e CurrentUICulture entre tarefas](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Controles se o <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> método tentará corresponder o tipo de declaração apenas com a última entrada DNS. Para obter mais informações, confira [Mitigação: Método X509CertificateClaimSet.FindClaims](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Controla se deve permitir AuthorizationContext.Empty retornar um objeto mutável.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Controles se caminhos com mais de `MAX_PATH` (260 caracteres) lançar um <xref:System.IO.PathTooLongException>. Para obter mais informações, consulte [suporte de caminho longo](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Controla se as rotinas nativas do sistema operacional são usadas para descompactação pelo <xref:System.IO.Compression.DeflateStream> classe. `false` usar APIs nativas; `true` para usar o <xref:System.IO.Compression.DeflateStream> implementação.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Usa a barra invertida ("\\") em vez de barra invertida ("/") como separador de caminho no <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriedade. Para obter mais informações, consulte [atenuação: Separador de caminho ziparchiveentry. FullName](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Controla se o operando de exceções do sistema que são geradas em threads em segundo plano criados com <xref:System.IO.Ports.SerialPort> fluxos encerram o processo.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Controla se a normalização do caminho herdado é usada e caminhos de URI são compatíveis com o <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> métodos. Para obter mais informações, confira [Mitigação: Normalização de caminho](../../../migration-guide/mitigation-path-normalization.md) e [atenuação: Verificações de dois-pontos no caminho](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Controla se um teste de igualdade compara os <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> propriedade de um objeto com o <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> propriedade do segundo objeto. Para obter mais informações, consulte [implementação incorreta de memberdescriptor. Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Desabilita a validação de OID (identificador) do objeto de uso avançado de chave (EKU) do certificado. Uma extensão de EKU (uso avançado de chave) é uma coleção de OIDs (identificadores de objeto) que indicam os aplicativos que usam a chave.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Desabilita a atenuação TLS1.0 navegador explorar contra SSL/TLS (FERA) desabilitando o uso de SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Controles se o <xref:System.Net.ServicePointManager?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes podem usar o protocolo SSL 3.0. Para obter mais informações, confira [Mitigação: protocolos TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Desabilita as versões do TLS SystemDefault reverter para um padrão de Tls, Tls11, Tls12.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Desabilita os alertas do lado do servidor TLS SslStream.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Controla se marshaling de parâmetros ByRef SafeArray em eventos de interoperabilidade de COM para código nativo (`false`) ou se o marshaling de volta para o código nativo está desabilitado (`true`).|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Controles se o [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializa alguns caracteres de controle com base nos padrões ECMAScript V6 e V8. Para obter mais informações, confira [Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Controles se o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dá suporte a vários ajustes ou apenas um único ajuste para um fuso horário. Se `true`, ele usa o <xref:System.TimeZoneInfo> de tipo para serializar e desserializar dados de data e hora; caso contrário, ele usa o <xref:System.TimeZone> tipo, que não oferece suporte a várias regras de ajuste.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Controles se <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> usa um tamanho de matriz maior durante a serialização de objeto e a desserialização. Definir essa opção como `true` para melhorar o desempenho de serialização e desserialização de grafos de objeto grande por tipos como <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Controles se o <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> construtor define o novo objeto <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> propriedade com uma referência de objeto existente. Para obter mais informações, confira [Mitigação: Construtor ClaimsIdentity](../../../migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Controles se a tentativa de reutilizar um <xref:System.Security.Cryptography.AesCryptoServiceProvider> descriptografador lança um <xref:System.Security.Cryptography.CryptographicException>. Para obter mais informações, consulte [descriptografador AesCryptoServiceProvider fornece uma transformação reutilizável](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Controles se o valor da [cspParameters. Parentwindowhandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) propriedade é um [IntPtr](xref:System.IntPtr) que tratar do representa o local da memória de uma janela, ou se é um identificador de janela (HWND). Para obter mais informações, confira [Mitigação: CspParameters. Parentwindowhandle espera um HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Controla se o uso de criptografia gerenciadas as classes em FIPS modo lança um <xref:System.Security.Cryptography.CryptographicException> (`true`) ou se baseia na implementação de bibliotecas do sistema (`false`).|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Determina se o padrão para algumas operações do SignedCMS é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Controles se o <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> método trata corretamente as curvas todas nomeadas com suporte pelo sistema operacional (`false`) ou reverte para o comportamento herdado.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Determina se o padrão para algumas operações SignedXML é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Determina se o `TransportWithMessageCredential` modo de segurança permite que as mensagens com um unsigned "cabeçalho para". Isso é uma opção de aceitação. Para obter mais informações, consulte [alterações de tempo de execução no .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Controles se o <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> construtor lança um <xref:System.ArgumentException> se um dos elementos é `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Determina que se a tentativa de usar X509 certificados com um provedor de armazenamento de chaves CSG gera uma exceção. Para obter mais informações, consulte [segurança do transporte WCF dá suporte a certificados armazenados usando CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Ao usar o transporte HTTP com um serviço auto-hospedado, definir esse valor como `true` faz com que o WCF ignorar a um aplicativo adicionando o `Connection: close` cabeçalho para os cabeçalhos de resposta para uma solicitação. Definir esse valor como `false` permite adicionar o `Connection: close` cabeçalho para os cabeçalhos de resposta, o que resulta no fechamento de soquete de solicitação depois que uma resposta foi enviada.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Lida com deadlocks que resultam de restrição de instâncias de um serviço reentrante a um único thread de execução em um horário.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Juntamente com `Switch.System.Net.DontEnableSchUseStrongCrypto`, determina se a segurança de mensagem do WCF usa TLS 1.1 e TLS 1.2.|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Um valor de `false` define a configuração padrão para permitir que o sistema operacional escolha o protocolo. Um valor de `true` define o padrão para o maior protocolo disponível. (Também disponível no branch de versões anteriores do framework de manutenção)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Determina se a mensagem padrão do algoritmo para mensagens MSMQ do WCF de assinatura é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Controla se WCF usa um SHA1 ou hash SHA256 para gerar nomes aleatórios para pipes nomeados.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Controla se deve lançar uma [NullReferenceException](xref:System.NullReferenceException) quando a mensagem de exceção é nula.|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Controla se as exceções geradas na inicialização do serviço são propagadas para o chamador do <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> método.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Controles se <xref:System.Threading.Timer> instâncias tirar proveito dos aprimoramentos de desempenho para ambientes de grande escala. Se `true`, as melhorias de desempenho estão habilitadas; se `false` (o valor padrão), eles são desabilitados.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Determina se determinados caracteres codificados por porcentagem que, às vezes, eram decodificados agora são codificados consistentemente à esquerda. Se `true`, eles são decodificados; caso contrário, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Determina a manipulação de caracteres de bidirecionais Unicode em URIs. `true` para removê-los dos URIs; `false` preservar e porcentagem-codificá-los.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Determina se o Windows Presentation Foundation se aplica um algoritmo antigo (`true`) ou um novo algoritmo (`false`) na alocação de espaço para \*-colunas. Para obter mais informações, confira [Mitigação: Alocação de espaço do controle de grade para colunas de estrela](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Se um seletor ou uma guia de controle sempre atualiza o valor de sua propriedade de valor selecionado antes de acionar a seleção de controles de evento de alteração.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Determina se a renderização de não-adorno de seleção com base está disponível para o <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.PasswordBox> controles para impedir que o texto obstruído (`false`), ou se o texto é renderizado apenas na camada de adorno (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Controla se os indexadores de IList personalizados são usados incorretamente (`false`) ou corretamente (`true`), o <xref:System.Windows.Data.Binding?displayProperty=nameWithType> classe.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Determina se as alterações DPI ocorrerem em por sistema (um valor de `false`) ou com base em monitor (um valor de `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Controles se melhorias no dimensionamento dos controles em uma <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> quando o WPF é executado no modo de reconhecimento por monitor estão desabilitadas (`true`) ou habilitado (`false`).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Determina se o desenvolvedor precisa manipular especialmente o <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ação quando o texto do controle está presente. `true` para lidar com o <xref:System.Windows.Forms.DomainUpDown.UpButton> ação; `false` para o <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> e <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ações a serem corretamente em sincronia.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Opte por não usar o código que permite que um personalizado <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementação para filtrar mensagens com segurança sem gerar uma exceção quando o <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> método é chamado. Para obter mais informações, confira [Mitigação: Implementações personalizadas de IMessageFilter. PreFilterMessage](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Determina se o <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriedade retorna o controle do código-fonte quando o usuário abre o menu de aninhado <xref:System.Windows.Forms.ToolStripMenuItem> controle. `true` para retornar `null`, o comportamento herdado; `false` para retornar o controle do código-fonte.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Controla se o suporte de invocação de dica de ferramenta está desabilitado (`true`) ou habilitado (`false`). Habilitando o suporte de invocação de dica de ferramenta também requer recursos de acessibilidade herdados definidos pela `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, e `Switch.UseLegacyAccessibilityFeatures.3` todas ser desabilitada (definida como `false`).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Determina se um recurso opcional `WM_POINTER`-pilha de toque/caneta com base está habilitado em aplicativos WPF. Para obter mais informações, confira [Mitigação: Com base em ponteiro suporte a toque e caneta](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Determina se o algoritmo de hash padrão usado para as somas de verificação é SHA256 (`false`) ou SHA1 (`true`).<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Controla se um herdado [NullReferenceException](xref:System.NullReferenceException) será lançada em vez da exceção que indica mais especificamente a causa da exceção (como um [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) ou uma [ FileNotFoundException](xref:System.IO.FileNotFoundException). Ele destina para uso pelo código que dependa da identificação de [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Os controles se compilações de soma de verificação de hash dos arquivos XOML no projeto de fluxo de trabalho usam o algoritmo MD5 (`true`), ou se usar o algoritmo SHA256 introduzido como padrão no .NET Framework 4.8.<br>Devido a problemas de colisão com MD5, a Microsoft recomenda SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Controla se a soma de verificação de hash pelo SqlTrackingService usa o algoritmo MD5 (`true`) para cadeias de caracteres armazenados em cache, ou se ele usa o algoritmo SHA256 introduzido como padrão no .NET Framework 4.8.<br>Devido a problemas de colisão com MD5, a Microsoft recomenda SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Controla se a soma de verificação de hash e o tempo de execução do fluxo de trabalho usa o algoritmo MD5 (`true`) para obter definições de fluxo de trabalho em cache, ou se ele usa o algoritmo SHA256 introduzido como padrão no .NET Framework 4.8.<br>Devido a problemas de colisão com MD5, a Microsoft recomenda SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Controla se os recursos de acessibilidade disponíveis a partir do .NET Framework 4.7.1 é habilitada ou desabilitada. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Os controles se recursos disponíveis no .NET Framework 4.7.2 de acessibilidade são habilitadas (`false`) ou desabilitado (`true`). Se `true`, `Switch.UseLegacyAccessibilityFeatures` também deve ser `true` para habilitar os recursos de acessibilidade do .NET Framework 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Os controles se os recursos de acessibilidade introduzido no .NET Framework 4.8 estão habilitados (`false`) ou desabilitado (`true`). Se `true`, `Switch.UseLegacyAccessibilityFeatures` e `Switch.UseLegacyAccessibilityFeatures.2` também deve ser `true`.|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Controles se as dicas de ferramenta são exibidas quando um usuário passa o cursor do mouse sobre um controle WPF (`true`), ou se eles são exibidos em foco do teclado e por meio da tecla de atalho de teclado (`false`, o comportamento padrão). Para aplicativos em execução no .NET Framework 4.8 mas destinados a versões anteriores do .NET Framework, permitindo que ambos o foco de teclado e suporte a chaves atalho requer que `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, e `Switch.UseLegacyAccessibilityFeatures.3` todas definidas para `false`.|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Controla se as sequências de chaves vazias em chaves compostas são ignoradas pela validação de esquema XSD. Para obter mais informações, confira [Mitigação: Validação de esquema XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Em vez de adicionar um `AppContextSwitchOverrides` elemento para um arquivo de configuração de aplicativo, você também pode definir as opções programaticamente, chamando o `static` (em c#) ou `Shared` (no Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.  
  
 Os desenvolvedores de biblioteca também podem definir opções personalizadas para permitir que os chamadores recusar alterada funcionalidade introduzida em versões posteriores de suas bibliotecas. Para obter mais informações, consulte a classe <xref:System.AppContext>.  
  
## <a name="switches-in-aspnet-applications"></a>Comutadores nos aplicativos ASP.NET

Você pode configurar um aplicativo ASP.NET para usar configurações de compatibilidade com a adição de um [ \<Adicionar >](../../../configure-apps/file-schema/appsettings/add-element-for-appsettings.md) elemento para o [ \<appSettings >](../../../configure-apps/file-schema/appsettings/index.md) seção do arquivo Web. config. 

O exemplo a seguir usa o `<add>` elemento para adicionar duas configurações para o `<appSettings>` seção de um arquivo Web. config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Exemplo

 O exemplo a seguir usa o `AppContextSwitchOverrides` elemento para definir uma opção de compatibilidade de aplicativo único, `Switch.System.Globalization.NoAsyncCurrentCulture`, que impede a cultura que fluem entre threads em chamadas de método assíncrono.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 O exemplo a seguir usa o `AppContextSwitchOverrides` elemento para definir duas opções de compatibilidade de aplicativo, `Switch.System.Globalization.NoAsyncCurrentCulture` e `Switch.System.IO.BlockLongPaths`. Observe que um ponto e vírgula separa os dois pares de nome/valor.  
  
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
- [\<tempo de execução > elemento](runtime-element.md)
- [Elemento \<configuration>](../configuration-element.md)
