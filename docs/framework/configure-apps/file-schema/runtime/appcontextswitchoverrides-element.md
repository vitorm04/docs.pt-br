---
title: '&lt;AppContextSwitchOverrides&gt; elemento'
ms.custom: 
ms.date: 10/17/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d0c87092786e1057bb925f55cfe46e3f4ef58b9d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; elemento
Define uma ou mais opções usadas pela classe <xref:System.AppContext> para fornecer um mecanismo de recusa de uma nova funcionalidade.  
  
 \<configuration>  
 \<tempo de execução >  
\<AppContextSwitchOverrides >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`value`|Atributo obrigatório.<br /><br /> Define um ou mais nomes de chave e seus valores associados de boolianos.|  
  
### <a name="value-attribute"></a>valor de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|"nome = valor"|Um nome de comutador predefinidos juntamente com seu valor (`true` ou `false`). Vários pares de nome/valor de opção são separados por ponto e vírgula (";"). Para obter uma lista de nomes predefinidos de comutador com suporte do .NET Framework, consulte a seção comentários.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 4.6, o `<AppContextSwitchOverrides>` elemento em um arquivo de configuração permite que os chamadores de uma API para determinar se o seu aplicativo pode tirar proveito da nova funcionalidade ou preservar a compatibilidade com versões anteriores de uma biblioteca. Por exemplo, se o comportamento de uma API foi alterado entre duas versões de uma biblioteca, o `<AppContextSwitchOverrides>` elemento permite que os chamadores dessa API para recusar o novo comportamento em versões da biblioteca que oferece suporte à nova funcionalidade. Para aplicativos que chamam as APIs do .NET Framework, o `<AppContextSwitchOverrides>` elemento também pode permitir que os chamadores cujos aplicativos direcionam uma versão anterior do .NET Framework para aceitar novas funcionalidades se seu aplicativo estiver sendo executado em uma versão do .NET Framework que inclui que funcionalidade.  
  
 O `value` atributo o `<AppContextSwitchOverrides>` elemento consiste em uma única cadeia de caracteres que consiste em um ou mais pares de nome/valor separados por ponto-e-vírgula.  Cada nome identifica uma opção de compatibilidade e seu valor correspondente é um valor booliano (`true` ou `false`) que indica se a opção é definida. Por padrão, a opção é `false`, e bibliotecas fornecem a funcionalidade de novo. Eles fornecem a funcionalidade anterior somente se a opção for definida (ou seja, seu valor é `true`). Isso permite que as bibliotecas fornecer o novo comportamento de uma API existente enquanto permite que os chamadores que dependem do comportamento anterior para recusar a nova funcionalidade.  
  
 O .NET Framework suporta as seguintes opções:  
  
|Nome do comutador|Descrição|Introduzido|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Controla se o Windows Presentation Foundation usa herdado um algoritmo para controlar o layout. Para saber mais, confira [Mitigação: layout de WPF](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Quando definido como `false`, permite a depuração de projetos de fluxo de trabalho baseado em XAML com o Visual Studio quando FIPS está habilitado. Sem ele, um <xref:System.NullReferenceException> é gerada em chamadas para métodos no assembly System. Activities.|.NET Framework 4.7|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Controla se o <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> método lançará uma exceção quando um <xref:System.Drawing.Icon> objeto tem quadros PNG. Para saber mais, confira [Mitigation: PNG Frames in Icon Objects](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md) (Mitigação: quadros PNG em objetos de ícone).|.NET Framework 4.6|  
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Controla se as operações assíncronas não fluxo do contexto do thread de chamada. Para obter mais informações, consulte [CurrentCulture e CurrentUICulture fluam entre tarefas](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Controla se o <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> método tenta corresponder o tipo de declaração apenas com a última entrada DNS. Para saber mais, confira [Mitigation: X509CertificateClaimSet.FindClaims Method](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md) (Mitigação: método X509CertificateClaimSet.FindClaims).|.NET Framework 4.6.1|  
|`Switch.System.IO.BlockLongPaths`|Controla se caminhos com mais de `MAX_PATH` (260 caracteres) lançar um <xref:System.IO.PathTooLongException>. Para obter mais informações, consulte [suporte de caminho longo](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Usa a barra invertida ("\\") em vez de barra invertida ("/") como separador de caminho no <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriedade. Para obter mais informações, consulte [atenuação: o separador de caminho ZipArchiveEntry.FullName](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Controla se caminho herdados normalização é usada e caminhos URI são compatíveis com o <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> métodos. Para obter mais informações, consulte [atenuação: caminho normalização](~/docs/framework/migration-guide/mitigation-path-normalization.md) e [atenuação: caminho vírgula verifica](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Controla se um teste de igualdade compara o <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> propriedade de um objeto com o <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> propriedade do segundo objeto. Para obter mais informações, consulte [implementação incorreta de MemberDescriptor.Equals](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Desabilita a validação de OID (identificador) do objeto de uso avançado de chave (EKU) de certificado. Uma extensão de uso avançado de chave (EKU) é uma coleção de identificadores de objeto (OIDs) que indicam que os aplicativos que usam a chave.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Desabilita a mitigação de TLS 1.0 por navegador explorar em SSL/TLS (FERA) desabilitando o uso de SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Controla se o <xref:System.Net.ServicePointManager?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes podem usar o protocolo SSL 3.0. Para saber mais, confira [Mitigation: TLS Protocols](~/docs/framework/migration-guide/mitigation-tls-protocols.md) (Mitigação: protocolos TLS).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Desabilita versões SystemDefault TLS reverter para um padrão de Tls12, Tls11, Tls.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Desabilita os alertas do SslStream TLS do lado do servidor.|.NET Framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Controla se o [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializa alguns caracteres de controle com base nos padrões do ECMAScript V6 e V8. Para obter mais informações, consulte [Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET Framework 4.7 |
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Controla se o <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> construtor define o novo objeto <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> propriedade com uma referência de objeto existente. Para saber mais, confira [Mitigation: ClaimsIdentity Constructor](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md) (Mitigação: construtor ClaimsIdentity).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Controla se a tentativa de reutilizar um <xref:System.Security.Cryptography.AesCryptoServiceProvider> descriptografador gera um <xref:System.Security.Cryptography.CryptographicException>. Para obter mais informações, consulte AesCryptoServiceProvider descriptografador fornece um transform](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform) reutilizável.|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Controla se o valor da [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) propriedade é um [IntPtr](xref:System.IntPtr) que representa o local de memória de uma janela de manipular ou se é um identificador de janela (HWND). Para obter mais informações, consulte [Mitigação: CspParameters.ParentWindowHandle espera um HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |.NET Framework 4.7|   
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Determina se o `TransportWithMessageCredential` modo de segurança permite que as mensagens com um sem sinal "para" cabeçalho. Isso é uma opção de aceitação. Para obter mais informações, consulte [alterações de tempo de execução do .NET Framework 4.6.1](https://msdn.microsoft.com/library/mt592686.aspx#WCF).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Determina que se a tentativa de usar o X509 certificados com um provedor de armazenamento de chaves CSG lança uma exceção. Para obter mais informações, consulte [segurança de transporte WCF dá suporte a certificados armazenados usando o CNG](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Juntamente com `Switch.System.Net.DontEnableSchUseStrongCrypto`, determina se a segurança de mensagens do WCF usa TLS 1.1 e TLS 1.2.|.NET Framework 4.7 |    
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Determina se o Windows Presentation Foundation se aplica um algoritmo antigo (`true`) ou um novo algoritmo (`false`) ao alocar espaço para \*-colunas. Para obter mais informações, consulte [Mitigação: alocação de espaço do controle de grade para colunas de estrela](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |.NET Framework 4.7 |
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Significa recusar o código que permite que um personalizado <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementação com segurança filtrar mensagens sem gerar uma exceção quando o <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> método é chamado. Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Determina se um recurso opcional `WM_POINTER`-pilha de toque com base/caneta está habilitado em aplicativos WPF. Para obter mais informações, consulte [atenuação: baseada em ponteiro de toque e suporte de caneta](Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md) | 
|`Switch.System.Windows.Media.ImageSourceConverter`<br/>`OverrideExceptionWithNullReferenceException`|Controla se um herdado [NullReferenceException](xref:System.NullReferenceException) é gerada em vez da exceção que indica mais especificamente a causa da exceção (como uma [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) ou um [ FileNotFoundException](xref:System.IO.FileNotFoundException). Ele é destinado ao uso pelo código que depende de tratamento de [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Controla se as sequências de chave vazias em chaves compostas são ignoradas pela validação de esquema XSD. Para obter mais informações, consulte [mitigação: validação de esquema XML](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Em vez de adicionar um `AppContextSwitchOverrides` elemento para um arquivo de configuração do aplicativo, você também pode definir as opções programaticamente chamando o `static` (em c#) ou `Shared` (no Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> método.  
  
 Os desenvolvedores de biblioteca também podem definir opções personalizadas para permitir que os chamadores recusar alterada funcionalidade introduzida em versões posteriores de suas bibliotecas. Para obter mais informações, consulte a classe <xref:System.AppContext>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `AppContextSwitchOverrides` elemento para definir uma opção de compatibilidade de aplicativo único, `Switch.System.Globalization.NoAsyncCurrentCulture`, que impede a cultura que fluem entre threads em chamadas de método assíncrono.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 O exemplo a seguir usa o `AppContextSwitchOverrides` elemento para definir dois comutadores de compatibilidade de aplicativo, `Switch.System.Globalization.NoAsyncCurrentCulture` e `Switch.System.IO.BlockLongPaths`. Observe que um ponto e vírgula separa os dois pares de nome/valor.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
<xref:System.AppContext>  
 [\<tempo de execução > elemento](runtime-element.md)  
 [Elemento \<configuration>](../configuration-element.md)
