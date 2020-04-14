---
title: Elemento AppContextSwitchOverrides
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 95ae438e9fb52cc584d18a981bffb66147eb4a77
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242810"
---
# <a name="appcontextswitchoverrides-element"></a>\<O elemento> AppContextSwitchOverrides

Define uma ou mais opções usadas pela classe <xref:System.AppContext> para fornecer um mecanismo de recusa de uma nova funcionalidade.

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<AppContextSwitchOverrides>**

## <a name="syntax"></a>Sintaxe

```xml
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`value`|Atributo obrigatório.<br /><br /> Define um ou mais nomes de switch e seus valores booleanos associados.|

### <a name="value-attribute"></a>Atributo de valor

|Valor|Descrição|
|-----------|-----------------|
|"nome=valor"|Um nome de switch predefinido`true` `false`junto com seu valor (ou ). Vários pares de nomes/valor de switch são separados por ponto e vírgula (";"). Para obter uma lista de nomes de switch predefinidos suportados pelo Quadro .NET, consulte a seção Observações.|

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre opções de inicialização do runtime.|

## <a name="remarks"></a>Comentários
 Começando com o .NET Framework `<AppContextSwitchOverrides>` 4.6, o elemento em um arquivo de configuração permite que os chamadores de uma API determinem se seu aplicativo pode tirar proveito da nova funcionalidade ou preservar a compatibilidade com versões anteriores de uma biblioteca. Por exemplo, se o comportamento de uma API foi `<AppContextSwitchOverrides>` alterado entre duas versões de uma biblioteca, o elemento permite que os chamadores dessa API optem por sair do novo comportamento nas versões da biblioteca que suportam a nova funcionalidade. Para aplicativos que chamam APIs no `<AppContextSwitchOverrides>` .NET Framework, o elemento também pode permitir que os chamadores cujos aplicativos segmentem uma versão anterior do .NET Framework optem por novas funcionalidades se seu aplicativo estiver sendo executado em uma versão do .NET Framework que inclua essa funcionalidade.

 O `value` atributo `<AppContextSwitchOverrides>` do elemento consiste em uma única seqüência que consiste de um ou mais pares de nome/valor delimitados em ponto e vírgula.  Cada nome identifica um switch de compatibilidade, e seu`true` `false`valor correspondente é um Boolean ( ou ) que indica se o switch está definido. Por padrão, o `false`switch é , e bibliotecas fornecem a nova funcionalidade. Eles só fornecem a funcionalidade anterior se o switch estiver `true`definido (ou seja, seu valor é ). Isso permite que as bibliotecas forneçam um novo comportamento para uma API existente, permitindo que os chamadores que dependem do comportamento anterior optem pela nova funcionalidade.

 O Quadro .NET suporta os seguintes switches:

|Nome do switch|Descrição|Introduzido|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Controla se o Windows Presentation Foundation usa um algoritmo legado para layout de controle. Para saber mais, confira [Mitigação: layout de WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Controla se o algoritmo padrão usado para assinar partes de um pacote pelo PackageDigitalSignatureManager é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Quando definido `false`para , permite a depuração de projetos de fluxo de trabalho baseados em XAML com o Visual Studio quando o FIPS está ativado. Sem ele, é lançado um <xref:System.NullReferenceException> a chamadas para métodos na montagem do Sistema.Atividades.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Controla se o resumo de verificação de uma instância de fluxo de trabalho no depurador usa MD5 ou SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Controla se o hashing de verificação de fluxo de trabalho usa o`true`algoritmo SHA1 introduzido como padrão no .NET Framework 4.7 (`false`), ou se ele usa o algoritmo SHA256 padrão introduzido como padrão no .NET Framework 4.8 ( ).<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Controla se os rastreamentos de pilha saem ao usar PDBs portáteis podem incluir informações de arquivo de origem e linha. `false`incluir informações de arquivo de origem e linha; caso contrário, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Controla se <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> o método lança <xref:System.Drawing.Icon> uma exceção quando um objeto tem quadros PNG. Para saber mais, confira [Mitigation: PNG Frames in Icon Objects](../../../migration-guide/mitigation-png-frames-in-icon-objects.md) (Mitigação: quadros PNG em objetos de ícone).|.NET framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Determina se <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> os objetos são descartados corretamente quando adicionados à coleta pelo <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> método. `true`para manter o comportamento legado; `false` para descartar todos os objetos de fonte privadas. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Controla se o <xref:System.Windows.Forms.PrintPreviewDialog> desempenho do é otimizado para impressoras de rede. Para obter mais informações, consulte [PrintPreviewExibi visão geral do controle](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Controla se as verificações de faixa de ano para as eras do calendário japonês são aplicadas. `true`para impor verificações `false` de intervalo de ano e desativá-las (o comportamento padrão). Para obter mais informações, consulte [Trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Controla se apenas "1" é reconhecido como o primeiro ano de uma era de calendário japonês em operações de análise. `true`reconhecer apenas "1"; `false` para reconhecer "1" ou Gannen (o comportamento padrão). Para obter mais informações, consulte [Trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Controla se o primeiro ano de uma era de calendário japonês é representado como "1" ou Gannen em operações de formatação. `true`para formatar o primeiro ano da era como "1"; `false` formatá-lo como Gannen (o comportamento padrão). Para obter mais informações, consulte [Trabalhando com calendários](../../../../standard/datetime/working-with-calendars.md).|.NET framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Controla se as operações assíncronas não fluem do contexto do segmento de chamada. Para obter mais informações, consulte [CurrentCulture e CurrentUICulture fluem em tarefas](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Controla se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> o método tenta corresponder ao tipo de solicitação apenas com a última entrada de DNS. Para saber mais, confira [Mitigation: X509CertificateClaimSet.FindClaims Method](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md) (Mitigação: método X509CertificateClaimSet.FindClaims).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Controla se permite que o AuthorizationContext.Empty retorne um objeto mutável.|.NET framework 4.6|
|`Switch.System.IO.BlockLongPaths`|Controla se caminhos mais longos `MAX_PATH` que <xref:System.IO.PathTooLongException>(260 caracteres) lançam um . Para obter mais informações, consulte [Suporte ao Caminho Longo](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Controla se as rotinas nativas do <xref:System.IO.Compression.DeflateStream> sistema operacional são usadas para descompressão pela classe. `false`para usar APIs nativas; `true` para usar <xref:System.IO.Compression.DeflateStream> a implementação.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Usa a barra\\invertida (" ") em vez da barra para <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> a frente ("/") como separador de caminho na propriedade. Para obter mais informações, consulte [Mitigação: ZipArchiveEntry.FullName Path Separator](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Controla se as exceções do sistema operacional que <xref:System.IO.Ports.SerialPort> são lançadas em segmentos de fundo criados com fluxos encerram o processo.|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Controla se a normalização do caminho legado é <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> usada e os caminhos URI são suportados pelos métodos. Para obter mais informações, consulte [Mitigação: Normalização](../../../migration-guide/mitigation-path-normalization.md) e [Mitigação do Caminho: Verificações de verificação de cólon de caminho](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Controla se um teste de <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> igualdade compara a <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> propriedade de um objeto com a propriedade do segundo objeto. Para obter mais informações, consulte [Implementação incorreta do MemberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Desabilita a validação do identificador de objeto (EKU) de uso de chave aprimorada do certificado (EKU). Uma extensão de EKU (uso avançado de chave) é uma coleção de OIDs (identificadores de objeto) que indicam os aplicativos que usam a chave.|.NET framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Desabilita a exploração do navegador TLS1.0 contra a mitigação de SSL/TLS (BEAST) desativando o uso de SCH_SEND_AUX_RECORD.|.NET framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Controla se <xref:System.Net.ServicePointManager?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> as classes e as classes podem usar o protocolo SSL 3.0. Para saber mais, confira [Mitigation: TLS Protocols](../../../migration-guide/mitigation-tls-protocols.md) (Mitigação: protocolos TLS).|.NET framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Desabilita as versões TLS do SystemDefault voltando a um padrão de Tls12, Tls11, Tls.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Desabilita alertas do lado do servidor SslStream TLS.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Controla se os parâmetros do ByRef SafeArray no`false`com interop eventos marshal de`true`volta ao código nativo ( ) ou se o marshaling de volta ao código nativo está desativado ().|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Controla se o [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializa alguns caracteres de controle com base nos padrões ECMAScript V6 e V8. Para obter mais informações, consulte [Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Controla se <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> o suporte a vários ajustes ou apenas um único ajuste para um fuso horário. Se `true`, ele <xref:System.TimeZoneInfo> usa o tipo para serializar e desserializar dados de data e hora; caso contrário, ele <xref:System.TimeZone> usa o tipo, que não suporta múltiplas regras de ajuste.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Controla <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> se usa um tamanho de matriz maior durante a serialização e desserialização do objeto. Defina este `true` switch para melhorar o desempenho da serialização e desserialização de gráficos de objetos grandes por tipos como <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Controla se <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29> o construtor define a <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> propriedade do novo objeto com uma referência de objeto existente. Para saber mais, confira [Mitigation: ClaimsIdentity Constructor](../../../migration-guide/retargeting/4.6.1-4.6.2.md) (Mitigação: construtor ClaimsIdentity).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Controla se a tentativa <xref:System.Security.Cryptography.AesCryptoServiceProvider> de reutilização <xref:System.Security.Cryptography.CryptographicException>de um decodificador lança um . Para obter mais informações, consulte [O descriptografador AesCryptoServiceProvider fornece uma transformação reutilizável](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Controla se o valor da propriedade [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) é um [IntPtr](xref:System.IntPtr) que representa o local de memória de uma alça de janela ou se é uma alça de janela (um HWND). Para obter mais informações, consulte [Mitigação: CspParameters.ParentWindowHandle espera um HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Controla se o uso de classes de criptografia <xref:System.Security.Cryptography.CryptographicException> gerenciadas no modo FIPS lança um (`true`) ou depende da implementação de bibliotecas de sistemas (`false`).|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Determina se o padrão para algumas operações de CMS assinados é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Controla se <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> o método lida corretamente com todas as`false`curvas nomeadas suportadas pelo sistema operacional ( ) ou reverte para o comportamento legado.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Determina se o padrão para algumas operações SignedXML é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Determina se `TransportWithMessageCredential` o modo de segurança permite mensagens com um cabeçalho "to" não assinado. Este é um interruptor de opt-in. Para obter mais informações, consulte ['Alterações de tempo de execução' no quadro .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Controla se <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> o construtor <xref:System.ArgumentException> lança um se `null`um dos elementos é .|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Determina se a tentativa de usar certificados X509 com um provedor de armazenamento chave CSG abre uma exceção. Para obter mais informações, consulte [os certificados de segurança de transporte WCF armazenados usando GNV](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Ao usar o transporte HTTP com um serviço auto-hospedado, definir esse valor faz com que o `true` WCF ignore um aplicativo adicionando o `Connection: close` cabeçalho aos cabeçalhos de resposta para uma solicitação. Definir esse `false` valor para `Connection: close` permitir a adição do cabeçalho aos cabeçalhos de resposta, o que resulta no fechamento do soquete de solicitação após o enviado de uma resposta.|.NET framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Lida com impasses que resultam da restrição de instâncias de um serviço de reentrante a um único segmento de execução por vez.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Junto `Switch.System.Net.DontEnableSchUseStrongCrypto`com , determina se a segurança de mensagem WCF usa TLS 1.1 e TLS 1.2.|.NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Um valor `false` de define a configuração padrão para permitir que o sistema operacional escolha o protocolo. Um valor `true` de define o padrão para o protocolo mais alto disponível. (Também disponível no ramo de manutenção de versões estruturas anteriores)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Determina se o algoritmo padrão de assinatura de mensagens para mensagens MSMQ no WCF é SHA1 ou SHA256.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Controla se o WCF usa um hash SHA1 ou SHA256 para gerar nomes aleatórios para tubos nomeados.<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Controla se deve lançar uma [NullReferenceException](xref:System.NullReferenceException) quando a mensagem de exceção for nula.|.NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Controla se as exceções lançadas na inicialização <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> do serviço são propagadas para o chamador do método.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Controla <xref:System.Threading.Timer> se as instâncias tiram proveito de melhorias de desempenho para ambientes de alta escala. Se `true`, as melhorias de desempenho estão habilitadas; se `false` (o valor padrão), eles estiverem desativados.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Determina se certos caracteres codificados por cento que às vezes foram decodificados são agora consistentemente deixados codificados. Se, `true`eles são decodificados; caso contrário, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Determina o manuseio de caracteres bidirecionais Unicode em URIs. `true`para retirá-los de URIs; `false` para preservá-los e codifica-los por cento.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Determina se o Windows Presentation Foundation`true`aplica um algoritmo`false`antigo ( ) ou \*um novo algoritmo ( ) na alocação de espaço para colunas. Para obter mais informações, consulte [Mitigação: alocação de espaço do controle de grade para colunas de estrela](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Controla se um seletor ou um controle de guia sempre atualiza o valor de sua propriedade de valor selecionada antes de elevar o evento alterado de seleção.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Determina se a renderização de seleção <xref:System.Windows.Controls.TextBox> não <xref:System.Windows.Controls.PasswordBox> baseada em Adorner está`false`disponível para os controles para evitar o`true`texto ocluído ( ), ou se o texto é renderizado apenas na camada Adorner ( ).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Controla se os indexadores IList`true`personalizados são`false`usados <xref:System.Windows.Data.Binding?displayProperty=nameWithType> incorretamente ( ) ou corretamente ( ) pela classe.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Determina se as alterações de DPI ocorrem `false`em uma base por sistema `true`(um valor de ) ou por monitor (um valor de ).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Controla se as melhorias no <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> dimensionamento de controles em um modo de`true`controle por`false`monitor são desativadas ( ) ou ativadas ( ).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Determina se o desenvolvedor precisa lidar <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> especialmente com a ação quando o texto de controle estiver presente. `true`para lidar <xref:System.Windows.Forms.DomainUpDown.UpButton> com a ação; `false` para <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> que <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> as ações e ações estejam adequadamente em sincronia.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Opta pelo código que permite <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uma implementação personalizada para filtrar <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> mensagens com segurança sem abrir uma exceção quando o método é chamado. Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Determina se <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> a propriedade retorna o controle de origem quando <xref:System.Windows.Forms.ToolStripMenuItem> o usuário abre o menu a partir de um controle aninhado. `true`para `null`retornar , o comportamento legado; `false` para retornar o controle de origem.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Controla se o suporte à`true`invocação de`false`dicas de ferramentas está desativado () ou habilitado ( ). A ativação do suporte à invocação de `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`dicas `Switch.UseLegacyAccessibilityFeatures.3` de ferramentas também `false`requer recursos de acessibilidade legados definidos por , e todos serão desativados (definidos para ).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Determina se uma `WM_POINTER`pilha de toque/caneta opcional está habilitada em aplicativos WPF. Para obter mais informações, consulte [Mitigação: Suporte ao toque e caneta baseado em ponteiro](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Determina se o algoritmo hash padrão usado para somas de verificação é SHA256 (`false`) ou SHA1 ( ).`true`<br>Em razão de problemas de colisão com SHA1, a Microsoft recomenda SHA256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Controla se um legado [NullReferenceException](xref:System.NullReferenceException) é lançado em vez da exceção que mais especificamente indica a causa da exceção (como um [DiretórioNotFoundException](xref:System.IO.DirectoryNotFoundException) ou um [FileNotFoundException](xref:System.IO.FileNotFoundException). Destina-se a ser usado por código que depende do manuseio da [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Controla se o hashing de checksum de arquivos XOML em`true`projetos de fluxo de trabalho cria o algoritmo MD5 ( ), ou se eles usam o algoritmo SHA256 introduzido como padrão no .NET Framework 4.8.<br>Devido a problemas de colisão com o MD5, a Microsoft recomenda o SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Controla se o hashdes de checksum pelo SqlTrackingService usa o algoritmo MD5 (`true`) para strings armazenadas em cache, ou se ele usa o algoritmo SHA256 introduzido como padrão no .NET Framework 4.8.<br>Devido a problemas de colisão com o MD5, a Microsoft recomenda o SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Controla se o hashing de checksum pelo Workflow`true`Runtime usa o algoritmo MD5 ( ) para definições de fluxo de trabalho em cache, ou se ele usa o algoritmo SHA256 introduzido como padrão no .NET Framework 4.8.<br>Devido a problemas de colisão com o MD5, a Microsoft recomenda o SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Controla se os recursos de acessibilidade disponíveis a partir do .NET Framework 4.7.1 estão ativados ou desativados. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Controla se os recursos de acessibilidade disponíveis no .NET`false`Framework 4.7.2 estão habilitados ( ) ou desativados (`true`). `true`Se, `Switch.UseLegacyAccessibilityFeatures` também `true` deve ser para habilitar recursos de acessibilidade .NET Framework 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Controla se os recursos de acessibilidade introduzidos no`false`.NET Framework`true`4.8 estão habilitados ( ) ou desativados ( ). Se `true` `Switch.UseLegacyAccessibilityFeatures` , `Switch.UseLegacyAccessibilityFeatures.2` e `true`também deve ser .|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Controla se as dicas de ferramentas são exibidas quando um usuário`true`sobreria o cursor do mouse sobre um controle`false`WPF ( ), ou se elas são exibidas tanto no foco do teclado quanto através da tecla de atalho do teclado (, o comportamento padrão). Para aplicativos em execução no .NET Framework 4.8, mas visando versões anteriores do `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2`.NET `Switch.UseLegacyAccessibilityFeatures.3` Framework, `false`habilitar o foco do teclado e o suporte à tecla de atalho requer que , e todos sejam definidos para .|.NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Controla se as seqüências de teclas vazias em teclas compostas são ignoradas pela validação do esquema XSD. Para obter mais informações, consulte [Mitigação: Validação de esquema XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET framework 4.6|

> [!NOTE]
> Em vez `AppContextSwitchOverrides` de adicionar um elemento a um arquivo de configuração de `static` aplicativo, você `Shared` também pode definir <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> os switches programáticamente chamando o método (em C#) ou (no Visual Basic).

 Os desenvolvedores de bibliotecas também podem definir switches personalizados para permitir que os chamadores optem por desativar a funcionalidade alterada introduzida em versões posteriores de suas bibliotecas. Para obter mais informações, consulte a classe <xref:System.AppContext>.

## <a name="switches-in-aspnet-applications"></a>Switches em aplicativos ASP.NET

Você pode configurar um aplicativo ASP.NET para usar configurações de compatibilidade [ \<adicionando](../appsettings/add-element-for-appsettings.md) um elemento Add>à [ \<](../appsettings/index.md) seção Configurações>do arquivo Web.config.

O exemplo a `<add>` seguir usa o elemento `<appSettings>` para adicionar duas configurações à seção de um arquivo Web.config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Exemplo

 O exemplo a `AppContextSwitchOverrides` seguir usa o elemento para `Switch.System.Globalization.NoAsyncCurrentCulture`definir um único switch de compatibilidade de aplicativo, que impede que a cultura flua através de threads em chamadas de método assíncronas.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 O exemplo a `AppContextSwitchOverrides` seguir usa o elemento para `Switch.System.Globalization.NoAsyncCurrentCulture` `Switch.System.IO.BlockLongPaths`definir dois switches de compatibilidade de aplicativos e . Um ponto e vírgula separa os dois pares de nome/valor.

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>Confira também

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<elemento> em tempo de execução](runtime-element.md)
- [\<elemento> de configuração](../configuration-element.md)
