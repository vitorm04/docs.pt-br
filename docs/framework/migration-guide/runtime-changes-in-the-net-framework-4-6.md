---
title: "Alterações de tempo de execução no .NET Framework 4.6 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6
- application compatibility
ms.assetid: 5262bcfa-6e48-416b-8972-69cb4002d386
caps.latest.revision: 34
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 407b31c8b5825093d9ba6bab6329aaf8dd821572
ms.openlocfilehash: 140579db3c30221815167857466e7e7cfea95bd5
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="runtime-changes-in-the-net-framework-46"></a>Alterações de tempo de execução do .NET Framework 4.6
Em casos raros, as alterações de tempo de execução podem afetar aplicativos existentes direcionados a versões anteriores do .NET Framework, mas que são executados em uma versão posterior do tempo de execução do .NET Framework. Elas também incluem diferenças no comportamento entre aplicativos que são executados em diferentes ambientes de tempo de execução do .NET Framework. Entre eles estão alterações feitas nas seguintes áreas:  
  
-   [Core](#Core)  
  
-   [Dados](#Data)  
  
-   [Rede](#Networking)  
  
-   [WCF (Windows Communication Foundation)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [Configuração e implantação](#Setup)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [O novo compilador JIT de 64 bits](#RyuJIT)  
  
<a name="Core"></a>   
## <a name="core"></a>Núcleo  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|A partir do [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], a classe <xref:System.Globalization.PersianCalendar> usa o algoritmo solar Hijri.|O algoritmo solar Hijri gera resultados idênticos aos do calendário persa atualmente em uso no Irã e no Afeganistão. Ele também gera resultados que são idênticos ao algoritmo anterior para datas de 1800 a 2023 no calendário gregoriano. As datas fora desse intervalo poderão ser afetadas se a classe <xref:System.Globalization.PersianCalendar> for usada para executar conversões de data (por exemplo, entre datas do calendário gregoriano e datas do calendário persa) ou para determinar se um ano específico é um ano bissexto.<br /><br /> Devido à mudança, o valor da propriedade <xref:System.Globalization.PersianCalendar.MinSupportedDateTime%2A?displayProperty=fullName> foi alterado de 21 de março de 0622 para 22 de março de 0622 em sistemas nos quais o [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] está instalado.<br /><br /> Para saber mais, confira o tópico <xref:System.Globalization.PersianCalendar>.|Secundário|  
|<xref:System.Runtime.Versioning.TargetFrameworkAttribute>|Para o domínio do aplicativo padrão, o valor da propriedade <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> é derivado de <xref:System.Runtime.Versioning.TargetFrameworkAttribute>, se um estiver presente, a menos que seja explicitamente definido pela atribuição de um nome à propriedade <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.  Nas versões anteriores do .NET Framework, o valor do atributo <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> é `null`, a menos que vários caminhos de código especial sejam executados ou um domínio do aplicativo não padrão seja criado sem especificar explicitamente sua estrutura de destino na propriedade <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>.<br /><br /> Para domínios do aplicativo não padrão, não há alteração na maneira que o valor da propriedade <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> é determinado. Se nenhum valor for explicitamente atribuído à propriedade <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName>, o domínio do aplicativo não padrão herdará o nome da estrutura de destino do domínio do aplicativo padrão.|Para o domínio do aplicativo padrão, o <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> pode retornar um valor não nulo quando ele anteriormente retornava `null`. Esse é o comportamento desejado.|Edge|  
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|Se algum certificado instalado no sistema não tiver suporte do .NET Framework, passar um valor de `True` para o argumento `verbose` retornará uma cadeia de caracteres válida. Nas versões anteriores do .NET Framework, a tentativa de acessar informações de chave públicas de certificados sem suporte, em alguns casos, gera uma exceção.|Esse método é apenas informativo; as observações da documentação que são geradas podem não ser consistentes entre as versões do .NET Framework. Essa alteração afeta somente aplicativos que chamam o método `ToString(True)` e tiverem instalado certificados que não têm suporte do .NET Framework. Ao retornar uma cadeia de caracteres em vez de gerar uma exceção, essa alteração torna o método mais robusto.|Edge|  
|ETW (Rastreamento de Eventos para Windows)|No [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e 4.6.1, o tempo de execução gera uma <xref:System.ArgumentException> quando dois nomes de evento diferem somente por um sufixo "Start" ou "Stop" (como quando um evento é denominado `LogUser` e outro é denominado `LogUserStart`). Nesse caso, o tempo de execução não pode construir a origem do evento, que não pode emitir nenhum log.|Certifique-se de que dois nomes de evento não sejam diferentes apenas por um sufixo "Start" ou "Stop".<br /><br /> Esse requisito foi removido a partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]; o tempo de execução pode esclarecer nomes de evento que diferem apenas pelo sufixo "Start".|Edge|  
|Reflexão e DCOM (Distributed COM)|Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo. Os seguintes tipos são afetados: <xref:System.Reflection.Assembly>; <xref:System.Reflection.MemberInfo> e seus tipos derivados, incluindo <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Type>, e <xref:System.Reflection.TypeInfo>; <xref:System.Reflection.MethodBody>; <xref:System.Reflection.Module>; e <xref:System.Reflection.ParameterInfo>.|As chamadas a [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707.aspx) para o objeto retornam `E_NOINTERFACE`.|Secundário|  
  
<a name="Data"></a>   
## <a name="data"></a>Dados  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Uma conexão TCP/IP com um banco de dados do SQL Server que é resolvida para `localhost`|A partir do [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], a tentativa de conexão falha com o erro "Ocorreu um erro relacionado à rede ou específico à instância durante o estabelecimento de uma conexão com o SQL Server. O servidor não foi encontrado ou não estava acessível. Verifique se o nome da instância está correto e se o SQL Server está configurado para permitir conexões remotas. (provedor: Interfaces de Rede do SQL, erro: 26 – Erro ao localizar servidor/instância especificado)"|Esse problema foi resolvido e o comportamento anterior restaurado no [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Para se conectar a um banco de dados do SQL Server que seja resolvido para `localhost`, faça upgrade para o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)].|Secundário|  
  
<a name="Networking"></a>   
## <a name="networking"></a>Rede  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Valores de data e hora na classe <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>.|Para cumprir os padrões da [RFC822](http://www.ietf.org/rfc/rfc0822.txt) e [RFC2822](http://www.ietf.org/rfc/rfc2822.txt), um valor formatado de data e hora agora tem uma hora de dois dígitos. Anteriormente, ele tinha uma hora de um único dígito para valores abaixo de 10:00.|Essa alteração afeta os seguintes cenários de uso:<br /><br /> - Comparando os comprimentos ou códigos hash dos objetos <xref:System.Net.Mime.ContentDisposition> serializados entre versões do .NET Framework.<br />- Comparando o valor retornado do método <xref:System.Net.Mime.ContentDisposition.ToString%2A> ou a representação da cadeia de caracteres dos valores de propriedade de data e hora <xref:System.Net.Mime.ContentDisposition> entre as versões do .NET Framework.|Secundário|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Serviços WCF que usam NETTCP com a autenticação de segurança e certificado SSL|O .NET Framework 4.6 adiciona o TLS 1.1 e o TLS 1.2 à lista padrão de protocolos SSL do WCF. Quando os computadores cliente e servidor têm o .NET Framework 4.6 ou posteriores instalados, o TLS 1.2 é usado para negociação.|O TLS 1.2 não dá suporte à autenticação do certificado MD5. Consequentemente, se um cliente usar um certificado MD5, o cliente WCF falhará ao se conectar ao serviço WCF. Para saber mais, confira [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md) (Mitigação: serviços WCF e autenticação de certificado).|Secundário|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Renderização de janela em um cenário de vários monitores|A janela inteira é renderizada sem distorção quando ela se estende para fora de uma exibição em um cenário de vários monitores.|Confira [Mitigation: WPF Window Rendering](../../../docs/framework/migration-guide/mitigation-wpf-window-rendering.md) (Mitigação: renderização da janela do WPF).|Secundário|  
|Verificador ortográfico em controles habilitados para texto do WPF|Quando em execução no Windows 10, o verificador ortográfico pode não funcionar porque os recursos de verificação ortográfica da plataforma estão disponíveis somente para idiomas presentes na lista de idiomas de entrada.|No Windows 10, quando um idioma é adicionado à lista de teclados disponíveis, o Windows baixa e instala automaticamente um pacote FOD (Recurso sob Demanda) correspondente que fornece recursos de verificação ortográfica. Ao adicionar o idioma à lista de idiomas de entrada, o verificador ortográfico terá suporte.|Secundário|  
  
<a name="Setup"></a>   
## <a name="setup-and-deployment"></a>Configuração e implantação  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Controle de versão do produto|O controle de versão do produto foi alterado nas versões anteriores do .NET Framework, especialmente o .NET Framework 4, 4.5, 4.5.1 e 4.5.2. Para saber mais, confira [Mitigação: Controle de versão de produto](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|Confira [Mitigação: Controle de versão de produto](../../../docs/framework/migration-guide/mitigation-product-versioning.md).|Médio|  
  
<a name="ClickOnce"></a>   
## <a name="clickonce"></a>ClickOnce  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Aplicativos publicados com o ClickOnce que usam um certificado de assinatura de código SHA-256.|Os aplicativos ClickOnce direcionados ao [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ou a versões anteriores e que são assinados com um certificado SHA-256 não têm mais uma dependência de tempo de execução no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou em uma versão posterior.|Anteriormente, assinar um aplicativo ClickOnce direcionado ao [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ou a versões anteriores com um certificado SHA-256 exigia que o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou uma versão posterior estivesse presente no sistema de destino. Isso resultou em erros nos casos em que ele não estava presente. Essa alteração elimina essa dependência e permite que certificados SHA-256 sejam usados para assinar aplicativos ClickOnce direcionados ao [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] e versões anteriores.|Secundário|  
  
<a name="RyuJIT"></a>   
## <a name="the-new-64-bit-jit-compiler"></a>O novo compilador JIT de 64 bits  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Compilação JIT de 64 bits|A partir do .NET Framework 4.6, um novo compilador JIT de 64 bits é usado para compilação Just-In-Time. Essa alteração não afeta o compilador JIT de 32 bits.|Em alguns casos, será gerada uma exceção inesperada ou um comportamento diferente será observado se um aplicativo for executado usando o compilador de 32 bits ou o compilador JIT de 64 bits antigo. **Observação:** todos esses problemas foram resolvidos no novo compilador de 64 bits lançado com o .NET Framework 4.6.2. A maioria também foi resolvida nas versões de serviço do .NET Framework 4.6 e 4.6.1, incluídos com o Windows Update. <br /><br /> Para saber mais, confira [Atenuação: Novo compilador JIT de 64 bits](../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md).|Edge|  
|Tratamento de exceção (retornar de uma região `try`)|Ao contrário do compilador Just-In-Time JIT64 mais antigo, o novo compilador JIT de 64 bits não permite uma instrução IL `ret` em uma região `try`.|Retornar de uma região `try` não é permitido pela especificação ECAM-335, e nenhum compilador gerenciado conhecido gera tal IL. No entanto, o compilador JIT64 executará essa IL se ela for gerada usando emissão de reflexo.<br /><br /> Se seu aplicativo gera uma IL que inclui um opcode `ret` em uma região `try`, você pode:<br /><br /> – Direcionar o .NET Framework 4.5 ou adicionar o elemento [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) ao arquivo de configuração de aplicativo para usar o compilador JIT antigo e evitar a alteração.<br />- Atualizar a IL gerada a ser retornada após a região `try`.<br />-|Edge|
