---
title: "Práticas recomendadas do Transport Layer Security (TLS) com o .NET Framework"
description: "Descreve as práticas recomendadas usando a segurança de camada de transporte (TLS) com o .NET Framework"
ms.date: 03/15/2018
ms.prod: .net-framework
ms.topic: article
helpviewer_keywords:
- sending data, Internet security
- protocols, Internet security
- Network security
- network resources, Internet security
- receiving data, Internet security
- authentication [.NET Framework], Internet security
- Internet, security
- security [.NET Framework], Internet
- permissions [.NET Framework], Internet
author: blowdart
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64829eee5b21a44acb18cbec9b901d77d49cab90
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2018
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Práticas recomendadas do Transport Layer Security (TLS) com o .NET Framework

O protocolo de segurança de camada de transporte (TLS) é um padrão da indústria projetado para ajudar a proteger a privacidade das informações comunicadas pela Internet. [TLS 1.2](https://tools.ietf.org/html/rfc5246) é o padrão de lançamento mais recente e fornece melhorias de segurança em relação às versões anteriores. TLS 1.2 eventualmente será substituída por [1.3 TLS](https://tools.ietf.org/html/draft-ietf-tls-tls13-22). Este artigo apresenta recomendações para proteger os aplicativos do .NET Framework que usam o protocolo TLS.

Para garantir os aplicativos do .NET Framework permaneçam seguros, a versão do TLS deve **não** ser codificado. Aplicativos do .NET framework devem usar o sistema operacional (SO) oferece suporte a TLS versão.

Este documento tem como alvo os desenvolvedores que estão:

- Diretamente usando o <xref:System.Net> APIs (por exemplo, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Diretamente usando clientes WCF e serviços usando o <xref:System.ServiceModel?displayProperty=nameWithType> namespace.
- Usando [serviços de nuvem do Azure](https://azure.microsoft.com/services/cloud-services/) funções Web e de trabalho para hospedar e executar seu aplicativo. Consulte o [serviços de nuvem do Azure](#azure-cloud-services) seção.

Recomendamos que você:

- Destino do .NET Framework 4.7 ou versões mais recentes em seus aplicativos. .NET Framework de destino 4.7.1 ou versões mais recentes em seus aplicativos do WCF.
- Não especifique a versão do TLS. Configure seu código para permitir que o sistema operacional decidir sobre a versão TLS.
- Realizar uma auditoria de código completo para verificar se que você não estiver especificando uma versão TLS ou SSL.

Quando o seu aplicativo permite que o sistema operacional escolha a versão do TLS:

- Tira proveito dos novos protocolos adicionado no futuro, como TLS 1.3 automaticamente.
- O sistema operacional bloqueia os protocolos que são descobertos para não ser seguro.

A seção [auditar seu código e fazer alterações de código](#audit-your-code-and-make-code-changes) abrange a auditoria e atualizar seu código.

Este artigo explica como habilitar a segurança máxima disponível para a versão do .NET Framework que seu aplicativo tem como alvo e é executado no. Quando um aplicativo define explicitamente um protocolo de segurança e a versão, ele aceita fora de qualquer outra alternativa e significa recusar o comportamento padrão de sistema operacional e do .NET Framework. Se você quiser que seu aplicativo para poder negociar uma conexão TLS 1.2, definir explicitamente para uma versão inferior do TLS impede que uma conexão TLS 1.2.

Se você não pode evitar Fixar uma versão de protocolo, é altamente recomendável que você especifique o protocolo TLS 1.2. Para obter orientação sobre como identificar e remover dependências do TLS 1.0, baixe o [para solucionar o problema do TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266) white paper.

O WCF dá suporte a TLS 1.0 por, 1.1 e 1.2 como padrão no .NET Framework 4.7. Padrões WCF para o sistema operacional a partir do .NET Framework 4.7.1, configurado versão. Se um aplicativo é explicitamente configurado com `SslProtocols.None`, WCF usa a configuração do sistema operacional padrão ao usar o transporte NetTcp.

Você pode fazer perguntas sobre este documento em que o problema do GitHub [segurança de camada de transporte (TLS) práticas recomendadas com o .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Auditoria de seu código e fazer alterações de código

Para aplicativos ASP.NET, inspecione o `<system.web><httpRuntime targetFramework>` elemento _Web. config_ para verificar se você estiver usando a versão desejada do .NET Framework.

Para formulários do Windows e outros aplicativos, consulte [como: uma versão do .NET Framework de destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Use as seções a seguir para verificar se que você não estiver usando uma versão específica de TLS ou SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Se seu aplicativo tem como destino .NET Framework 4.7 ou versões posteriores

As seções a seguir mostram como verificar se você não estiver usando uma versão específica de TLS ou SSL.

### <a name="for-http-networking"></a>Rede de HTTP

<xref:System.Net.ServicePointManager>, usando o .NET Framework 4.7 e versões posteriores, o padrão será para o sistema operacional escolhendo o melhor protocolo de segurança e a versão. Para obter a melhor escolha do padrão sistema operacional, se possível, não defina um valor para o <xref:System.Net.ServicePointManager.SecurityProtocol> propriedade. Do contrário, defina-o como <xref:System.Net.SecurityProtocolType.SystemDefault>.

O restante deste artigo não é relevante durante o direcionamento do .NET Framework 4.7 ou versões posteriores de rede HTTP.

### <a name="for-tcp-sockets-networking"></a>Para soquetes TCP de rede

<xref:System.Net.Security.SslStream>, usando o .NET Framework 4.7 e versões posteriores, o padrão será para o sistema operacional escolhendo o melhor protocolo de segurança e a versão. Para obter a melhor escolha do padrão sistema operacional, se possível, não use as sobrecargas do método de <xref:System.Net.Security.SslStream> que levam um explícita <xref:System.Security.Authentication.SslProtocols> parâmetro. Caso contrário, passe <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. É recomendável que você não use <xref:System.Security.Authentication.SslProtocols.Default>; configuração `SslProtocols.Default` força o uso do SSL 3.0 /TLS 1.0 e impedir que o protocolo TLS 1.2.

Não defina um valor para o <xref:System.Net.ServicePointManager.SecurityProtocol> propriedade (para a conexão de rede HTTP).

Não use as sobrecargas de método de <xref:System.Net.Security.SslStream> que levam um explícita <xref:System.Security.Authentication.SslProtocols> parâmetro (para soquetes TCP de rede). Quando você redirecionar seu aplicativo para .NET Framework 4.7 ou versões posteriores, você vai seguindo a recomendação de práticas recomendada.

O restante deste tópico não é relevante quando direcionando o .NET Framework 4.7 ou versões posteriores para TCP soquetes de rede.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Transporte WCF TCP usando a segurança de transporte com as credenciais de certificado

Como o restante do .NET Framework, o WCF usa a mesma pilha de rede.

Se você estiver direcionando 4.7.1, WCF está configurado para permitir que o sistema operacional escolher o melhor protocolo de segurança por padrão, a menos que explicitamente configurado:

- Em seu arquivo de configuração do aplicativo.
- **Ou**, em seu aplicativo no código-fonte.

Por padrão, 4.7 do .NET Framework e versões posteriores está configurado para usar o TLS 1.2 e permite que conexões usando o TLS 1.1 ou TLS 1.0. Configurar WCF para permitir que o sistema operacional escolher o melhor protocolo de segurança ao configurar a associação para usar <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Isso pode ser definido em <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` pode ser acessado em <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` pode ser acessado em <xref:System.ServiceModel.NetTcpBinding.Security>.

Se você estiver usando uma associação personalizada:

- Configurar WCF para permitir que o sistema operacional escolher o melhor protocolo de segurança, definindo <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> usar <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Ou** configurar o protocolo usado com o caminho de configuração `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Se você estiver **não** utilizando uma associação personalizada **e** você está definindo sua associação WCF usando a configuração, defina o protocolo usado com o caminho de configuração `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Para segurança de mensagens do WCF com as credenciais de certificado

4.7 do .NET framework e versões posteriores por padrão usa o protocolo especificado no <xref:System.Net.ServicePointManager.SecurityProtocol> propriedade. Quando o [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` é definido como `true`, WCF escolhe o melhor protocolo até TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Se seu aplicativo tem como alvo uma versão do .NET Framework anterior à 4.7

Auditoria de seu código para verificar se que você não estiver instalando uma versão específica de TLS ou SSL usando as seções a seguir:

### <a name="for-net-framework-46---462-and-not-wfc"></a>Para o .NET Framework 4.6 - 4.6.2 e não WFC

Definir o `DontEnableSystemDefaultTlsVersions` `AppContext` alternar para `false`. Consulte [Configurando a segurança por meio de comutadores AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Para o WCF usando o .NET Framework 4.6 - 4.6.2 usando a segurança de transporte TCP com as credenciais de certificado

Você deve instalar os patches mais recentes do sistema operacional. Consulte [atualizações de segurança](#security-updates).

Estrutura do WCF escolhe automaticamente o protocolo mais alto disponível até TLS 1.2, a menos que você configurar explicitamente uma versão de protocolo. Para obter mais informações, consulte a seção anterior [transporte TCP do WCF para usar segurança de transporte com as credenciais de certificado](#wcf-tcp-cert).

### <a name="for-net-framework-35---451-and-not-wcf"></a>Para o .NET Framework 3.5 - 4.5.1 e não o WCF

Recomendamos que você atualize seu aplicativo .NET Framework 4.7 ou versões posteriores. Se você não pode atualizar, execute as etapas a seguir. Em algum momento no futuro, seu aplicativo poderá falhar até você atualizar para o .NET Framework 4.7 ou versões posteriores.

Definir o [SchUseStrongCrypto](#schusestrongcrypto) e [SystemDefaultTlsVersions](#systemdefaulttlsversions) chaves do registro como 1. Consulte [Configurando a segurança por meio do registro do Windows](#configuring-security-via-the-windows-registry). A versão 3.5 do .NET Framework oferece suporte a `SchUseStrongCrypto` sinalizador somente quando um valor explícito do TLS é passado.

Se você estiver executando no .NET Framework 3.5, você precisa instalar um patch ativo para que o TLS 1.2 pode ser especificado por seu programa:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Pacote cumulativo de atualizações de confiabilidade HR-1605 - suporte para versões padrão do sistema do TLS incluído no .NET Framework 3.5.1 no Windows 7 SP1 e Server 2008 R2 SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Pacote cumulativo de atualizações de confiabilidade HR-1605 - suporte para TLS padrão versões do sistema incluídos no .NET Framework 3.5 no Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Rollup de confiabilidade 1605 HR - suporte para versões padrão do TLS do sistema incluídos no .NET Framework 3.5 no Windows 8.1 e Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | 1605 pacote cumulativo de hotfixes 3154521 para o .NET Framework 4.5.2 e 4.5.1 no Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Para o WCF usando o .NET Framework 3.5 - 4.5.2 usando a segurança de transporte TCP com as credenciais de certificado

As versões da estrutura do WCF são codificados para usar valores SSL 3.0 e TLS 1.0. Esses valores não podem ser alterados. Você deve atualizar e redirecionar para o NET Framework 4.6 ou posterior para usar o TLS 1.1 e 1.2.

## <a name="if-your-app-targets-net-framework-35"></a>Se seu aplicativo tem como alvo o .NET Framework 3.5

Se você deve definir explicitamente um protocolo de segurança em vez de deixar o .NET framework ou escolha o sistema operacional o protocolo de segurança, adicione `SecurityProtocolTypeExtensions` e `SslProtocolsExtension` enumerações ao seu código. `SecurityProtocolTypeExtensions` e `SslProtocolsExtension` incluem valores de `Tls12`, `Tls11`e o `SystemDefault` valor. Consulte [suporte para TLS padrão versões do sistema incluídos no .NET Framework 3.5 no Windows 8.1 e Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Configurando a segurança por meio de AppContext alterna (para .NET Framework 4.6 ou posterior)

O [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) opções descritas nesta seção são relevantes se seu aplicativo é destinado ou é executado no .NET Framework 4.6 ou posterior. Se, por padrão, ou definindo-los explicitamente, os comutadores devem ser `false` se possível. Se você quiser configurar a segurança por meio de um ou ambos os comutadores, não especifique um valor de protocolo de segurança em seu código; fazer poderia substituir a switches.

As opções têm o mesmo efeito se você está fazendo a rede de HTTP (<xref:System.Net.ServicePointManager>) ou de rede de soquetes TCP (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Um valor de `false` para `Switch.System.Net.DontEnableSchUseStrongCrypto` faz com que o aplicativo para usar criptografia forte. Um valor de `false` para `DontEnableSchUseStrongCrypto` usa protocolos de rede mais seguros (TLS 1.2, TLS 1.1 e TLS 1.0) e bloqueia a protocolos que não são seguros. Para obter mais informações, consulte [sinalizador SCH_USE_STRONG_CRYPTO o](#the-schusestrongcrypto-flag). Um valor de `true` desabilita a criptografia forte para seu aplicativo.

Se seu aplicativo tem como alvo o .NET Framework 4.6 ou posterior, essa opção padrão é `false`. Que é um padrão seguro, é recomendável. Se seu aplicativo é executado no .NET Framework 4.6, mas tem como alvo uma versão anterior, a opção padrão é `true`. Nesse caso, você deve definir explicitamente-lo para `false`.

`DontEnableSchUseStrongCrypto` só deve ter um valor de `true` se você precisar se conectar a serviços herdados não oferecem suporte a criptografia forte e não podem ser atualizados.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Um valor de `false` para `Switch.System.Net.DontEnableSystemDefaultTlsVersions` faz com que seu aplicativo para permitir que o sistema operacional escolher o protocolo. Um valor de `true` faz com que o aplicativo para usar protocolos escolhidos pelo .NET Framework.

Se seu aplicativo tem como alvo o .NET Framework 4.7 ou versões posteriores, essa opção padrão é `false`. Que é um padrão seguro é recomendável. Se seu aplicativo é executado no .NET Framework 4.7 ou versões posteriores, mas tem como alvo uma versão anterior, a opção padrão é `true`. Nesse caso, você deve definir explicitamente-lo para `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Um valor de `false` para `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` faz com que seu aplicativo para usar o valor definido na `ServicePointManager.SecurityProtocols` para segurança de mensagem usando as credenciais de certificado. Um valor de `true` usa o protocolo mais alto disponível, até o TLS 1.0 por

Para aplicativos voltados para o .NET Framework 4.7 e versões posteriores, o valor padrão é `false`. Para aplicativos voltados para o .NET Framework 4.6.2 e anterior, o valor padrão é `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Um valor de `false` para `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` define a configuração padrão para permitir que o sistema operacional escolher o protocolo. Um valor de `true` define o padrão para o protocolo mais alto disponível, até o TLS 1.2.

Para aplicativos voltados para o .NET Framework 4.7.1 e versões posteriores, o valor padrão é `false`. Para aplicativos de destino do .NET Framework 4.7 e versões anterior, o valor padrão é `true`.

Para obter mais informações sobre protocolos TLS, consulte [atenuação: protocolos TLS](../migration-guide/mitigation-tls-protocols.md). Para obter mais informações sobre `AppContext` comutadores, consulte [ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Configurando a segurança por meio do registro do Windows

Se a configuração de um ou ambos `AppContext` opções não estiverem disponíveis, você pode controlar os protocolos de segurança usado pelo seu aplicativo com as chaves de registro do Windows descritas nesta seção. Você não poderá usar um ou ambos os `AppContext` alterna se seu aplicativo tem como alvo uma versão do .NET Framework anterior 4.6 ou você não pode editar o arquivo de configuração. Se você quiser configurar a segurança com o registro, não especifique um valor de protocolo de segurança em seu código; fazer poderia substituir o registro.

Os nomes das chaves do registro são semelhantes aos nomes das correspondentes `AppContext` alterna mas sem um `DontEnable` anexado ao nome. Por exemplo, o `AppContext` alternar `DontEnableSchUseStrongCrypto` é a chave do Registro chamada [SchUseStrongCrypto](#schusestrongcrypto).

Essas chaves estão disponíveis em todas as versões do .NET Framework para o qual há um patch de segurança recentes. Consulte [atualizações de segurança](#security-updates).

Todas as chaves de Registro descritas a seguir têm o mesmo efeito se você está fazendo a rede de HTTP (<xref:System.Net.ServicePointManager>) ou de rede de soquetes TCP (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

O `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` chave do registro tem um valor do tipo DWORD. Um valor de 1 faz com que o aplicativo para usar criptografia forte. A criptografia forte usa protocolos de rede mais seguros (TLS 1.2, TLS 1.1 e TLS 1.0) e bloqueia a protocolos que não são seguros. Um valor 0 desativa a criptografia forte. Para obter mais informações, consulte [sinalizador SCH_USE_STRONG_CRYPTO o](#the-schusestrongcrypto-flag).

Se seu aplicativo tem como alvo o .NET Framework 4.6 ou posterior, essa chave padrão para um valor de 1. Que é um padrão seguro é recomendável. Se seu aplicativo é executado no .NET Framework 4.6, mas tem como alvo uma versão anterior, em seguida, a chave padrão é 0. Nesse caso, você deve definir explicitamente seu valor como 1.

Essa chave só deve ter um valor de 0 se você precisar se conectar a serviços herdados não oferecem suporte a criptografia forte e não podem ser atualizados.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

O `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` chave do registro tem um valor do tipo DWORD. Um valor de 1 faz com que seu aplicativo para permitir que o sistema operacional escolher o protocolo. Um valor de 0 faz com que o aplicativo para usar protocolos escolhidos pelo .NET Framework.

`<VERSION>` deve ser v 4.0.30319 (para o .NET Framework 4 e posterior) ou v 2.0.50727 (para o .NET Framework 3.5).

Se seu aplicativo tem como alvo o .NET Framework 4.7 ou versões posteriores, essa chave padrão para um valor de 1. Que é um padrão seguro é recomendável. Se seu aplicativo é executado no .NET Framework 4.7 ou versões posteriores, mas tem como alvo uma versão anterior, a chave padrão é 0. Nesse caso, você deve definir explicitamente seu valor como 1.

Para obter mais informações, consulte [cumulativa atualização para Windows 10 versão 1511 e Windows Server 2016 Technical Preview 4: 10 de maio de 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

Para obter mais informações com o .NET framework 3.5.1, consulte [suporte para TLS padrão versões do sistema incluídos no .NET Framework 3.5.1 no Windows 7 SP1 e Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

O seguinte _. REG_ arquivo define as chaves do registro e suas variantes para seus valores mais seguros:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001
```

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Configurando protocolos Schannel no registro do Windows

Você pode usar o registro para um controle refinado sobre os protocolos que negocia o seu aplicativo cliente e/ou servidor. Sistema de rede do seu aplicativo atravessa Schannel (que é outro nome para [canal seguro](https://msdn.microsoft.com/library/windows/desktop/aa380123). Configurando `Schannel`, você pode configurar o comportamento do seu aplicativo.

Iniciar com o `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` chave do registro. Sob essa chave, você pode criar todas as subchaves no conjunto de `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`, e `TLS 1.2`. Em cada um desses subchaves, você pode criar subchaves `Client` e/ou `Server`. Em `Client` e `Server`, você pode criar valores DWORD `DisabledByDefault` (0 ou 1) e `Enabled` (0 ou 0xFFFFFFFF).

## <a name="the-schusestrongcrypto-flag"></a>O sinalizador SCH_USE_STRONG_CRYPTO

Quando ele está habilitado (por padrão, por um `AppContext` alternar, ou o registro do Windows), o .NET Framework usa o `SCH_USE_STRONG_CRYPTO` sinalizador quando seu aplicativo solicita um protocolo de segurança TLS. O `SCH_USE_STRONG_CRYPTO` sinalizador pode ser habilitado por padrão, com o `AppContext` alternar, ou com o registro. O sistema operacional passa o sinalizador para `Schannel`para instruir para desativar conhecidos algoritmos criptográficos fracos, codificação pacotes e versões do protocolo TLS/SSL que podem ser habilitadas caso contrário, para melhor interoperabilidade. Para obter mais informações, consulte:

- [Canal de segurança](https://msdn.microsoft.com/library/windows/desktop/aa380123)
- [Estrutura SCHANNEL_CRED](https://msdn.microsoft.com/library/windows/desktop/aa379810)

O `SCH_USE_STRONG_CRYPTO` sinalizador também é passado para `Schannel` quando você usar explicitamente o `Tls` (TLS 1.0) `Tls11`, ou `Tls12` valores de enumeração <xref:System.Net.SecurityProtocolType> ou <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Atualizações de segurança

As práticas recomendadas neste artigo dependem da instalação de atualizações de segurança recentes. Essas atualizações incluem a capacidade de usar recursos posteriores e 4.7 avançadas de Framework .NET. Atualizações de segurança recentes são importantes se seu aplicativo é executado no .NET Framework 4.7 e versões posteriores (mesmo se ele tem como alvo uma versão anterior).

Para atualizar o .NET Framework para permitir que o sistema operacional escolher a versão recomendada do TLS para usar, você deve instalar pelo menos:

- O [visualização de agosto de 2017 .NET Framework de acumulação de qualidade de](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Ou** o [setembro de 2017 segurança do .NET Framework e o pacote cumulativo de atualizações de qualidade](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Confira também: 

- [Versões e dependências do .NET Framework](../migration-guide/versions-and-dependencies.md)
- [Como: determinar quais versões do .NET Framework estão instaladas](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Suporte a TLS 1.2

Para seu aplicativo negociar o TLS 1.2, o sistema operacional e a versão do .NET Framework ambos precisam oferecer suporte a TLS 1.2.

**Requisitos do sistema operacional para dar suporte a TLS 1.2**

Para habilitar ou habilitar novamente o TLS 1.2 e/ou o TLS 1.1, em um sistema com suporte, consulte [as configurações do registro de segurança de camada de transporte (TLS)](/windows-server/security/tls/tls-registry-settings).

| **OS** | **Suporte a TLS 1.2** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | Suporte e habilitado por padrão. |
| Windows 8.1</br>Windows Server 2012 R2 | Suporte e habilitado por padrão. |
| Windows 8.0</br>Windows Server 2012 | Suporte e habilitado por padrão. |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | Com suporte, mas não é ativado por padrão. Consulte o [as configurações do registro de segurança de camada de transporte (TLS)](/windows-server/security/tls/tls-registry-settings) página da web para obter detalhes sobre como habilitar o protocolo TLS 1.2. |
| Windows Server 2008 | Suporte para TLS 1.1 e o TLS 1.2 requer uma atualização. Consulte [atualização para adicionar suporte para TLS 1.1 e TLS 1.2 no Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Sem suporte. |

Para obter informações sobre quais TLS/SSL protocolos estão habilitados por padrão em cada versão do Windows, consulte [protocolos TLS/SSL (Schannel SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159).

**Requisitos para suporte a TLS 1.2 com o .NET Framework 3.5**

Esta tabela mostra a atualização do sistema operacional, que você precisará dar suporte a TLS 1.2 com o .NET Framework 3.5. É recomendável que você aplique todas as atualizações do sistema operacional.

| **OS** | **Atualização mínima necessária dar suporte a TLS 1.2 com o .NET Framework 3.5** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Atualização cumulativa para o Windows 10 versão 1511 e Windows Server 2016 Technical Preview 4: 10 de maio de 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [Suporte para TLS padrão versões do sistema incluídos no .NET Framework 3.5 no Windows 8.1 e Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [Suporte para TLS padrão versões do sistema incluídos no .NET Framework 3.5 no Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [Suporte para TLS padrão versões do sistema incluídos no .NET Framework 3.5.1 no Windows 7 SP1 e Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Suporte para TLS padrão versões do sistema incluídos no .NET Framework 2.0 SP2 no Windows Vista SP2 e Server 2008 SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Sem suporte |

## <a name="azure-cloud-services"></a>Serviços de nuvem do Azure

Se você estiver usando [serviços de nuvem do Azure](https://azure.microsoft.com/services/cloud-services/) funções Web e de trabalho para hospedar e executar seu aplicativo, há algumas considerações que você precisa levar em conta ao suporte a TLS 1.2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>4.7 do .NET framework não está instalado no sistema operacional de convidado do Azure por padrão

A versão mais recente instalada a versão mais recente de 5 de família de sistema operacional de convidado do Azure (Windows Server 2016) é 4.6.2. Para ver quais versões do .NET Framework estão instaladas em cada sistema operacional convidado do Azure, consulte o [versões do sistema operacional de convidado do Azure e matriz de compatibilidade do SDK](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Se seu aplicativo tem como alvo uma versão do .NET Framework que não está disponível na versão do sistema operacional de convidado do Azure, você precisa instalá-lo. Consulte [instalar .NET em funções de serviço de nuvem do Azure](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Se a instalação do framework requer uma reinicialização, as funções de serviço também podem ser reiniciado antes de entrar no estado pronto.

### <a name="azure-guest-os-registry-settings"></a>Configurações de registro do sistema operacional convidado do Azure

Imagem de SO convidado do Azure para [serviços de nuvem do Azure](https://azure.microsoft.com/services/cloud-services/) já tem o `SchUseStrongCrypto` chave do registro é definida como um valor de 1. Para obter mais informações, consulte [SchUseStrongCrypto](#schusestrongcrypto).

Definir o [SystemDefaultTlsVersions](#systemdefaulttlsversions) chave do registro como 1. Consulte [Configurando a segurança por meio do registro do Windows](#configuring-security-via-the-windows-registry).
