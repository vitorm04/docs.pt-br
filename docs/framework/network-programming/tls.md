---
title: Melhores práticas do TLS (Transport Layer Security) com o .NET Framework
description: Descreve as melhores práticas de uso da segurança do protocolo TLS (Transport Layer Security) com o .NET Framework
ms.date: 10/22/2018
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
ms.openlocfilehash: b08d119c0c7edb71ceab5c763c1359bf4c90cfec
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212528"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Melhores práticas do TLS (Transport Layer Security) com o .NET Framework

O protocolo TLS (Transport Layer Security) é um padrão da indústria projetado para ajudar a proteger a privacidade das informações comunicadas pela Internet. O [TLS 1.2](https://tools.ietf.org/html/rfc5246) é um padrão que fornece aprimoramentos de segurança em relação às versões anteriores. Com o tempo, o TLS 1.2 será substituído pelo padrão mais recentemente lançado, o [TLS 1.3](https://tools.ietf.org/html/rfc8446), que é mais rápido e mais seguro. Este artigo apresenta recomendações para proteger aplicativos .NET Framework que usam o protocolo TLS.

Para garantir que os aplicativos .NET Framework continuem seguros, a versão do TLS **não** deve ser codificada. Os aplicativos .NET Framework devem usar a versão do TLS compatível com o SO (sistema operacional).

Este documento é destinado a desenvolvedores que estejam:

- Usando diretamente as APIs do <xref:System.Net> (por exemplo, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Usando diretamente clientes do WCF e serviços usando o namespace <xref:System.ServiceModel?displayProperty=nameWithType>.
- Usando as funções de Trabalho e Web do [Serviços de Nuvem do Azure](https://azure.microsoft.com/services/cloud-services/) para hospedar e executar seu aplicativo. Confira a seção [Serviços de Nuvem do Azure](#azure-cloud-services).

Recomendamos que você:

- Defina o .NET Framework 4.7 ou versões posteriores como destino nos seus aplicativos. Defina o .NET Framework 4.7.1 ou versões posteriores como destino nos seus aplicativos WCF.
- Não especifique a versão do protocolo TLS. Configure seu código para permitir que o sistema operacional decida sobre a versão do protocolo TLS.
- Realize uma auditoria completa de código para verificar se que você não está especificando uma versão do protocolo TLS ou SSL.

Quando seu aplicativo permite que o sistema operacional escolha a versão do protocolo TLS:

- Ele aproveita automaticamente os novos protocolos adicionados no futuro, como o protocolo TLS 1.3.
- O sistema operacional bloqueia os protocolos que forem identificados como não seguros.

A seção [Auditar seu código e fazer alterações no código](#audit-your-code-and-make-code-changes) aborda como auditar e atualizar seu código.

Este artigo explica como habilitar a segurança máxima disponível para a versão do .NET Framework para a qual seu aplicativo é destinado e na qual é executado. Quando um aplicativo define explicitamente um protocolo de segurança e versão, ele recusa qualquer outro dado alternativo e recusa o comportamento padrão do .NET Framework e sistema operacional. Se você quiser que seu aplicativo possa negociar uma conexão do TLS 1.2, configurar explicitamente para uma versão inferior do TLS impede uma conexão com o TLS 1.2.

Se não puder evitar a codificação de uma versão do protocolo, recomendamos especificar o TLS 1.2. Para obter orientações sobre como identificar e remover as dependências do TLS 1.0, baixe o white paper [Solucionar o problema do TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).

O WCF dá suporte ao TLS 1.0, 1.1 e 1.2 como o padrão no .NET Framework 4.7. A partir do .NET Framework 4.7.1, o WCF define a versão configurada do sistema operacional como padrão. Se um aplicativo for explicitamente configurado com `SslProtocols.None`, o WCF usará a configuração do sistema operacional padrão ao usar o transporte NetTcp.

É possível fazer perguntas sobre este documento na questão do GitHub [Melhores práticas do TLS (Transport Layer Security) com o .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Auditar seu código e fazer alterações no código

Para aplicativos ASP.NET, inspecione o elemento `<system.web><httpRuntime targetFramework>` de _web.config_ para verificar se você está usando a versão desejada do .NET Framework.

Para o Windows Forms e outros aplicativos, confira [Como Direcionar a uma versão do .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Use as seções a seguir para verificar se você não está usando uma versão específica do TLS ou SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Se o aplicativo definir o .NET Framework 4.7 ou versões posteriores como destino

As seções a seguir para mostram como verificar se você não está usando uma versão específica do TLS ou SSL.

### <a name="for-http-networking"></a>Para rede HTTP

O <xref:System.Net.ServicePointManager>, usando o .NET Framework 4.7 e versões posteriores, define como padrão o sistema operacional com o melhor protocolo de segurança e versão. Para obter a melhor opção padrão de sistema operacional, se possível, não defina um valor para a propriedade <xref:System.Net.ServicePointManager.SecurityProtocol>. Do contrário, defina-o como <xref:System.Net.SecurityProtocolType.SystemDefault>.

O restante deste artigo não é relevante ao definir o .NET Framework 4.7 ou versões posteriores como destino para uma rede HTTP.

### <a name="for-tcp-sockets-networking"></a>Para rede de soquetes TCP

O <xref:System.Net.Security.SslStream>, usando o .NET Framework 4.7 e versões posteriores, define como padrão o sistema operacional com o melhor protocolo de segurança e versão. Para obter a melhor opção padrão de sistema operacional, se possível, não use as sobrecargas do método de <xref:System.Net.Security.SslStream> que levam um parâmetro <xref:System.Security.Authentication.SslProtocols> explícito. Caso contrário, passe <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Recomendamos não usar o <xref:System.Security.Authentication.SslProtocols.Default>; configurar o `SslProtocols.Default` força o uso do SSL 3.0 /TLS 1.0 e impede o TLS 1.2.

Não defina um valor para a propriedade <xref:System.Net.ServicePointManager.SecurityProtocol> (para a rede HTTP).

Não use as sobrecargas de método do <xref:System.Net.Security.SslStream> que levam um parâmetro <xref:System.Security.Authentication.SslProtocols> explícito (para rede de soquetes TCP). Ao redirecionar seu aplicativo para o .NET Framework 4.7 ou versões posteriores, você estará seguindo a recomendação de melhores práticas.

O restante deste tópico não é relevante ao definir o .NET Framework 4.7 ou versões posteriores como destino para uma rede de soquetes TCP.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Para o transporte de TCP do WCF usando a segurança de transporte com credenciais de certificado

O WCF usa a mesma pilha de rede do restante do .NET Framework.

Se você estiver definindo o 4.7.1 como destino, o WCF é configurado para permitir que o sistema operacional escolha o melhor protocolo de segurança por padrão, a menos que explicitamente configurado:

- No seu arquivo de configuração do aplicativo.
- **Ou**, no seu aplicativo no código-fonte.

Por padrão, o .NET Framework 4.7 e versões posteriores são configuradas para usar o TLS 1.2 e permite conexões usando o TLS 1.1 ou TLS 1.0. Configure o WCF para permitir que o sistema operacional escolha o melhor protocolo de segurança configurando a associação para usar <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Isso pode ser definido em <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` pode ser acessado em <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` pode ser acessado em <xref:System.ServiceModel.NetTcpBinding.Security>.

Se você estiver usando uma associação personalizada:

- Configure o WCF para permitir que o sistema operacional escolha o melhor protocolo de segurança configurando <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> para usar <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Ou** configure o protocolo usado com o caminho de configuração `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Se você **não** estiver utilizando uma associação personalizada **e** estiver definindo sua associação do WCF usando a configuração, defina o protocolo usado com o caminho de configuração `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Para Segurança de Mensagens do WCF com as credenciais de certificado

O .NET Framework 4.7 e versões posteriores usam por padrão o protocolo especificado na propriedade <xref:System.Net.ServicePointManager.SecurityProtocol>. Quando o [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` é definido como `true`, o WCF escolhe o melhor protocolo, até o TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Se o aplicativo definir uma versão do .NET Framework anterior à 4.7 como destino

Audite seu código para verificar se você não está configurando uma versão específica do protocolo TLS ou SSL usando as seguintes seções:

### <a name="for-net-framework-46---462-and-not-wcf"></a>Para o .NET Framework 4.6 – 4.6.2 e não WCF

Defina a opção `DontEnableSystemDefaultTlsVersions` `AppContext` como `false`. Confira [Configurar a segurança por meio de opções do AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Para o WCF usando o .NET Framework 4.6 – 4.6.2 usando a segurança de transporte do TCP com Credenciais de Certificado

Você deve instalar os patches mais recentes do sistema operacional. Confira [Atualizações de segurança](#security-updates).

A estrutura do WCF escolhe automaticamente o maior protocolo disponível até o TLS 1.2, a menos que você configure explicitamente uma versão do protocolo. Para saber mais, confira a seção anterior [Para transporte de TCP do WCF usando a segurança de transporte com credenciais de certificado](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Para o .NET Framework 3.5 a 4.5.2 e não o WCF

Recomendamos atualizar seu aplicativo para o .NET Framework 4.7 ou versões posteriores. Se não for possível atualizar, execute as etapas a seguir. Em um determinado momento no futuro, seu aplicativo poderá falhar até você atualizar para o .NET Framework 4.7 ou versões posteriores.

Defina as chaves do Registro [SchUseStrongCrypto](#schusestrongcrypto) e [SystemDefaultTlsVersions](#systemdefaulttlsversions) como 1. Confira [Como configurar a segurança por meio do Registro do Windows](#configuring-security-via-the-windows-registry). A versão 3.5 do .NET Framework só dá suporte ao sinalizador `SchUseStrongCrypto` quando um valor explícito de TLS é passado.

Se você estiver executando no .NET Framework 3.5, será preciso instalar uma aplicação de patch para que o TLS 1.2 possa ser especificado pelo seu programa:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Pacote Cumulativo de Atualizações de Confiabilidade HR-1605 – Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 3.5.1 no Windows 7 SP1 e Server 2008 R2 SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Pacote Cumulativo de Atualizações de Confiabilidade HR-1605 – Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 3.5 no Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Pacote Cumulativo de Atualizações de Confiabilidade HR-1605 – Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 3.5 no Windows 8.1 e Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | Pacote Cumulativo de Atualizações 3154521 de Hotfix 1605 para o .NET Framework 4.5.2 e 4.5.1 no Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Para o WCF usando o .NET Framework 3.5 – 4.5.2 usando a segurança de transporte do TCP com Credenciais de Certificado

Essas versões da estrutura do WCF são codificadas para usar valores do protocolo SSL 3.0 e TLS 1.0. Esses valores não podem ser alterados. É preciso atualizar e redirecionar para o .NET Framework 4.6 ou versões posteriores para usar o TLS 1.1 e 1.2.

## <a name="if-your-app-targets-net-framework-35"></a>Se o aplicativo definir o .NET Framework 3.5 como destino

Se você precisa definir explicitamente um protocolo de segurança em vez de deixar o .NET Framework ou o sistema operacional escolhê-lo, adicione as enumerações `SecurityProtocolTypeExtensions` e `SslProtocolsExtension` ao seu código. `SecurityProtocolTypeExtensions` e `SslProtocolsExtension` incluem valores para `Tls12`, `Tls11` e o valor `SystemDefault`. Confira [Suporte para versões padrão do sistema TLS incluídas no .NET Framework 3.5 no Windows 8.1 e Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Como configurar a segurança por meio das opções AppContext (para o .NET Framework 4.6 ou versões posteriores)

As opções [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) descritas nesta seção serão relevantes se o aplicativo for destinado ou executado no .NET Framework 4.6 ou versões posteriores. Seja por padrão ou definindo-as explicitamente, as opções devem ser `false` se possível. Se você quiser configurar a segurança por meio de uma ou ambas as opções, não especifique um valor de protocolo de segurança no seu código; isso pode substituir as opções.

As opções têm o mesmo efeito, seja para uma rede HTTP (<xref:System.Net.ServicePointManager>) ou uma rede de soquetes TCP (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Um valor `false` para `Switch.System.Net.DontEnableSchUseStrongCrypto` faz com que seu aplicativo use criptografia forte. Um valor `false` para `DontEnableSchUseStrongCrypto` usa protocolos de rede mais seguros (TLS 1.2, TLS 1.1 e TLS 1.0) e bloqueia protocolos não seguros. Para saber mais, confira [O sinalizador SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag). Um valor `true` desabilita uma criptografia forte para o aplicativo.

Se o aplicativo for destinado ao .NET Framework 4.6 ou versões posteriores, essa opção será definida como `false` por padrão. Esse é um padrão seguro que recomendamos. Se o aplicativo for executado em .NET Framework 4.6, mas for destinado a uma versão anterior, a opção será definida como `true` por padrão. Nesse caso, defina-a explicitamente como `false`.

`DontEnableSchUseStrongCrypto` só deve ter um valor `true` se você precisar se conectar a serviços herdados que não suportem criptografia forte e não possam ser atualizados.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Um valor `false` para `Switch.System.Net.DontEnableSystemDefaultTlsVersions` faz com que seu aplicativo permita que o sistema operacional escolha o protocolo. Um valor `true` faz com que seu aplicativo use protocolos escolhidos pelo .NET Framework.

Se o aplicativo for destinado ao .NET Framework 4.7 ou versões posteriores, essa opção será definida como `false` por padrão. Esse é um padrão seguro que recomendamos. Se o aplicativo for executado no .NET Framework 4.7 ou versões posteriores, mas for destinado a uma versão anterior, a opção será definida como `true` por padrão. Nesse caso, defina-a explicitamente como `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Um valor `false` para `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` faz com que seu aplicativo use o valor definido no `ServicePointManager.SecurityProtocols` para segurança de mensagem usando credenciais de certificado. Um valor `true` usa o maior protocolo disponível, até o TLS1.0

Para aplicativos destinados ao .NET Framework 4.7 e versões posteriores, o valor padrão é `false`. Para aplicativos destinados ao .NET Framework 4.6.2 e versões anteriores, o valor padrão é `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Um valor `false` para `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` define a configuração padrão para permitir que o sistema operacional escolha o protocolo. Um valor `true` define o padrão como o maior protocolo disponível, até o TLS1.2.

Para aplicativos destinados ao .NET Framework 4.7.1 e versões posteriores, o valor padrão é `false`. Para aplicativos destinados ao .NET Framework 4.7 e versões anteriores, o valor padrão é `true`.

Para saber mais sobre os protocolos TLS, confira [Mitigação: protocolos TLS](../migration-guide/mitigation-tls-protocols.md). Para saber mais sobre as opções `AppContext`, confira [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Como configurar a segurança por meio do Registro do Windows

> [!WARNING]
> Definir as chaves do Registro afeta todos os aplicativos no sistema. Use esta opção somente se você estiver no controle total do computador e puder controlar as alterações ao Registro.

Se configurar uma ou ambas as opções `AppContext` não for uma opção, será possível controlar os protocolos de segurança que seu aplicativo usa com as chaves do Registro do Windows descritas nesta seção. Você não poderá usar uma ou ambas as opções `AppContext` se o aplicativo executar no .NET Framework 4.5.2 ou anterior ou se não for possível editar o arquivo de configuração. Se você quiser configurar a segurança com o Registro, não especifique um valor de protocolo de segurança no seu código; isso substituirá a configuração do Registro.

Os nomes das chaves do Registro são similares aos nomes das opções `AppContext` correspondentes, mas sem um `DontEnable` anexado ao nome. Por exemplo, a opção `AppContext` `DontEnableSchUseStrongCrypto` é a chave do Registro chamada [SchUseStrongCrypto](#schusestrongcrypto).

Essas chaves estão disponíveis em todas as versões do .NET Framework para as quais há um patch de segurança recente. Confira [Atualizações de segurança](#security-updates).

Todas as chaves do Registro descritas abaixo têm o mesmo efeito, seja para uma rede HTTP (<xref:System.Net.ServicePointManager>) ou uma rede de soquetes TCP (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

A chave do Registro `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` tem um valor do tipo DWORD. Um valor 1 faz com que seu aplicativo use criptografia forte. A criptografia forte usa protocolos de rede mais seguros (TLS 1.2, TLS 1.1 e TLS 1.0) e bloqueia protocolos não seguros. Um valor 0 desabilita a criptografia forte. Para saber mais, confira [O sinalizador SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag).

Se o aplicativo for destinado ao .NET Framework 4.6 ou versões posteriores, o valor dessa chave será definido como 1 por padrão. Esse é um padrão seguro que recomendamos. Se o aplicativo for executado em .NET Framework 4.6, mas for destinado a uma versão anterior, a chave será definida como 0 por padrão. Nesse caso, defina o valor explicitamente como 1.

Essa chave só deve ter um valor 0 se você precisar se conectar a serviços herdados que não deem suporte à criptografia forte e não possam ser atualizados.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

A chave do Registro `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` tem um valor do tipo DWORD. Um valor 1 faz com que seu aplicativo permita que o sistema operacional escolha o protocolo. Um valor 0 faz com que seu aplicativo use protocolos escolhidos pelo .NET Framework.

A `<VERSION>` deve ser v4.0.30319 (para o .NET Framework 4 e superior) ou v2.0.50727 (para .NET Framework 3.5).

Se o aplicativo for destinado ao .NET Framework 4.7 ou versões posteriores, o valor dessa chave será definido como 1 por padrão. Esse é um padrão seguro que recomendamos. Se o aplicativo for executado no .NET Framework 4.7 ou versões posteriores, mas for destinado a uma versão anterior, a chave será definida como 0 por padrão. Nesse caso, defina o valor explicitamente como 1.

Para obter mais informações, confira [Atualização cumulativa do Windows 10 Versão 1511 e do Windows Server 2016 Technical Preview 4: 10 de maio de 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

Para saber mais sobre o .NET Framework 3.5.1, confira [Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 3.5.1 no Windows 7 SP1 e Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

O arquivo _.REG_ a seguir define as chaves do Registro e suas variantes para seus valores mais seguros:

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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Configurar os protocolos Schannel no Registro do Windows

Você pode usar o registro para um controle refinado sobre os protocolos que seu aplicativo servidor e/ou cliente negocia. A rede do seu aplicativo passa pelo Schannel (que é outro nome para [Canal Seguro](/windows/desktop/SecAuthN/secure-channel). Configurando o `Schannel`, é possível configurar o comportamento do seu aplicativo.

Comece com a chave do Registro do `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols`. Sob essa chave, é possível criar qualquer subchave no conjunto `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1` e `TLS 1.2`. Em cada uma dessas subchaves, é possível criar subchaves `Client` e/ou `Server`. Em `Client` e `Server`, é possível criar valores DWORD `DisabledByDefault` (0 ou 1) e `Enabled` (0 ou 0xFFFFFFFF).

## <a name="the-sch_use_strong_crypto-flag"></a>O sinalizador SCH_USE_STRONG_CRYPTO

Quando ele é habilitado (por padrão, por uma opção `AppContext` ou pelo Registro do Windows), o .NET Framework usa o sinalizador `SCH_USE_STRONG_CRYPTO` quando seu aplicativo solicita o protocolo de segurança TLS. O sinalizador `SCH_USE_STRONG_CRYPTO` pode ser habilitado por padrão, com a opção `AppContext` ou com o Registro. O sistema operacional passa o sinalizador para o `Schannel` para instruí-lo a desativar algoritmos criptográficos fracos conhecidos, pacotes de codificação e versões do protocolo TLS/SSL que possam ser habilitadas para uma melhor interoperabilidade. Para obter mais informações, consulte:

- [Canal Seguro](/windows/desktop/SecAuthN/secure-channel)
- [Estrutura SCHANNEL_CRED](/windows/desktop/api/schannel/ns-schannel-_schannel_cred)

O sinalizador `SCH_USE_STRONG_CRYPTO` também é transmitido para o `Schannel` quando você usa explicitamente valores enumerados do `Tls` (TLS 1.0), `Tls11` ou `Tls12` de <xref:System.Net.SecurityProtocolType> ou <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Atualizações de segurança

As melhores práticas neste artigo dependem da instalação de atualizações de segurança recentes. Essas atualizações incluem a capacidade de usar recursos avançados do .NET Framework 4.7 e posterior. As atualizações de segurança recentes são importantes se o aplicativo é executado no .NET Framework 4.7 e em versões posteriores (mesmo se ele for destinado a uma versão anterior).

Para atualizar o .NET Framework para permitir que o sistema operacional escolha a versão recomendada do TLS a ser usada, instale pelo menos:

- A [Prévia do Pacote Cumulativo de Atualizações de Qualidade de agosto de 2017 do .NET Framework](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Ou** o [Pacote Cumulativo de Atualizações de Segurança e Qualidade de setembro de 2017 do .NET Framework](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Confira também: 

- [Versões e dependências do .NET Framework](../migration-guide/versions-and-dependencies.md)
- [Como: Determinar quais versões do .NET Framework estão instaladas](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Suporte para o TLS 1.2

Para que seu aplicativo negocie o TLS 1.2, o sistema operacional e a versão do .NET Framework precisam dar suporte ao TLS 1.2.

**Requisitos do sistema operacional para dar suporte ao TLS 1.2**

Para habilitar ou reabilitar o TLS 1.2 e/ou o TLS 1.1 em um sistema compatível com eles, confira [Configurações do Registro do TLS (protocolo TLS)](/windows-server/security/tls/tls-registry-settings).

| **Sistema operacional** | **Suporte ao TLS 1.2** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Com suporte e habilitado por padrão. |
| Windows 8.1<br>Windows Server 2012 R2 | Com suporte e habilitado por padrão. |
| Windows 8.0<br>Windows Server 2012 | Com suporte e habilitado por padrão. |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | Com suporte, mas não habilitado por padrão. Veja a página da Web [Configurações do Registro do TLS (protocolo TLS)](/windows-server/security/tls/tls-registry-settings) para obter detalhes sobre como habilitar o TLS 1.2. |
| Windows Server 2008 | O suporte ao protocolo TLS 1.2 e TLS 1.1 requer uma atualização. Confira [Atualizar para adicionar suporte ao protocolo TLS 1.1 e TLS 1.2 no Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Sem suporte. |

Para saber mais sobre quais protocolos TLS/SSL são habilitados por padrão em cada versão do Windows, confira [Protocolos no TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).

**Requisitos para suporte ao protocolo TLS 1.2 com .NET Framework 3.5**

Esta tabela mostra a atualização do sistema operacional que você precisará para dar suporte ao protocolo TLS 1.2 com o .NET Framework 3.5. Recomendamos aplicar todas as atualizações do sistema operacional.

| **Sistema operacional** | **Atualização mínima necessária para dar suporte ao TLS 1.2 com .NET Framework 3.5** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Atualização cumulativa do Windows 10 Versão 1511 e do Windows Server 2016 Technical Preview 4: 10 de maio de 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 R2 | [Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 3.5 no Windows 8.1 e Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0<br>Windows Server 2012 | [Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 3.5 no Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | [Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 3.5.1 no Windows 7 SP1 e Server 2008 R2 SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Suporte para Versões Padrão do Sistema TLS incluídas no .NET Framework 2.0 SP2 no Windows Vista SP2 e Server 2008 SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Sem suporte |

## <a name="azure-cloud-services"></a>Serviços de Nuvem do Azure

Se você está usando as funções de Trabalho e Web dos [Serviços de Nuvem do Azure](https://azure.microsoft.com/services/cloud-services/) para hospedar e executar seu aplicativo, há algumas considerações que você precisa levar em conta para dar suporte ao TLS 1.2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>O .NET Framework 4.7 não é instalado no Sistema Operacional Convidado do Azure por padrão

A versão mais recente instalada na última versão do Sistema Operacional Convidado para Família 5 do Azure (Windows Server 2016) é 4.6.2. Para ver quais versões do .NET Framework estão instaladas em cada Sistema Operacional Convidado do Azure, confira as [Versões do Sistema Operacional de Convidado do Azure e matriz de compatibilidade do SDK](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Se o aplicativo for destinado a uma versão do .NET Framework que não esteja disponível na versão do Sistema Operacional Convidado do Azure, será preciso instalá-la por conta própria. Confira [Instalar o .NET em Funções de Serviços de Nuvem do Azure](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Se a instalação da estrutura exigir uma reinicialização, as funções de serviço também podem ser reiniciadas antes de entrar no estado Pronto.

### <a name="azure-guest-os-registry-settings"></a>Configurações de registro do Sistema Operacional Convidado do Azure

A imagem de Família de SOs Convidados 5 do Azure para os [Serviços de Nuvem do Azure](https://azure.microsoft.com/services/cloud-services/) já tem a chave do Registro `SchUseStrongCrypto` definida com um valor 1. Para saber mais, confira [SchUseStrongCrypto](#schusestrongcrypto).

Defina a chave do Registro [SystemDefaultTlsVersions](#systemdefaulttlsversions) como 1. Confira [Como configurar a segurança por meio do Registro do Windows](#configuring-security-via-the-windows-registry).
