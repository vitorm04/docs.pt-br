---
title: Novidades no .NET Framework | Microsoft Docs
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework-4.6
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
caps.latest.revision: 292
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: 56bf5905fc9e4c676e2cf681c9135fddf88e5c89
ms.lasthandoff: 04/08/2017

---
# <a name="what39s-new-in-the-net-framework"></a>Novidades no .NET Framework
<a name="introduction"></a> Este artigo resume os principais recursos novos e aprimoramentos nas seguintes versões do .NET Framework:  
  
 [.NET Framework 4.7](#v47)   
 [.NET Framework 4.6.2](#v462)   
 [.NET Framework 4.6.1](#v461)   
 [.NET 2015 e .NET Framework 4.6](#v46)   
 [.NET Framework 4.5.2](#v452)   
 [.NET Framework 4.5.1](#v451)   
 [.NET Framework 4.5](#core)  
  
 Este artigo não fornece informações abrangentes sobre cada recurso novo e está sujeito a alterações. Para obter informações gerais sobre o .NET Framework, confira [Introdução](http://msdn.microsoft.com/library/c693fd34-88fe-4d90-b332-19eeadf3b7e7). Para conhecer as plataformas compatíveis, confira [Requisitos do sistema](~/docs/framework/get-started/system-requirements.md). Para obter links de download e instruções de instalação, confira [Guia de instalação](../../../docs/framework/install/guide-for-developers.md).  
  
> [!NOTE]
>  A equipe do .NET Framework também libera recursos fora de banda com o NuGet para expandir o suporte à plataforma e introduzir novas funcionalidades, como coleções imutáveis e tipos de vetor habilitados para SIMD. Para saber mais, confira [Bibliotecas de classes e APIs adicionais](http://msdn.microsoft.com/library/cf2d9006-b631-4e5d-81cd-20aab78c60f1) e [O .NET Framework e lançamentos fora da banda](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). Confira uma [lista completa dos pacotes do NuGet](http://blogs.msdn.com/b/dotnet/p/nugetpackages.aspx) para o .NET Framework, ou assine [nosso feed](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).  
  
<a name="v47"></a>   
## <a name="introducing-the-net-framework-47"></a>Apresentação do .NET Framework 4.7  
 O .NET Framework 4.7 se baseia no .NET Framework 4.6, 4.6.1 e 4.6.2, adicionando muitas correções e vários recursos novos, mas permanecendo um produto muito estável.  

> [!NOTE]
> O .NET Framework 4.7 vem pré-instalado em todos os sistemas com a Atualização do Windows 10 para Criadores. Ele não está disponível para download ou instalação em outros sistemas operacionais Windows.  

## <a name="whats-new-in-the-net-framework-47"></a>Novidades no .NET Framework 4.7

O .NET Framework 4.7 inclui novos recursos nas seguintes áreas:

- [Core](#Core47)
- [Rede](#net47)
- [ASP.NET](#ASP-NET47)
- [WCF (Windows Communication Foundation)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

<a name="Core47" />
### <a name="core"></a>Núcleo ###

O .NET Framework 4.7 melhora a serialização do <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Funcionalidade aprimorada com ECC (Criptografia de curva elíptica)***

No .NET Framework 4.7, os métodos `ImportParameters(ECParameters)` foram adicionados às classes <xref:System.Security.Cryptography.ECDsa> e <xref:System.Security.Cryptography.ECDiffieHellman> a fim de permitir a um objeto representar uma chave já estabelecida. Também foi adicionado um método `ExportParameters(Boolean)` à exportação da chave usando parâmetros de curva explícita.

O .NET Framework 4.7 também adiciona suporte para curvas adicionais (incluindo o pacote de curvas Brainpool) e adicionou definições predefinidas para facilitar a criação por meio dos novos métodos de fábrica <xref:System.Security.Cryptography.ECDsa.Create%2A> e <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A>.

Veja um [exemplo dos aprimoramentos de criptografia do .NET Framework 4.7](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) no GitHub.

**Suporte aprimorado para caracteres de controle do DataContractJsonSerializer**

No .NET Framework 4.7, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializa os caracteres de controle de acordo com o padrão ECMAScript 6. Esse comportamento está habilitado por padrão para aplicativos direcionados ao .NET Framework 4.7 e é um recurso baseado no consentimento para aplicativos que estejam executando no .NET Framework 4.7, mas que são direcionados a uma versão anterior do .NET Framework. Para saber mais, confira [Alterações de redirecionamento no .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />
### <a name="networking"></a>Rede ###

O .NET Framework 4.7 adiciona os seguintes recursos de rede:

**Suporte do sistema operacional padrão para protocolos TLS***

A pilha de TLS, que é usada pelo <xref:System.Net.Security.SslStream?displayProperty=fullName> e por componentes de início de pilha, como HTTP, FTP e SMTP, permite que os desenvolvedores usem protocolos TLS padrão com suporte do sistema operacional. Os desenvolvedores não precisam mais codificar uma versão de TLS.

<a name="ASP-NET47" />
### <a name="aspnet"></a>ASP.NET ###

No .NET Framework 4.7, o ASP.NET inclui os seguintes recursos novos:

**Extensibilidade de cache do objeto**

A partir do .NET Framework 4.7, o ASP.NET adiciona um novo conjunto de APIs que permitem aos desenvolvedores substituir as implementações padrão de ASP.NET para o armazenamento em cache de objeto na memória e o monitoramento da memória. Agora, os desenvolvedores podem substituir qualquer um dos três componentes a seguir se a implementação do ASP.NET não for adequada:

- **Armazenamento de cache de objeto**. Na nova seção de configuração de provedores de cache, os desenvolvedores podem conectar novas implementações de um cache de objeto para um aplicativo ASP.NET usando a nova interface **ICacheStoreProvider**.
 
- **Monitoramento da memória**. O monitor de memória padrão no ASP.NET notifica os aplicativos quando eles estiverem se aproximando do limite configurado de bytes particulares para o processo, ou quando o computador estiver com pouca RAM física total disponível. Quando esses limites estiverem próximos, as notificações serão disparadas. Para alguns aplicativos, as notificações são disparadas muito próximas aos limites configurados a fim de permitir reações úteis. Agora, os desenvolvedores podem criar seus próprios monitores de memória e substituir o padrão usando a propriedade <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=fullName>.

- **Reações de limite de memória**. Por padrão, o ASP.NET tenta aparar o cache de objetos e chamar periodicamente <xref:System.GC.Collect%2A?displayProperty=fullName> quando o limite do processo de bytes particulares está próximo. Para alguns aplicativos, a frequência de chamadas para <xref:System.GC.Collect%2A?displayProperty=fullName> ou a quantidade aparada do cache é ineficaz. Agora, os desenvolvedores podem substituir ou complementar o comportamento padrão incluindo implementações do **IObserver** no monitor de memória do aplicativo.

<a name="wcf47" />
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF) ###

O Windows Communication Foundation (WFC) adiciona os seguintes recursos e alterações:

**Capacidade de definir configurações de segurança de mensagem padrão para TLS 1.1 ou TLS 1.2**

A partir do .NET Framework 4.7, o WCF permite que você configure o TSL 1.1 ou o TLS 1.2, além de SSL 3.0 e TSL 1.0, como o protocolo de segurança de mensagem padrão. Esta é uma configuração baseada no consentimento; para habilitá-la, você deve adicionar a seguinte entrada ao arquivo de configuração do aplicativo:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" /> 
</runtime>
```

**Confiabilidade aprimorada de aplicativos WCF e serialização do WCF**

O WCF inclui diversas alterações de código que eliminam as condições de corrida, melhorando o desempenho e a confiabilidade das opções de serialização. Elas incluem:

- Suporte aprimorado para combinação de código síncrono e assíncrono em chamadas para **SocketConnection.BeginRead** e **SocketConnection.Read**.
- Confiabilidade aprimorada ao anular uma conexão com **SharedConnectionListener** e **DuplexChannelBinder**.
- Confiabilidade aprimorada de operações de serialização ao chamar o método [FormatterServices.GetSerializableMembers](assetId:///System.Runtime.Serialization.FormatterServices.GetSerializableMembers(System.Type??qualifyHint=True&autoUpgrade=False).
- Confiabilidade aprimorada ao remover um waiter chamando o método **ChannelSynchronizer.RemoveWaiter**.  

<a name="wf47" />
### <a name="windows-forms"></a>Windows Forms ###

No .NET Framework 4.7, o Windows Forms melhora o suporte para monitores com alto DPI.

**Suporte para DPI alto**

A partir dos aplicativos direcionados ao .NET Framework 4.7, o .NET Framework apresenta o suporte para DPI alto e DPI dinâmico em aplicativos do Windows Forms. O suporte para DPI alto melhora o layout e a aparência de formulários e controles em monitores com alto DPI. O DPI dinâmico altera o layout e a aparência de formulários e controles quando o usuário altera o DPI ou o fator de escala de exibição de um aplicativo em execução.

O suporte ao DPI alto é um recurso baseado no consentimento que você configura definindo uma seção [\<System.Windows.Forms.ConfigurationSection>](Windows%20Forms%20Configuration%20Section.md) no arquivo de configuração do aplicativo. Para saber mais sobre como adicionar suporte ao DPI alto e suporte ao DPI dinâmico para seu aplicativo Windows Forms, confira [Suporte a DPI alto no Windows Forms](High%20DPI%20Support%20In%20Windows%20Forms.md).  

<a name="WPF47"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

No .NET Framework 4.7, o WPF inclui os seguintes aprimoramentos:

**Suporte para uma pilha de toque/caneta com base em mensagens WM_POINTER do Windows**

Agora você tem a opção de usar uma pilha de toque/caneta com base em [mensagens WM_POINTER](https://msdn.microsoft.com/library/windows/desktop/hh454903(v=vs.85).aspx) em vez de WISP (Plataforma de Serviços do Windows Ink). Esse é um recurso do .NET Framework baseado no consentimento. Para saber mais, confira [Alterações de redirecionamento no .NET Framework 4.7](Retargeting%20Changes%20in%20the%20.NET%20Framework%204.7.md).

**Nova implementação para APIs de impressão do WPF**

As APIs de impressão do WPF na classe [System.Printing.PrintQueue](assetId:///T:System.Printing.PrintQueue?qualifyHint=True&autoUpgrade=True) chamam a [Print Document Package API (API de Impressão pacote de documentos)](https://msdn.microsoft.com/library/windows/desktop/hh448418(v=vs.85).aspx) do Windows em vez da [XPS Print API (API de impressão XPS)](https://msdn.microsoft.com/library/windows/desktop/ff686814(v=vs.85).aspx) preterida. Para saber o impacto dessa alteração na compatibilidade do aplicativo, consulte [Alterações de redirecionamento do .NET Framework 4.7](Retargeting%20Changes%20in%20the%20.NET%20Framework%204.7.md). 

<a name="v462"></a>   
## <a name="whats-new-in-the-net-framework-462"></a>Novidades no .NET Framework 4.6.2  
O .NET Framework 4.6.2 inclui novos recursos nas seguintes áreas:  
  
-   [ASP.NET](#ASPNET462)  
  
-   [Categorias de caractere](#Strings)  
  
-   [Criptografia](#Crypto462)  
  
-   [SqlClient](#SQLClient)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF462)  
  
-   [Windows Workflow Foundation (WF)](#WF462)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Converter aplicativos do Windows Forms e do WPF em aplicativos UWP](#UWPConvert)  
  
-   [Melhorias na depuração](#Debug462)  
  
 Para obter uma lista das novas APIs adicionadas ao .NET Framework 4.6.2, confira [Alterações na API do .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) no GitHub. Para obter uma lista de aprimoramentos e correções de bug no .NET Framework 4.6.2, confira [Alterações na API do .NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=708778) no GitHub.  Para saber mais, confira [Anunciando o .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) no Blog do .NET.  
  
<a name="ASPNET462"></a>   
### <a name="aspnet"></a>ASP.NET  
 No .NET Framework 4.6.2, o ASP.NET inclui os seguintes aprimoramentos:  
  
 **Suporte aprimorado para mensagens de erro localizadas em validadores de anotação de dados**  
 Os validadores de anotação de dados permitem que você execute a validação adicionando um ou mais atributos a uma propriedade de classe. O elemento [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) do atributo define o texto da mensagem de erro se a validação falhar. A partir do .NET Framework 4.6.2, o ASP.NET facilita a localização de mensagens de erro. Mensagens de erro serão localizadas se:  
  
1.  O [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) é fornecido no atributo de validação.  
  
2.  O arquivo de recurso é armazenado na pasta App_LocalResources.  
  
3.  O nome do arquivo de recursos localizado tem o formato `DataAnnotation.Localization.{`*nome*`}.resx`, em que *nome* é um nome de cultura no formato *código do Idioma*`-`*Código do país/região* ou *código do Idioma*.  
  
4.  O nome da chave do recurso é a cadeia de caracteres atribuída ao atributo [ValidationAttribute.ErrorMessage](assetId:///P:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage?qualifyHint=True&autoUpgrade=True) e seu valor é a mensagem de erro localizada.  
  
 Por exemplo, o atributo de anotação de dados a seguir define a mensagem de erro da cultura padrão para uma classificação inválida.  
  
```csharp  
  
public class RatingInfo  
{  
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]  
   [Display(Name = "Your Rating")]  
   public int Rating { get; set; }  
}  
  
```  
  
```vb  
  
Public Class RatingInfo  
   \<Required(ErrorMessage = "The rating must be between 1 and 10.")>  
   \<Display(Name = "Your Rating")>  
   Public Property Rating As Integer = 1  
End Class  
  
```  
  
 Você pode criar um arquivo de recurso, DataAnnotation.Localization.fr.resx, cuja chave é a cadeia de caracteres da mensagem de erro e cujo valor é a mensagem de erro localizada. O arquivo deve ser encontrado na pasta `App.LocalResources`. Por exemplo, veja a seguir a chave e seu valor em uma mensagem de erro localizada no idioma francês (fr):  
  
|Nome|Valor|  
|----------|-----------|  
|A classificação deve estar entre 1 e 10.|La note doit être comprise entre 1 et 10.|  
  
 Assim, esse arquivo pode  
  
 Além disso, a localização de anotação de dados é extensível. Os desenvolvedores podem conectar seu próprio provedor de localizador de cadeia de caracteres implementando a interface [IStringLocalizerProvider](assetId:///T:System.Web.Globalization.IStringLocalizerProvider?qualifyHint=False&autoUpgrade=True) para armazenar a cadeia de localização em algum lugar diferente de um arquivo de recurso.  
  
 **Suporte assíncrono com provedores de armazenamento de estado de sessão**  
 Agora, o ASP.NET permite o uso de métodos de retorno de tarefas com provedores de armazenamento de estado da sessão, permitindo assim que os aplicativos ASP.NET obtenham os benefícios de escalabilidade do modo assíncrono. Para dar suporte às operações assíncronas com provedores de armazenamento de estado de sessão, o ASP.NET inclui uma nova interface, [System.Web.SessionState.ISessionStateModule](assetId:///T:System.Web.SessionState.ISessionStateModule?qualifyHint=True&autoUpgrade=True), que herda de [IHttpModule](assetId:///T:System.Web.IHttpModule?qualifyHint=False&autoUpgrade=True) e permite aos desenvolvedores implementar seus próprios módulo de estado de sessão e provedores de estado de sessão assíncrona. A interface é definida assim:  
  
```csharp  
  
public interface ISessionStateModule : IHttpModule {  
    void ReleaseSessionState(HttpContext context);  
    Task ReleaseSessionStateAsync(HttpContext context);  
}  
  
```  
  
 Além disso, a classe [SessionStateUtility](assetId:///T:System.Web.SessionState.SessionStateUtility?qualifyHint=False&autoUpgrade=True) inclui dois novos métodos, [IsSessionStateReadOnly](assetId:///M:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly(System.Web.HttpContext)?qualifyHint=False&autoUpgrade=True) e [IsSessionStateRequired](assetId:///M:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired(System.Web.HttpContext)?qualifyHint=False&autoUpgrade=True), que podem ser usados para oferecer suporte a operações assíncronas.  
  
 **Suporte assíncrono para provedores de cache de saída**  
 A partir do .NET Framework 4.6.2, os métodos de retorno de tarefa podem ser usados com provedores de cache de saída a fim de oferecer os benefícios de escalabilidade do modo assíncrono.  Provedores que implementam esses métodos reduzem o bloqueio de thread em um servidor Web e melhoram a escalabilidade de um serviço ASP.NET.  
  
 As seguintes APIs foram adicionadas para oferecer suporte a provedores de cache de saída assíncronos:  
  
-   A classe [System.Web.Caching.OutputCacheProviderAsync](assetId:///T:System.Web.Caching.OutputCacheProviderAsync?qualifyHint=True&autoUpgrade=True), que herda de [System.Web.Caching.OutputCacheProvider](assetId:///T:System.Web.Caching.OutputCacheProvider?qualifyHint=True&autoUpgrade=True) e permite que os desenvolvedores implementem um provedor de cachê de saída assíncrono.  
  
-   A classe [OutputCacheUtility](assetId:///T:System.Web.Caching.OutputCacheUtility?qualifyHint=False&autoUpgrade=True), que fornece métodos auxiliares para configuração do cache de saída.  
  
-   Dezoito novos métodos na classe [System.Web.HttpCachePolicy](assetId:///T:System.Web.HttpCachePolicy?qualifyHint=True&autoUpgrade=True). Entre elas estão [GetCacheability](assetId:///M:System.Web.HttpCachePolicy.GetCacheability?qualifyHint=False&autoUpgrade=True), [GetCacheExtensions](assetId:///M:System.Web.HttpCachePolicy.GetCacheExtensions?qualifyHint=False&autoUpgrade=True), [GetETag](assetId:///M:System.Web.HttpCachePolicy.GetETag?qualifyHint=False&autoUpgrade=True), [GetETagFromFileDependencies](assetId:///M:System.Web.HttpCachePolicy.GetETagFromFileDependencies?qualifyHint=False&autoUpgrade=True), [GetMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetMaxAge?qualifyHint=False&autoUpgrade=True), [GetMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetMaxAge?qualifyHint=False&autoUpgrade=True), [GetNoStore](assetId:///M:System.Web.HttpCachePolicy.GetNoStore?qualifyHint=False&autoUpgrade=True), [GetNoTransforms](assetId:///M:System.Web.HttpCachePolicy.GetNoTransforms?qualifyHint=False&autoUpgrade=True), [GetOmitVaryStar](assetId:///M:System.Web.HttpCachePolicy.GetOmitVaryStar?qualifyHint=False&autoUpgrade=True), [GetProxyMaxAge](assetId:///M:System.Web.HttpCachePolicy.GetProxyMaxAge?qualifyHint=False&autoUpgrade=True), [GetRevalidation](assetId:///M:System.Web.HttpCachePolicy.GetRevalidation?qualifyHint=False&autoUpgrade=True), [GetUtcLastModified](assetId:///M:System.Web.HttpCachePolicy.GetUtcLastModified?qualifyHint=False&autoUpgrade=True), [GetVaryByCustom](assetId:///M:System.Web.HttpCachePolicy.GetVaryByCustom?qualifyHint=False&autoUpgrade=True), [HasSlidingExpiration](assetId:///M:System.Web.HttpCachePolicy.HasSlidingExpiration?qualifyHint=False&autoUpgrade=True) e [IsValidUntilExpires](assetId:///M:System.Web.HttpCachePolicy.IsValidUntilExpires?qualifyHint=False&autoUpgrade=True).  
  
-   Dois novos métodos na classe [System.Web.HttpCacheVaryByContentEncodings](assetId:///T:System.Web.HttpCacheVaryByContentEncodings?qualifyHint=True&autoUpgrade=True): [GetContentEncodings](assetId:///M:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings?qualifyHint=False&autoUpgrade=True) e [SetContentEncodings](assetId:///M:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings(System.String[])?qualifyHint=False&autoUpgrade=True).  
  
-   Dois novos métodos na classe [System.Web.HttpCacheVaryByHeaders](assetId:///T:System.Web.HttpCacheVaryByHeaders?qualifyHint=True&autoUpgrade=True): [GetHeaders](assetId:///M:System.Web.HttpCacheVaryByHeaders.GetHeaders?qualifyHint=False&autoUpgrade=True) e [SetHeaders](assetId:///M:System.Web.HttpCacheVaryByHeaders.SetHeaders(System.String[])?qualifyHint=False&autoUpgrade=True).  
  
-   Dois novos métodos na classe [System.Web.HttpCacheVaryByParams](assetId:///T:System.Web.HttpCacheVaryByParams?qualifyHint=True&autoUpgrade=True): [GetParams](assetId:///M:System.Web.HttpCacheVaryByParams.GetParams?qualifyHint=False&autoUpgrade=True) e [SetParams](assetId:///M:System.Web.HttpCacheVaryByParams.SetParams(System.String[])?qualifyHint=False&autoUpgrade=True).  
  
-   Na classe [System.Web.Caching.AggregateCacheDependency](assetId:///T:System.Web.Caching.AggregateCacheDependency?qualifyHint=True&autoUpgrade=True), o método [GetFileDependencies](assetId:///M:System.Web.Caching.AggregateCacheDependency.GetFileDependencies?qualifyHint=False&autoUpgrade=True).  
  
-   Em [CacheDependency](assetId:///T:System.Web.Caching.CacheDependency?qualifyHint=False&autoUpgrade=True), o método [GetFileDependencies](assetId:///M:System.Web.Caching.CacheDependency.GetFileDependencies?qualifyHint=False&autoUpgrade=True).  
  
<a name="Strings"></a>   
### <a name="character-categories"></a>Categorias de caractere  
 Os caracteres no .NET Framework 4.6.2 são classificadas com base no [Padrão Unicode, versão 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/). No .NET Framework 4.6 e no .NET Framework 4.6.1, os caracteres foram classificados com base nas categorias de caracteres do Unicode 6.3.  
  
 O suporte para o Unicode 8.0 é limitado à classificação de caracteres pela classe [CharUnicodeInfo](assetId:///T:System.Globalization.CharUnicodeInfo?qualifyHint=False&autoUpgrade=True) e para tipos e métodos que dependem dela. Entre elas está a classe [StringInfo](assetId:///T:System.Globalization.StringInfo?qualifyHint=False&autoUpgrade=True), o método [Char.GetUnicodeCategory](assetId:///M:System.Char.GetUnicodeCategory(System.Char)?qualifyHint=True&autoUpgrade=True) sobrecarregado e as [classes de caracteres](../Topic/Character%20Classes%20in%20Regular%20Expressions.md) reconhecidas pelo mecanismo de expressões regulares do .NET Framework.  A comparação e a classificação de caracteres e cadeia de caracteres não são afetadas por essa alteração e continuam a depender do sistema operacional subjacente ou, em sistemas com Windows 7, em dados de caracteres fornecidos pelo .NET Framework.  
  
 Para alterações nas categorias de caracteres do Unicode 6.0 para Unicode 7.0, confira [O padrão Unicode, versão 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) no site The Unicode Consortium. Para alterações do Unicode 7.0 para Unicode 8.0, confira [O padrão Unicode, versão 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) no site The Unicode Consortium.  
  
<a name="Crypto462"></a>   
### <a name="cryptography"></a>Criptografia  
 **Suporte para certificados X509 contendo um DSA FIPS 186-3**  
 O .NET Framework 4.6.2 adiciona suporte a certificados DSA (Algoritmo de Assinatura Digital) X509 cujas chaves ultrapassam o limite de 1024 bits do FIPS 186-2.  
  
 Além de oferecer suporte a chaves maiores de FIPS 186-3, o .NET Framework 4.6.2 permite assinaturas de computação com a família SHA-2 de algoritmos de hash (SHA256, SHA384 e SHA512). O suporte ao FIPS 186-3 é fornecido pela nova classe [System.Security.Cryptography.DSACng](assetId:///T:System.Security.Cryptography.DSACng?qualifyHint=True&autoUpgrade=True).  
  
 Para acompanhar as alterações recentes na classe [RSA](assetId:///T:System.Security.Cryptography.RSA?qualifyHint=False&autoUpgrade=True) no .NET Framework 4.6, e na classe [ECDsa](assetId:///T:System.Security.Cryptography.ECDsa?qualifyHint=False&autoUpgrade=True) no .NET Framework 4.6.1, a classe base abstrata [DSA](assetId:///T:System.Security.Cryptography.DSA?qualifyHint=False&autoUpgrade=True) no .NET Framework 4.6.2 tem métodos adicionais que permitem aos chamadores usar essa funcionalidade sem conversão. Você pode chamar o método de extensão [DSACertificateExtensions.GetDSAPrivateKey](assetId:///M:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?qualifyHint=True&autoUpgrade=True) para assinar dados, como mostra o exemplo a seguir.  
  
```csharp  
  
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPrivateKey())  
    {  
        return dsa.SignData(data, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()  
    Using DSA As DSA = cert.GetDSAPrivateKey()  
        Return DSA.SignData(data, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 E você pode chamar o método de extensão [DSACertificateExtensions.GetDSAPublicKey](assetId:///M:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?qualifyHint=True&autoUpgrade=True) para verificar dados assinados, como mostra o exemplo a seguir.  
  
```csharp  
  
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPublicKey())  
    {  
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```  
  
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean  
    Using dsa As DSA = cert.GetDSAPublicKey()  
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 **Maior clareza para as entradas nas rotinas de derivação de chaves ECDiffieHellman**  
 O .NET Framework 3.5 adicionou suporte para o Acordo de chave Diffie-Hellman de curva elíptica com três rotinas KDF (Função de derivação de chaves) diferentes. As entradas para as rotinas, e as próprias rotinas, foram configuradas por meio de propriedades no objeto [ECDiffieHellmanCng](assetId:///T:System.Security.Cryptography.ECDiffieHellmanCng?qualifyHint=False&autoUpgrade=True). Mas como nem toda rotina lia cada propriedade de entrada, havia muita margem para confusão do desenvolvedor.  
  
 Para lidar com isso no .NET Framework 4.6.2, os três métodos a seguir foram adicionados à classe base [ECDiffieHellman](assetId:///T:System.Security.Cryptography.ECDiffieHellman?qualifyHint=False&autoUpgrade=True) para representar mais claramente essas rotinas KDF e suas entradas:  
  
|Método ECDiffieHellman|Descrição|  
|----------------------------|-----------------|  
|[DeriveKeyFromHash(ECDiffieHellmanPublicKey, HashAlgorithmName, Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Security.Cryptography.HashAlgorithmName,System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|Deriva o material da chave usando a fórmula<br /><br /> HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> em que *x* é o resultado calculado do algoritmo EC Diffie-Hellman.|  
|[DeriveKeyFromHmac(ECDiffieHellmanPublicKey, HashAlgorithmName, Byte\[\], Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Security.Cryptography.HashAlgorithmName,System.Byte[],System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|Deriva o material da chave usando a fórmula<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> em que *x* é o resultado calculado do algoritmo EC Diffie-Hellman.|  
|[DeriveKeyTls(ECDiffieHellmanPublicKey, Byte\[\], Byte\[\])](assetId:///M:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls(System.Security.Cryptography.ECDiffieHellmanPublicKey,System.Byte[],System.Byte[])?qualifyHint=False&autoUpgrade=False)|Deriva o material da chave usando o algoritmo de derivação PRF (Função pseudoaleatória) TLS.|  
  
 **Suporte para criptografia simétrica de chave persistida**  
 A biblioteca de criptografia do Windows (CNG) adicionou suporte para o armazenamento de chaves simétricas persistidas e para o uso de chaves simétricas armazenadas em hardware, e o .NET Framework 4.6.2 possibilita aos desenvolvedores o uso desse recurso.  Como a noção de nomes e provedores de chave é específica à implementação, o uso desse recurso exige a utilização do construtor dos tipos de implementação concreta em vez da abordagem preferencial de fábrica (por exemplo, chamar `Aes.Create`).  
  
 O suporte à criptografia simétrica de chave persistente existe para os algoritmos AES ([AesCng](assetId:///T:System.Security.Cryptography.AesCng?qualifyHint=False&autoUpgrade=True)) e 3DES ([TripleDESCng](assetId:///T:System.Security.Cryptography.TripleDESCng?qualifyHint=False&autoUpgrade=True)). Por exemplo:  
  
```csharp  
  
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)  
{  
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))  
    {  
        aes.IV = iv;  
  
        // Using the zero-argument overload is required to make use of the persisted key  
        using (ICryptoTransform encryptor = aes.CreateEncryptor())  
        {  
            if (!encryptor.CanTransformMultipleBlocks)  
            {  
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");  
            }  
  
            return encryptor.TransformFinalBlock(data, 0, data.Length);  
        }  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()  
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)  
        Aes.IV = iv  
  
        ' Using the zero-argument overload Is required to make use of the persisted key  
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()  
            If Not encryptor.CanTransformMultipleBlocks Then  
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")  
            End If  
            Return encryptor.TransformFinalBlock(data, 0, data.Length)  
        End Using  
    End Using  
End Function  
  
```  
  
 **Suporte a SignedXml para hash SHA-2**  
 O .NET Framework 4.6.2 adiciona o suporte à classe [SignedXml](assetId:///T:System.Security.Cryptography.Xml.SignedXml?qualifyHint=False&autoUpgrade=True) para os métodos de assinatura PKCS#1 RSA-SHA256, RSA-SHA384 e RSA-SHA512, e os algoritmos de resumo de referência SHA256, SHA384 e SHA512.  
  
 As constantes de URI são expostas em [SignedXml](xref:System.Security.Cryptography.Xml.SignedXml?qualifyHint=False&autoUpgrade=True):  
  
|Campo SignedXml|Constante|  
|---------------------|--------------|  
|[XmlDsigSHA256Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmlenc#sha256"|  
|[XmlDsigRSASHA256Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|  
|[XmlDsigSHA384Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#sha384"|  
|[XmlDsigRSASHA384Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|  
|[XmlDsigSHA512Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmlenc#sha512"|  
|[XmlDsigRSASHA512Url](assetId:///F:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url?qualifyHint=False&autoUpgrade=True)|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|  
  
 Todos os programas que registraram um manipulador [SignatureDescription](assetId:///T:System.Security.Cryptography.SignatureDescription?qualifyHint=False&autoUpgrade=True) personalizado em [CryptoConfig](assetId:///T:System.Security.Cryptography.CryptoConfig?qualifyHint=False&autoUpgrade=True) para adicionar suporte a esses algoritmos continuarão a funcionar como antes, mas como agora há padrões de plataforma, o registro de [CryptoConfig](assetId:///T:System.Security.Cryptography.CryptoConfig?qualifyHint=False&autoUpgrade=True) não é mais necessário.  
  
<a name="SQLClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 O provedor de dados .NET Framework para SQL Server ([System.Data.SqlClient](assetId:///N:System.Data.SqlClient?qualifyHint=True&autoUpgrade=True)) inclui os seguintes recursos novos no .NET Framework 4.6.2:  
  
 **Pooling de conexão e tempos limite com bancos de dados SQL do Azure**  
 Quando o pooling de conexão estiver habilitado e ocorrer um tempo limite ou outro erro de logon, uma exceção será armazenada em cache, e a exceção em cache será lançada em qualquer tentativa de conexão subsequentes nos próximos cinco segundos a um minuto.  Para obter mais detalhes, confira [Pooling de conexão do SQL Server (ADO.NET)](../Topic/SQL%20Server%20Connection%20Pooling%20\(ADO.NET\).md).  
  
 Esse comportamento não é desejável ao se conectar a Bancos de Dados SQL do Azure, uma vez que as tentativas de conexão podem falhar com erros transitórios que normalmente são recuperados rapidamente. Para otimizar melhor a experiência de repetição de conexão, o comportamento do período de bloqueio do pool conexão é removido quando as conexões com os Bancos de Dados SQL do Azure falham.  
  
 A adição da nova palavra-chave `PoolBlockingPeriod` permite que você selecione o período de bloqueio mais adequado para seu aplicativo. Os valores são:  
  
 `Auto`  
 O período de bloqueio do pool de conexão de um aplicativo que se conecta a um Banco de Dados SQL do Azure está desabilitado, e período de bloqueio do pool de conexão de um aplicativo que se conecta a qualquer outra instância do SQL Server está habilitado. Este é o valor padrão. Se o nome de ponto de extremidade do Servidor terminar com qualquer uma das seguintes opções, será considerado um Banco de Dado SQL do Azure:  
  
-   .database.windows.net  
  
-   .database.chinacloudapi.cn  
  
-   .database.usgovcloudapi.net  
  
-   .database.cloudapi.de  
  
 `AlwaysBlock`  
 O período de bloqueio do pool de conexão está sempre habilitado.  
  
 `NeverBlock`  
 O período de bloqueio do pool de conexão está sempre desabilitado.  
  
 **Aprimoramentos para Always Encrypted**  
 O SQLClient apresenta dois aprimoramentos para Always Encrypted:  
  
-   Agora, para melhorar o desempenho de consultas parametrizadas em colunas de banco de dados criptografadas, os metadados de criptografia para parâmetros de consulta são armazenado em cache. Com a propriedade [SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled](assetId:///P:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled?qualifyHint=True&autoUpgrade=True) definida como `true` (que é o valor padrão), se a mesma consulta for chamada várias vezes, o cliente recuperará metadados de parâmetro do servidor somente uma vez.  
  
-   As entradas de chave de criptografia da coluna no cache de chave são removidas após um intervalo de tempo configurável, definido usando a propriedade [SqlConnection.ColumnEncryptionKeyCacheTtl](assetId:///P:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl?qualifyHint=True&autoUpgrade=True).  
  
<a name="WCF"></a>   
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 No .NET Framework 4.6.2, o Windows Communication Foundation foi aprimorado nas seguintes áreas:  
  
 **Suporte à segurança de transporte do WCF para certificados armazenados usando CNG**  
 A segurança de transporte do WCF dá suporte a certificados armazenados usando a biblioteca de criptografia do Windows (CNG). No .NET Framework 4.6.2, esse suporte é limitado ao uso de certificados com uma chave pública que tenha um expoente não superior a 32 bits de comprimento. Quando um aplicativo é direcionado ao .NET Framework 4.6.2, esse recurso é ativado por padrão.  
  
 Para aplicativos direcionados ao .NET Framework 4.6.1 e versões anteriores, mas que são executados no .NET Framework 4.6.2 ou posterior, esse recurso pode ser habilitado adicionando a seguinte linha à seção [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) do arquivo app.config ou web.config.  
  
```xml  
  
<AppContextSwitchOverrides  
    value="Switch.System.ServiceModel.DisableCngCertificates=false"  
/>  
  
```  
  
 Isso também pode ser feito de modo programático com um código como o seguinte:  
  
```csharp  
  
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";  
AppContext.SetSwitch(disableCngCertificates, false);  
  
```  
  
```vb  
  
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"  
AppContext.SetSwitch(disableCngCertificates, False)  
  
```  
  
 **Melhor suporte para várias regras de ajuste de horário de verão pela classe DataContractJsonSerializer**  
 Os clientes podem usar uma configuração de aplicativo para determinar se a classe [DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) oferece suporte a várias regras de ajuste para um único fuso horário. Esse é um recurso de opção de aceitação. Para habilitá-lo, adicione a seguinte configuração ao arquivo app.config:  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />  
</runtime>  
  
```  
  
 Quando esse recurso estiver habilitado, um objeto [DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) usará o tipo [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) em vez do [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) para desserializar dados de data e hora. O [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) oferece suporte a várias regras de ajuste, o que possibilita o trabalho com dados históricos fuso horário; o [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) não oferece.  
  
 Para saber mais sobre a estrutura [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) e ajustes de fuso horário, confira [Visão geral do fuso horário](../Topic/Time%20Zone%20Overview.md).  
  
 **Suporte para preservar um horário UTC ao serializar e desserializar com a classe XMLSerializer**  
 Normalmente, quando a classe [XmlSerializer](assetId:///T:System.Xml.Serialization.XmlSerializer?qualifyHint=False&autoUpgrade=True) é usada para serializar um valor de [DateTime](assetId:///T:System.DateTime?qualifyHint=False&autoUpgrade=True) UTC, ela cria uma cadeia de caracteres serializada de tempo que preserva a data e hora, mas pressupõe que o horário é local.  Por exemplo, se você criar uma instância de uma data e hora UTC chamando o código a seguir:  
  
```csharp  
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);  
```  
  
```vb  
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)  
```  
  
 o resultado será a cadeia de caracteres de tempo serializado "03:00:00.0000000-08:00" para um sistema de oito horas atrás do UTC.  E valores serializados sempre são desserializados como valores de hora e data locais.  
  
 Use uma configuração de aplicativo para determinar se o [XmlSerializer](assetId:///T:System.Xml.Serialization.XmlSerializer?qualifyHint=False&autoUpgrade=True) preserva informações de fuso horário UTC ao serializar e desserializar valores de [DateTime](assetId:///T:System.DateTime?qualifyHint=False&autoUpgrade=True):  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides   
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />  
</runtime>  
  
```  
  
 Quando esse recurso estiver habilitado, um objeto [DataContractJsonSerializer](assetId:///T:System.Runtime.Serialization.Json.DataContractJsonSerializer?qualifyHint=False&autoUpgrade=True) usará o tipo [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) em vez do [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) para desserializar dados de data e hora. O [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) oferece suporte a várias regras de ajuste, o que possibilita o trabalho com dados históricos fuso horário; o [TimeZone](assetId:///T:System.TimeZone?qualifyHint=False&autoUpgrade=True) não oferece.  
  
 Para saber mais sobre a estrutura [TimeZoneInfo](assetId:///T:System.TimeZoneInfo?qualifyHint=False&autoUpgrade=True) e ajustes de fuso horário, confira [Visão geral do fuso horário](../Topic/Time%20Zone%20Overview.md).  
  
 **Melhor correspondência de NetNamedPipeBinding**  
 O WCF possui uma nova configuração de aplicativo que pode ser definida em aplicativos cliente para garantir que eles sempre se conectem ao serviço escutando no URI mais próximo ao solicitado. Com essa configuração de aplicativo definida como `false` (padrão), os clientes podem usar [NetNamedPipeBinding](assetId:///T:System.ServiceModel.NetNamedPipeBinding?qualifyHint=False&autoUpgrade=True) para tentar se conectar a um serviço escutando em um URI que é uma subcadeia de caracteres do URI solicitado.  
  
 Por exemplo, um cliente tenta se conectar a um serviço escutando em `net.pipe://localhost/Service1`, mas um serviço diferente nessa máquina que está executando com privilégios de administrador está escutando em `net.pipe://localhost`. Com essa configuração de aplicativo definida como `false`, o cliente tentaria se conectar ao serviço errado. Depois de definir a configuração do aplicativo como `true`, o cliente sempre se conectará ao serviço com correspondência mais próxima.  
  
> [!NOTE]
>  Os clientes que usam [NetNamedPipeBinding](assetId:///T:System.ServiceModel.NetNamedPipeBinding?qualifyHint=False&autoUpgrade=True) localizam serviços com base no endereço base do serviço (se ele existir) em vez do endereço de ponto de extremidade completo. Para garantir sempre o funcionamento dessa configuração o serviço deve usar um endereço base exclusivo.  
  
 Para habilitar essa alteração, adicione a seguinte configuração de aplicativo ao arquivo app.config ou web.config de seu aplicativo cliente:  
  
```xml  
  
<configuration>  
    <appSettings>  
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />  
    </appSettings>  
</configuration>  
  
```  
  
 **SSL 3.0 não é um protocolo padrão**  
 Ao usar NetTcp com segurança de transporte e um tipo de credencial de certificado, o SSL 3.0 não é mais um protocolo padrão usado para negociar uma conexão segura. Na maioria dos casos, não deve haver impacto nos aplicativos existentes, pois o TLS 1.0 está incluído na lista de protocolos para NetTcp. Todos os clientes existentes devem ser capazes de negociar uma conexão usando no mínimo o TLS 1.0.      Se Ssl3 for exigido, use um dos seguintes mecanismos de configuração para adicioná-lo à lista de protocolos negociados.  
  
-   A propriedade [SslStreamSecurityBindingElement.SslProtocols](assetId:///P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?qualifyHint=True&autoUpgrade=True)  
  
-   A propriedade [TcpTransportSecurity.SslProtocols](assetId:///P:System.ServiceModel.TcpTransportSecurity.SslProtocols?qualifyHint=True&autoUpgrade=True)  
  
-   A seção [\<transport>](../Topic/%3Ctransport%3E%20of%20%3CnetTcpBinding%3E.md) da seção [\<netTcpBinding>](../Topic/%3CnetTcpBinding%3E.md)  
  
-   A seção [\<sslStreamSecurity>](../Topic/%3CsslStreamSecurity%3E.md) da seção [\<customBinding>](../Topic/%3CcustomBinding%3E.md)  
  
<a name="WPF462"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 No .NET Framework 4.6.2, o Windows Presentation Foundation foi aprimorado nas seguintes áreas:  
  
 **Classificação de grupo**  
 Um aplicativo que usa um objeto [CollectionView](assetId:///T:System.Windows.Data.CollectionView?qualifyHint=False&autoUpgrade=True) para agrupar dados agora pode declarar explicitamente como classificar os grupos. A classificação explícita resolve o problema de ordens não intuitivas que ocorrem quando um aplicativo adiciona ou remove grupos dinamicamente, ou quando ele altera o valor das propriedades do item envolvidas no agrupamento. Ela também pode melhorar o desempenho do processo de criação de grupo mudando comparações das propriedades de agrupamento da classificação da coleção inteira para a classificação dos grupos.  
  
 Para oferecer suporte à classificação de grupo, as novas propriedades [GroupDescription.SortDescriptions](assetId:///P:System.ComponentModel.GroupDescription.SortDescriptions?qualifyHint=True&autoUpgrade=True) e [GroupDescription.CustomSort](assetId:///P:System.ComponentModel.GroupDescription.CustomSort?qualifyHint=True&autoUpgrade=True) descrevem como classificar a coleção de grupos produzida pelo objeto [GroupDescription](assetId:///T:System.ComponentModel.GroupDescription?qualifyHint=False&autoUpgrade=True). Isso é semelhante à forma como as propriedades [ListCollectionView](assetId:///T:System.Windows.Data.ListCollectionView?qualifyHint=False&autoUpgrade=True) de nome idêntico descrevem como classificar os itens de dados.  
  
 Duas novas propriedades estáticas da classe [PropertyGroupDescription](assetId:///T:System.Windows.Data.PropertyGroupDescription?qualifyHint=False&autoUpgrade=True), [CompareNameAscending](assetId:///P:System.Windows.Data.PropertyGroupDescription.CompareNameAscending?qualifyHint=False&autoUpgrade=True) e [CompareNameDescending](assetId:///P:System.Windows.Data.PropertyGroupDescription.CompareNameDescending?qualifyHint=False&autoUpgrade=True), podem ser usadas para os casos mais comuns.  
  
 Por exemplo, os seguintes dados de grupos XAML por idade, classificam as faixas etárias em ordem crescente, e agrupam os itens dentro de cada faixa etária por sobrenome.  
  
```xaml  
  
<GroupDescriptions>  
     \<PropertyGroupDescription   
         PropertyName=”Age”   
         CustomSort=   
              ”{x:Static PropertyGroupDescription.CompareNamesAscending}”/>  
     </PropertyGroupDescription>  
</GroupDescriptions>  
  
<SortDescriptions>  
     \<SortDescription PropertyName=”LastName”/>  
</SortDescriptions>  
  
```  
  
 **Suporte ao teclado virtual**  
 O suporte ao teclado virtual permite o acompanhamento de foco em aplicativos WPF invocando e ignorando automaticamente o novo Teclado Virtual no Windows 10 quando a entrada de toque for recebida por um controle que aceita entrada textual.  
  
 Nas versões anteriores do .NET Framework, os aplicativos WPF não podiam aceitar o acompanhamento de foco sem desabilitar o suporte a gestos caneta/toque do WPF.  Como resultado, os aplicativos WPF devem escolher entre o suporte total a toque do WPF ou depender da promoção de mouse do Windows.  
  
 **DPI por monitor**  
 Para dar suporte à recente proliferação de ambientes com alto DPI e DPI híbrido para aplicativos WPF, o WPF no .NET Framework 4.6.2 permite o reconhecimento por monitor. Confira [Exemplos e guia do desenvolvedor](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) no GitHub para saber mais sobre como habilitar seu aplicativo WPF para ter o reconhecimento do DPI por monitor.  
  
 Nas versões anteriores do .NET Framework, os aplicativos WPF tinha reconhecimento de DPI do sistema. Em outras palavras, a interface do usuário do aplicativo é dimensionado adequadamente pelo sistema operacional, dependendo do DPI do monitor no qual o aplicativo é renderizado. ,  
  
 Para aplicativos em execução no .NET Framework 4.6.2, você pode desabilitar as alterações de DPI por monitor em aplicativos WPF adicionando uma instrução de configuração à seção [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) do arquivo de configuração do aplicativo, da seguinte maneira:  
  
```xml  
  
<runtime>  
   \<AppContextSwitchOverrides value=”Switch.System.Windows.DoNotScaleForDpiChanges=false”/>  
</runtime>  
  
```  
  
<a name="WF462"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 No .NET Framework 4.6.2, o Windows Workflow Foundation foi aprimorado na seguinte área:  
  
 **Suporte para expressões em C# e IntelliSense no Designer do WF hospedado novamente**  
 A partir do .NET Framework 4.5, o WF oferece suporte a expressões em C# no Designer do Visual Studio e em fluxos de trabalho de código. O Designer de Fluxo de Trabalho hospedado novamente é um recurso fundamental do WF que permite ao Designer de Fluxo de Trabalho estar em um aplicativo fora do Visual Studio (por exemplo, no WPF).  O Windows Workflow Foundation permite o suporte às expressões em C# e ao IntelliSense no Designer de Fluxo de Trabalho hospedado novamente. Para saber mais, confira o [blog do Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).  
  
 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`  
 Nas versões do .NET Framework anteriores ao .NET Framework 4.6.2, o IntelliSense de Designer do WF é interrompido quando um cliente recompila um projeto de fluxo de trabalho a partir do Visual Studio. Embora a compilação do projeto seja bem-sucedida, os tipos de fluxo de trabalho não são encontrados no designer, e surgem avisos do IntelliSense para os tipos de fluxo de trabalho ausentes na janela **Lista de Erros**. O .NET Framework 4.6.2 resolve esse problema e disponibiliza o IntelliSense.  
  
 **Agora, os aplicativos do Fluxo de Trabalho V1 com Acompanhamento de Fluxo de Trabalho ativado são executados no modo FIPS**  
 Máquinas com o Modo de Conformidade FIPS habilitado podem executar um aplicativo no estilo Fluxo de trabalho versão 1 com o acompanhamento de Fluxo de trabalho ativado. Para habilitar esse cenário, faça a seguinte alteração em seu arquivo app.config:  
  
```xml  
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />  
```  
  
 Se esse cenário não estiver habilitado, a execução do aplicativo continuará a gerar uma exceção com a mensagem "Esta implementação não faz parte dos algoritmos criptográficos validados por FIPS da Plataforma Windows".  
  
 **Aprimoramentos de fluxo de trabalho ao usar a Atualização Dinâmica com o Designer de Fluxo de Trabalho do Visual Studio**  
 Agora, o Designer de Fluxo de Trabalho, o Designer de Atividade do Fluxograma e outros Designers de Atividade de Fluxo de Trabalho carregam e exibem com êxito os fluxos de trabalho que foram salvos depois de chamar o método [DynamicUpdateServices.PrepareForUpdate](assetId:///M:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate(System.Activities.Activity)?qualifyHint=True&autoUpgrade=True). Nas versões do .NET Framework anteriores ao .NET Framework 4.6.2, carregar um arquivo XAML no Visual Studio para um fluxo de trabalho que foi salvo após chamar [DynamicUpdateServices.PrepareForUpdate](assetId:///M:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate(System.Activities.Activity)?qualifyHint=True&autoUpgrade=True) pode resultar nos seguintes problemas:  
  
-   O Designer de Fluxo de Trabalho não consegue carregar o arquivo XAML corretamente (quando [ViewStateData.Id](assetId:///P:System.Activities.Presentation.ViewState.ViewStateData.Id?qualifyHint=True&autoUpgrade=True) está no final da linha).  
  
-   O Designer de Atividades do Fluxograma ou outros Designers de Atividade de Fluxo de Trabalho podem exibir todos os objetos em seus locais padrão em vez de valores de propriedade anexados.  
  
<a name="ClickOnce"></a>   
### <a name="clickonce"></a>ClickOnce  
 O ClickOnce foi atualizado para oferecer suporte a TLS 1.1 e o TLS 1.2, além do protocolo 1.0, para o qual ele já oferece suporte. O ClickOnce detecta automaticamente qual protocolo é necessário; não é necessário executar nenhuma etapa adicional dentro do aplicativo ClickOnce para habilitar o suporte ao TLS 1.1 e 1.2.  
  
<a name="UWPConvert"></a>   
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Converter aplicativos do Windows Forms e do WPF em aplicativos UWP  
 Agora, o Windows oferece recursos para levar aplicativos existentes da área de trabalho do Windows, incluindo aplicativos do Windows Forms e WPF, para a plataforma Universal do Windows (UWP). Essa tecnologia age como uma ponte, permitindo que você migre gradualmente sua base de código existente para a UWP, levando seu aplicativo para todos os dispositivos com Windows 10.  
  
 Os aplicativos da área de trabalho convertidos ganham uma identidade de aplicativo semelhante à identidade de aplicativo de aplicativos da UWP, o que torna as APIs da UWP acessíveis para habilitar recursos como Blocos Dinâmicos e notificações. O aplicativo continua a se comportar como antes e é executado como um aplicativo de confiança total. Após a conversão do aplicativo, um processo de contêiner do aplicativo pode ser adicionado ao processo de confiança total existente a fim de adicionar uma interface do usuário adaptável. Quando toda a funcionalidade for movida para o processo de contêiner do aplicativo, o processo de confiança total poderá ser removido, e o novo aplicativo UWP poderá ser disponibilizado para todos os dispositivos com Windows 10.  
  
<a name="Debug462"></a>   
### <a name="debugging-improvements"></a>Melhorias na depuração  
 A *API de depuração não gerenciada* foi aprimorada no .NET Framework 4.6.2 para executar análises adicionais quando um [NullReferenceException](assetId:///T:System.NullReferenceException?qualifyHint=False&autoUpgrade=True) for gerada, para que seja possível determinar qual variável em uma única linha do código-fonte é `null`.   Para oferecer suporte a esse cenário, as seguintes APIs foram adicionadas à API de depuração não gerenciada.  
  
-   As interfaces [ICorDebugCode4](../Topic/ICorDebugCode4%20Interface.md), [ICorDebugVariableHome](../Topic/ICorDebugVariableHome%20Interface.md) e [ICorDebugVariableHomeEnum](../Topic/ICorDebugVariableHomeEnum%20Interface.md), que expõem os locais nativos das variáveis gerenciadas. Isso permite que os depuradores façam algumas análises de fluxo de código quando uma [NullReferenceException](assetId:///T:System.NullReferenceException?qualifyHint=False&autoUpgrade=True) ocorrer e trabalhem com versões anteriores para determinar a variável gerenciada que corresponde ao local nativo no qual estava `null`.  
  
-   O método [ICorDebugType2::GetTypeID](../Topic/ICorDebugType2::GetTypeID%20Method.md) fornece um mapeamento para ICorDebugType para [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md), que permite que o depurador obtenha um [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md) sem uma instância do ICorDebugType. APIs existentes em [COR_TYPEID](../Topic/COR_TYPEID%20Structure.md) podem ser usadas para determinar o layout de classe do tipo.  
  
<a name="v461"></a>   
## <a name="whats-new-in-the-net-framework-461"></a>Novidades no .NET Framework 4.6.1  
 O .NET Framework 4.6.1 inclui novos recursos nas seguintes áreas:  
  
-   [Criptografia](#Crypto)  
  
-   [ADO.NET](#ADO.NET461)  
  
-   [Windows Presentation Foundation (WPF)](#WPF461)  
  
-   [Windows Workflow Foundation](#WWF461)  
  
-   [Criação de perfil](#Profile461)  
  
-   [NGen](#NGEN461)  
  
 Para saber mais sobre o .NET Framework 4.6.1, consulte os seguintes tópicos:  
  
-   A [Lista de alterações no .NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkId=622964)  
  
-   [Compatibilidade de aplicativos no 4.6.1](../Topic/Application%20Compatibility%20in%20the%20.NET%20Framework%204.6.1.md)  
  
-   [A comparação da API do .NET Framework](http://go.microsoft.com/fwlink/?LinkId=622989) (no GitHub)  
  
<a name="Crypto"></a>   
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Criptografia: suporte para certificados X509 contendo ECDSA  
 O .NET Framework 4.6 adicionou o suporte a RSACng para certificados X509. O .NET Framework 4.6.1 adiciona suporte para certificados X509 ECDSA (Algoritmo de Assinatura Digital de Curva Elíptica).  
  
 O ECDSA oferece melhor desempenho e é um algoritmo de criptografia mais seguro do que o RSA, fornecendo uma excelente opção quando o desempenho e a escalabilidade de TLS (Transport Layer Security) forem uma preocupação. A implementação do .NET Framework envolve chamadas para funcionalidades existentes do Windows.  
  
 O exemplo de código a seguir mostra como é fácil gerar uma assinatura para um fluxo de bytes usando o novo suporte para certificados X509 ECDSA incluídos no .NET Framework 4.6.1.  
  
<!-- TODO: review snippet reference  [!CODE [whatsnew.461.crypto#1](../CodeSnippet/VS_Snippets_CLR/whatsnew.461.crypto#1)]  -->  
  
 Isso oferece um contraste evidente ao código necessário para gerar uma assinatura no .NET Framework 4.6.  
  
<!-- TODO: review snippet reference  [!CODE [whatsnew.461.crypto#2](../CodeSnippet/VS_Snippets_CLR/whatsnew.461.crypto#2)]  -->  
  
<a name="ADO.NET461"></a>   
### ADO.NET Os itens a seguir foram adicionados ao ADO.NET:  
  
 Suporte a Always Encrypted para chaves protegidas por hardware  
 Agora, o ADO.NET oferece suporte ao armazenamento nativo de chaves mestras de coluna do Always Encrypted em HSMs (Módulos de segurança de Hardware). Com esse suporte, os clientes podem aproveitar as chaves assimétricas armazenadas em HSMs sem ter que escrever provedores de armazenamento de chave mestra de coluna personalizados e registrá-los nos aplicativos.  
  
 Os clientes precisam instalar o provedor de CSP fornecido pelo fornecedor de HSM ou provedores de armazenamento de chaves CNG em servidores de aplicativos ou computadores cliente para acessar dados do Always Encrypted protegidos com chaves mestras de coluna armazenadas em um HSM.  
  
 Melhorar o comportamento de conexão de [MultiSubnetFailover](assetId:///P:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover?qualifyHint=False&autoUpgrade=True) para o AlwaysOn  
 Agora, o SqlClient fornece automaticamente uma conexão mais rápida para um Grupo de disponibilidade (AG) do AlwaysOn. Ele detecta de forma transparente se o seu aplicativo está se conectando a um grupo de disponibilidade (AG) do AlwaysOn em uma sub-rede diferente e descobre rapidamente o servidor ativo atual e fornece uma conexão ao servidor. Antes dessa versão, um aplicativo tinha que definir a cadeia de conexão para incluir `“MultisubnetFailover=true”` a fim de indicar que ele estava se conectando a um Grupo de disponibilidade do AlwaysOn. Sem definir a palavra-chave de conexão como `true`, um aplicativo pode enfrentar um tempo limite ao se conectar a um Grupo de disponibilidade AlwaysOn. Com esta versão, um aplicativo *não* precisa mais definir [MultiSubnetFailover](assetId:///P:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover?qualifyHint=False&autoUpgrade=True) como `true`. Para saber mais sobre o suporte ao SqlClient para Grupos de Disponibilidade AlwaysOn, confira [Suporte do SqlClient para alta disponibilidade e recuperação de desastres](../Topic/SqlClient%20Support%20for%20High%20Availability,%20Disaster%20Recovery.md).  
  
<a name="WPF461"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Windows Presentation Foundation inclui diversos aprimoramentos e alterações.  
  
 Desempenho aprimorado  
 O atraso em disparar eventos de toque foi corrigido no .NET Framework 4.6.1. Além disso, a digitação de controle [RichTextBox](assetId:///T:System.Windows.Controls.RichTextBox?qualifyHint=False&autoUpgrade=True) não ocupa mais o thread de renderização durante a entrada rápida.  
  
 Aprimoramentos na verificação ortográfica  
 O verificador ortográfico do WPF foi atualizado no Windows 8.1 e em versões posteriores para aproveitar o suporte ao sistema operacional para verificação ortográfica de outros idiomas.  Não há nenhuma alteração na funcionalidade em versões do Windows anteriores ao Windows 8.1.  
  
 Como nas versões anteriores do .NET Framework, o idioma para um controle [TextBox](assetId:///T:System.Windows.Controls.TextBox?qualifyHint=False&autoUpgrade=True) ou um bloco [RichTextBox](assetId:///T:System.Windows.Controls.RichTextBox?qualifyHint=False&autoUpgrade=True) é detectado procurando por informações na seguinte ordem:  
  
-   `xml:lang`, se estiver presente.  
  
-   Idioma de entrada atual.  
  
-   Cultura do thread atual.  
  
 Para saber mais sobre o suporte de idiomas no WPF, confira a [postagem de blog do WPF sobre recursos do .NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkID=691819).  
  
 Suporte adicional para dicionários personalizados por usuário  
 No .NET Framework 4.6.1, o WPF reconhece os dicionários personalizados registrados globalmente. Esse recurso está disponível além da capacidade de registrá-los por controle.  
  
 Nas versões anteriores do WPF, os dicionários personalizados não reconheciam as listas de Palavras Excluídas e de Autocorreção. Elas têm suporte no Windows 8.1 e no Windows 10 com o uso de arquivos que podem ser colocados no diretório `%AppData%\Microsoft\Spelling\<language tag>`.  As regras a seguir se aplicam a estes arquivos:  
  
-   Os arquivos devem ter extensões .dic (para palavras adicionadas), .exc (para palavras excluídas) ou .acl (para Autocorreção).  
  
-   Os arquivos devem ser em texto sem formatação UTF-16 LE que começa com a marca de ordem de Byte (BOM).  
  
-   Cada linha deve conter uma palavra (nas listas de palavras adicionadas e excluídas) ou um par de autocorreção com as palavras separadas por uma barra vertical ("&#124;") (na lista de palavras de Autocorreção).  
  
-   Esses arquivos são considerados somente leitura e não são modificados pelo sistema.  
  
> [!NOTE]
>  Esses novos formatos de arquivo não recebem suporte diretamente das APIs de verificação ortografia do WPF, e os dicionários personalizados fornecidos ao WPF nos aplicativos devem continuar usando arquivos .lex.  
  
 Exemplos  
 Há uma série de [Exemplos de WPF](https://msdn.microsoft.com/library/ms771633.aspx) no MSDN. Mais de 200 dos exemplos mais populares (com base no uso) serão movidos para um [repositório do GitHub de código-fonte aberto](https://github.com/Microsoft/WPF-Samples). Ajude-nos a melhorar nossos exemplos enviando-nos uma solicitação pull ou abrindo um [problema no GitHub](https://github.com/Microsoft/WPF-Samples/issues).  
  
 Extensões do DirectX  
 O WPF inclui um [pacote do NuGet](http://go.microsoft.com/fwlink/?LinkID=691342) que fornece novas implementações de [D3DImage](assetId:///T:System.Windows.Interop.D3DImage?qualifyHint=False&autoUpgrade=True) que facilitam a interoperação com o conteúdo do DX10 e Dx11. O código para esse pacote foi aberto e está disponível [no GitHub](https://github.com/Microsoft/WPFDXInterop).  
  
<a name="WWF461"></a>   
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: Transações  
 Agora, o método [Transaction.EnlistPromotableSinglePhase](assetId:///Overload:System.Transactions.Transaction.EnlistPromotableSinglePhase?qualifyHint=True&autoUpgrade=True) pode usar um gerenciador de transação distribuída diferente do MSDTC para promover a transação. Faça isso especificando um identificador de promotor de transação de GUID para a nova sobrecarga [Transaction.EnlistPromotableSinglePhase(IPromotableSinglePhaseNotification, Guid)](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification,System.Guid)?qualifyHint=True&autoUpgrade=False). Se essa operação for bem-sucedida, haverá limitações nos recursos da transação. Após a inscrição do um promotor de transação não MSDTC, os métodos a seguir geram uma [TransactionPromotionException](assetId:///T:System.Transactions.TransactionPromotionException?qualifyHint=False&autoUpgrade=True), pois esses métodos exigem promoção para MSDTC:  
  
-   [Transaction.EnlistDurable](assetId:///Overload:System.Transactions.Transaction.EnlistDurable?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetDtcTransaction](assetId:///M:System.Transactions.TransactionInterop.GetDtcTransaction(System.Transactions.Transaction)?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetExportCookie](assetId:///M:System.Transactions.TransactionInterop.GetExportCookie(System.Transactions.Transaction,System.Byte[])?qualifyHint=True&autoUpgrade=True)  
  
-   [TransactionInterop.GetTransmitterPropagationToken](assetId:///M:System.Transactions.TransactionInterop.GetTransmitterPropagationToken(System.Transactions.Transaction)?qualifyHint=True&autoUpgrade=True)  
  
 Após a inscrição do um promotor de transação não MSDTC, ele deverá ser usado para futuras inscrições duráveis usando os protocolos que definidos por ele. O [Guid](assetId:///T:System.Guid?qualifyHint=False&autoUpgrade=True) do promotor de transação pode ser obtido usando a propriedade [PromoterType](assetId:///P:System.Transactions.Transaction.PromoterType?qualifyHint=False&autoUpgrade=True). Quando transação promove, o promotor da transação fornece uma matriz [Byte](assetId:///T:System.Byte?qualifyHint=False&autoUpgrade=True) que representa o token promovido. Um aplicativo pode obter o token promovido para uma transação promovida não MSDTC com o método [GetPromotedToken](assetId:///M:System.Transactions.Transaction.GetPromotedToken?qualifyHint=False&autoUpgrade=True).  
  
 Os usuários da nova sobrecarga [Transaction.EnlistPromotableSinglePhase(IPromotableSinglePhaseNotification, Guid)](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification,System.Guid)?qualifyHint=True&autoUpgrade=False) devem seguir uma sequência de chamada específica para que a operação de promoção seja concluída com êxito. Essas regras estão na documentação do método.  
  
<a name="Profile461"></a>   
### <a name="profiling"></a>Criação de perfil  
 A API de criação de perfil não gerenciado foi aprimorada da seguinte forma:  
  
 Melhor suporte para acessar PDBs na interface [ICorProfilerInfo7](../Topic/ICorProfilerInfo7%20Interface.md)  
 No ASP.Net 5, está se tornando cada vez mais comum a compilação de assemblies na memória pelo Roslyn. Para os desenvolvedores que estão criando ferramentas de criação de perfil, isso significa que os PDBs que eram serializados historicamente no disco talvez não estejam mais presentes. Normalmente, as ferramentas de criação de perfil usam PDBs para mapear o código de volta para as linhas de origem para tarefas como cobertura de código ou análise de desempenho de linha por linha. A interface [ICorProfilerInfo7](../Topic/ICorProfilerInfo7%20Interface.md) agora inclui dois métodos novos, [ICorProfilerInfo7::GetInMemorySymbolsLength](../Topic/ICorProfilerInfo7::GetInMemorySymbolsLength%20Method.md) e [ICorProfilerInfo7::ReadInMemorySymbols](../Topic/ICorProfilerInfo7::ReadInMemorySymbols.md), a fim de fornecer essas ferramentas de criação de perfil com acesso aos dados de PDB na memória. Com as novas APIs, um criador de perfil pode obter o conteúdo de um PDB na memória como uma matriz de bytes e, em seguida, processá-lo ou serializá-lo no disco.  
  
 Instrumentação com mais qualidade com a interface ICorProfiler  
 Agora, os criadores de perfil que usam a funcionalidade ReJit da API `ICorProfiler` para instrumentação dinâmica podem modificar alguns metadados. Anteriormente, essas ferramentas podiam instrumentar IL a qualquer momento, mas os metadados só podiam ser modificados no tempo de carregamento do módulo. Como IL faz referência aos metadados, isso limitou os tipos de instrumentação possíveis. Retirados alguns desses limites adicionando o método [ICorProfilerInfo7::ApplyMetaData](../Topic/ICorProfilerInfo7::ApplyMetaData%20Method.md) a fim de oferecer suporte a um subconjunto de edições de metadados após o carregamento do módulo, em particular, adicionando novos registros `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec` e `UserString`. Essa alteração possibilita um intervalo mais amplo de instrumentação dinâmica possível.  
  
<a name="NGEN461"></a>   
### <a name="native-image-generator-ngen-pdbs"></a>PDBs do NGEN (Gerador de Imagens Nativas)  
 O rastreamento de eventos entre máquinas permite aos clientes criar o perfil de um programa na Máquina A e examinar os dados de criação de perfil com mapeamento de linha de origem na Máquina B. Com as versões anteriores do .NET Framework, o usuário copiaria todos os módulos e imagens nativas da máquina com perfil para a máquina de análise que contém o PDB IL para criar o mapeamento da fonte para a nativa. Embora esse processo funcione bem quando os arquivos são relativamente pequenos, por exemplo, para aplicativos de telefone, os arquivos podem ser muito grandes em sistemas do desktop e a cópia exige um tempo considerável.  
  
 Com PDBs do Ngen, o NGen pode criar um PDB que contém o mapeamento do IL para a nativa sem uma dependência do PDB do IL. Em nosso cenário de rastreamento de eventos entre máquinas, basta copiar o PDB da imagem nativa gerado pela Máquina A para a Máquina B e usar as [APIs de acesso à interface de depuração](https://docs.microsoft.com/en-us/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) para ler o mapeamento da fonte ao IL do PDB de IL e o mapeamento de IL para nativa do PDB da imagem nativa. A combinação dos dois mapeamentos fornece um mapeamento da fonte para nativa. Como o PDB da imagem nativa é muito menor do que todos os módulos e imagens nativas, o processo de cópia da Máquina A para a Máquina B é muito mais rápido.  
  
<a name="v46"></a>   
## <a name="whats-new-in-net-2015"></a>Novidades do .NET 2015  
 O .NET 2015 apresenta o .NET Framework 4.6 e o .NET Core. Alguns recursos novos se aplicam aos dois, enquanto outros recursos são específicos ao .NET Framework 4.6 ou .NET Core.  
  
-   **ASP.NET 5**  
  
     O .NET 2015 inclui o ASP.NET 5, que é uma plataforma enxuta do .NET para a compilação de aplicativos modernos baseados em nuvem. A plataforma é modular para que você possa incluir somente os recursos necessários em seu aplicativo. Pode ser hospedada no IIS ou auto-hospedada em um processo personalizado, e você pode executar aplicativos com diferentes versões do .NET Framework no mesmo servidor. Ela inclui um novo sistema de configuração do ambiente projetado para implantação na nuvem.  
  
     MVC, API da Web e Páginas da Web são unificados em uma única estrutura chamada MVC 6. Compile aplicativos do ASP.NET 5 usando as novas ferramentas no Visual Studio 2015. Os aplicativos existentes funcionarão no novo .NET Framework; no entanto, para compilar um aplicativo que usa o MVC 6 ou SignalR 3, use o sistema de projetos no Visual Studio 2015.  
  
     Para saber mais, confira [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238).  
  
-   **Atualizações do ASP.NET**  
  
    -   **API baseada em tarefas para a liberação de resposta assíncrona**  
  
         Agora, o ASP.NET fornece uma API simples baseada em tarefas para liberação de resposta assíncrona, [HttpResponse.FlushAsync](assetId:///M:System.Web.HttpResponse.FlushAsync?qualifyHint=True&autoUpgrade=True), que permite a liberação das respostas de modo assíncrono usando o suporte a `async/await` de sua linguagem.  
  
    -   `Model binding supports task-returning methods`  
  
         No .NET Framework 4.5, o ASP.NET adicionou o recurso de Associação de Modelo, que permitiu uma abordagem extensível e focada no código para operações de dados com base em CRUD em páginas de Web Forms e controles de usuário. Agora, o sistema de Associação de Modelo oferece suporte a métodos de associação de modelos que retornam [Task](assetId:///T:System.Threading.Tasks.Task?qualifyHint=False&autoUpgrade=True). Esse recurso permite aos desenvolvedores de Web Forms obter os benefícios de escalabilidade do modo assíncrono com a facilidade do sistema de associação de dados ao usar versões mais recentes dos ORMs, incluindo o Entity Framework.  
  
         A associação de modelo assíncrono é controlada pela configuração `aspnet:EnableAsyncModelBinding`.  
  
        ```  
  
        <appSettings>  
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />  
        </appSettings>  
  
        ```  
  
         Em aplicativos direcionados ao .NET Framework 4.6, o padrão é `true`. Em aplicativos em execução no .NET Framework 4.6 direcionados a uma versão anterior do .NET Framework, o padrão é `false`. Isso pode ser habilitado ao definir a configuração como `true`.  
  
    -   **Suporte a HTTP/2 (Windows 10)**  
  
         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) é uma nova versão do protocolo HTTP que fornece uma utilização de conexão muito melhor (menos viagens entre cliente e servidor), resultando em um carregamento de página da Web com menor latência para os usuários.  As páginas da Web (em vez de serviços) são as mais beneficiados com o HTTP/2, pois o protocolo otimiza para solicitação de vários artefatos como parte de uma experiência única. O suporte ao HTTP/2 foi adicionado ao ASP.NET no .NET Framework 4.6. Como a funcionalidade de rede existe em várias camadas, havia a necessidade de novos recursos no Windows, no IIS e no ASP.NET para habilitar o HTTP/2. Você deve estar executando o Windows 10 para usar o HTTP/2 com o ASP.NET.  
  
         O HTTP/2 também é compatível e ativado por padrão em aplicativos UWP (Plataforma Universal do Windows) do Windows 10 que usam a API [System.Net.Http.HttpClient](assetId:///T:System.Net.Http.HttpClient?qualifyHint=True&autoUpgrade=True).  
  
         Para fornecer uma maneira de usar o recurso [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) em aplicativos ASP.NET, um novo método com duas sobrecargas, [PushPromise(String)](assetId:///M:System.Web.HttpResponse.PushPromise(System.String)?qualifyHint=False&autoUpgrade=False) e [PushPromise(String, String, NameValueCollection)](assetId:///M:System.Web.HttpResponse.PushPromise(System.String,System.String,System.Collections.Specialized.NameValueCollection)?qualifyHint=False&autoUpgrade=False), foi adicionado à classe [HttpResponse](assetId:///T:System.Web.HttpResponse?qualifyHint=False&autoUpgrade=True).  
  
        > [!NOTE]
        >  Embora o ASP.NET 5 ofereça suporte ao HTTP/2, o suporte para o recurso PUSH PROMISE ainda não foi adicionado.  
  
         O navegador e o servidor Web (IIS no Windows) fazem todo o trabalho. Você não precisa fazer qualquer trabalho pesado para seus usuários.  
  
         A maioria dos [principais navegadores oferece suporte a HTTP/2](http://www.wikipedia.org/wiki/HTTP/2), portanto, é provável que seus usuários se beneficiem do suporte a HTTP/2 se o servidor oferecer suporte a ele.  
  
    -   **Suporte para o protocolo de associação de token**  
  
         A Microsoft e o Google colaboraram em uma nova abordagem para autenticação chamada de [Protocolo de associação de token](https://github.com/TokenBinding/Internet-Drafts). A premissa é que tokens de autenticação (no cache do navegador) podem ser roubados e usados por criminosos para acessar recursos seguros (por exemplo, sua conta bancária) sem a necessidade de sua senha ou de qualquer outro conhecimento privilegiado. O novo protocolo tem como objetivo atenuar esse problema.  
  
         O Protocolo de associação de token será implementado no Windows 10 como um recurso do navegador. Aplicativos ASP.NET participarão do protocolo, para que os tokens de autenticação sejam validados como legítimos. As implementações do cliente e do servidor estabelecem a proteção de ponta a ponta especificada pelo protocolo.  
  
    -   **Algoritmos de hash da cadeia de caracteres aleatória**  
  
         O .NET Framework 4.5 apresentou um [algoritmo de hash de cadeia de caracteres aleatória](https://msdn.microsoft.com/library/jj152924.aspx). No entanto, ele não tinha suporte do ASP.NET porque alguns recursos do ASP.NET dependem de um código hash estável. No .NET Framework 4.6, já há suporte para os algoritmos de hash da cadeia de caracteres aleatória. Para habilitar esse recurso, use a configuração `aspnet:UseRandomizedStringHashAlgorithm`.  
  
        ```  
  
        <appSettings>  
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />  
        </appSettings>  
  
        ```  
  
-   **ADO.NET**  
  
     O ADO.NET agora oferece suporte ao recurso Always Encrypted disponível no SQL Server 2016 Community Technology Preview 2 (CTP2). Com o Always Encrypted, o SQL Server pode executar operações em dados criptografados e, acima de tudo, a chave de criptografia reside com o aplicativo no ambiente de confiança do cliente, e não no servidor. O Always Encrypted protege os dados do cliente para que DBAs não tenham acesso aos dados de texto sem formatação. A criptografia e a descriptografia de dados ocorre de forma transparente no nível do driver, minimizando as alterações que precisam ser feitas nos aplicativos atuais. Para obter detalhes, confira [Always Encrypted (Mecanismo de banco de dados)](https://msdn.microsoft.com/library/mt163865\(v=sql.130\).aspx) e [Always Encrypted (desenvolvimento do cliente)](https://msdn.microsoft.com/library/mt147923\(v=sql.130\).aspx).  
  
-   **Compilador JIT de 64 bits para código gerenciado**  
  
     O .NET Framework 4.6 apresenta uma nova versão do compilador JIT de 64 bits (cujo codinome original é RyuJIT). O novo compilador de 64 bits fornece melhorias consideráveis de desempenho em relação ao compilador JIT de 64 bits mais antigo. O novo compilador de 64 bits está habilitado para processos de 64 bits em execução sobre o .NET Framework 4.6. Seu aplicativo será executado em um processo de 64 bits se for compilado como 64 bits ou AnyCPU e será executado em um sistema operacional de 64 bits. Apesar de nossos esforços para fazer a transição para o novo compilador a mais transparente possível, ainda é possível perceber mudanças no comportamento. Gostaríamos de saber sobre quaisquer problemas encontrados ao usar o novo compilador JIT. Entre em contato conosco por meio do [Microsoft Connect](http://connect.microsoft.com/) se você encontrar um problema que possa estar relacionado ao novo compilador JIT de 64 bits.  
  
     O novo compilador JIT de 64 bits também inclui recursos de aceleração de hardware SIMD quando combinado com tipos habilitados para SIMD no namespace [System.Numerics](assetId:///N:System.Numerics?qualifyHint=False&autoUpgrade=True), o que pode suspender aprimoramentos no desempenho.  
  
-   **Aperfeiçoamentos no carregador de assembly**  
  
     Agora, o carregador de assembly usa a memória de forma mais eficiente ao descarregar assemblies de nível de integridade após uma imagem NGEN correspondente ser carregada. Essa mudança reduz a memória virtual, o que é particularmente benéfico para aplicativos de 32 bits grandes (como o Visual Studio) e também poupa memória física.  
  
-   **Mudanças na biblioteca de classes base**  
  
     Várias APIs novas foram adicionadas ao .NET Framework 4.6 para habilitar cenários-chave. As seguintes alterações e adições foram incluídas:  
  
    -   Implementações **IReadOnlyCollection\<T>**   
  
         As coleções adicionais implementam [IReadOnlyCollection\<T>](assetId:///T:System.Collections.Generic.IReadOnlyCollection`1?qualifyHint=False&autoUpgrade=True) como [Queue<T\>](assetId:///T:System.Collections.Generic.Queue`1?qualifyHint=False&autoUpgrade=True) e [Stack\<T>](assetId:///T:System.Collections.Generic.Stack`1?qualifyHint=False&autoUpgrade=True).  
  
    -   **CultureInfo.CurrentCulture e CultureInfo.CurrentUICulture**  
  
         As propriedades [CurrentCulture](assetId:///P:System.Globalization.CultureInfo.CurrentCulture?qualifyHint=True&autoUpgrade=True) e [CultureInfo.CurrentUICulture](assetId:///P:System.Globalization.CultureInfo.CurrentUICulture?qualifyHint=True&autoUpgrade=True) agora são leitura e gravação, em vez de somente leitura. Se você atribuir um novo objeto [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True) a essas propriedades, a cultura do thread atual definida pela propriedade `Thread.CurrentThread.CurrentCulture`, e a cultura do thread de interface do usuário atual definida pela propriedade `Thread.CurrentThread.CurrentUICulture` também mudarão.  
  
    -   **Aprimoramentos na coleta de lixo (GC)**  
  
         Agora, a classe [GC](assetId:///T:System.GC?qualifyHint=False&autoUpgrade=True) inclui os métodos[TryStartNoGCRegion](assetId:///M:System.GC.TryStartNoGCRegion(System.Int64)?qualifyHint=False&autoUpgrade=True) e [EndNoGCRegion](assetId:///M:System.GC.EndNoGCRegion?qualifyHint=False&autoUpgrade=True) que permitem o cancelamento da permissão da coleta de lixo durante a execução de um caminho crítico.  
  
         Uma nova sobrecarga do método [GC.Collect(Int32, GCCollectionMode, Boolean, Boolean)](assetId:///M:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean,System.Boolean)?qualifyHint=True&autoUpgrade=False) lhe permite controlar se o heap de objetos pequeno e o heap de objetos grande são limpos e compactadas ou somente limpos.  
  
    -   **Tipos habilitados para SIMD**  
  
         Agora, o namespace [Numerics](assetId:///N:System.Numerics?qualifyHint=False&autoUpgrade=True) inclui uma série de tipos habilitados para SIMD, como [Matrix3x2](assetId:///T:System.Numerics.Matrix3x2?qualifyHint=False&autoUpgrade=True), [Matrix4x4](assetId:///T:System.Numerics.Matrix4x4?qualifyHint=False&autoUpgrade=True), [Plane](assetId:///T:System.Numerics.Plane?qualifyHint=False&autoUpgrade=True), [Quaternion](assetId:///T:System.Numerics.Quaternion?qualifyHint=False&autoUpgrade=True), [Vector2](assetId:///T:System.Numerics.Vector2?qualifyHint=False&autoUpgrade=True), [Vector3](assetId:///T:System.Numerics.Vector3?qualifyHint=False&autoUpgrade=True) e [Vector4](assetId:///T:System.Numerics.Vector4?qualifyHint=False&autoUpgrade=True).  
  
         Como o novo compilador JIT de 64 bits também inclui recursos de aceleração de hardware SIMD, há melhorias de desempenho consideráveis, especialmente ao usar os tipos habilitados para SIMD com o novo compilador JIT de 64 bits.  
  
    -   **Atualizações de criptografia**  
  
         A API [System.Security.Cryptography](assetId:///N:System.Security.Cryptography?qualifyHint=True&autoUpgrade=True) está sendo atualizada para oferecer suporte às [APIs de criptografia CNG do Windows](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx). Versões anteriores do .NET Framework dependiam inteiramente de uma [versão anterior das APIs de criptografia do Windows](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx) como a base para a implementação de [System.Security.Cryptography](assetId:///N:System.Security.Cryptography?qualifyHint=True&autoUpgrade=True). Recebemos solicitações para o suporte a API de CNG, uma vez que ela dá suporte a [algoritmos de criptografia modernos](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support), que são importantes para determinadas categorias de aplicativos.  
  
         O .NET Framework 4.6 inclui os seguintes aprimoramentos novos a fim de oferecer suporte às APIs de criptografia CNG do Windows:  
  
        -   Um conjunto de métodos de extensão para Certificados X509, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` e `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, que retornam uma implementação baseada em CNG, em vez de uma implementação baseada em CAPI, quando for possível. (Alguns cartões inteligentes etc., ainda exigirão CAPI, e as APIs tratam do fallback).  
  
        -   A classe [System.Security.Cryptography.RSACng](assetId:///T:System.Security.Cryptography.RSACng?qualifyHint=True&autoUpgrade=True), que fornece uma implementação CNG do algoritmo RSA.  
  
        -   Aprimoramentos à API do RSA para que as ações comuns não exijam mais a conversão. Por exemplo, a criptografia de dados usando um objeto [X509Certificate2](assetId:///T:System.Security.Cryptography.X509Certificates.X509Certificate2?qualifyHint=False&autoUpgrade=True) exige um código semelhante ao seguinte em versões anteriores do .NET Framework.  
  
<!-- TODO: review snippet reference              [!CODE [WhatsNew.Casting#1](../CodeSnippet/VS_Snippets_CLR/whatsnew.casting#1)]  -->  
  
             Code that uses the new cryptography APIs in the .NET Framework 4.6 can be rewritten as follows to avoid the cast.  
  
<!-- TODO: review snippet reference              [!CODE [WhatsNew.Casting#2](../CodeSnippet/VS_Snippets_CLR/whatsnew.casting#2)]  -->  
  
    -   **Suporte para conversão de datas e horas para ou do horário Unix**  
  
         Os novos métodos a seguir foram adicionados à estrutura [DateTimeOffset](assetId:///T:System.DateTimeOffset?qualifyHint=False&autoUpgrade=True) para oferecer suporte à conversão de valores de data e hora para ou de horário Unix:  
  
        -   [DateTimeOffset.FromUnixTimeSeconds](assetId:///M:System.DateTimeOffset.FromUnixTimeSeconds(System.Int64)?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.FromUnixTimeMilliseconds](assetId:///M:System.DateTimeOffset.FromUnixTimeMilliseconds(System.Int64)?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.ToUnixTimeSeconds](assetId:///M:System.DateTimeOffset.ToUnixTimeSeconds?qualifyHint=True&autoUpgrade=True)  
  
        -   [DateTimeOffset.ToUnixTimeMilliseconds](assetId:///M:System.DateTimeOffset.ToUnixTimeMilliseconds?qualifyHint=True&autoUpgrade=True)  
  
    -   **Opções de compatibilidade**  
  
         A nova classe [AppContext](assetId:///T:System.AppContext?qualifyHint=False&autoUpgrade=True) adiciona um novo recurso de compatibilidade que permite aos escritores de biblioteca fornecer aos seus usuários um mecanismo de recusa uniforme para a nova funcionalidade. Ela estabelece um contrato flexível entre componentes a fim de comunicar uma solicitação de recusa. Normalmente, essa funcionalidade é importante quando uma alteração é feita na funcionalidade existente. Por outro lado, já existe uma aceitação implícita da nova funcionalidade.  
  
         Com o [AppContext](assetId:///T:System.AppContext?qualifyHint=False&autoUpgrade=True), as bibliotecas definem e expõem as opções de compatibilidade, enquanto o código que depende delas podem definir essas opções a fim de afetar o comportamento da biblioteca. Por padrão, as bibliotecas fornecem a nova funcionalidade, e apenas a alteram (ou seja, eles fornecem a funcionalidade anterior) se a opção for definida.  
  
         Um aplicativo (ou uma biblioteca) pode declarar o valor de uma opção (que é sempre um valor [Boolean](assetId:///T:System.Boolean?qualifyHint=False&autoUpgrade=True)) definida pela biblioteca dependente. A opção é sempre implicitamente `false`. A definição da opção como `true` a habilita. A definição explícita da opção `false` fornece o novo comportamento.  
  
        ```csharp  
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);  
        ```  
  
         A biblioteca deve verificar se um consumidor declarou o valor da opção e, em seguida, agir adequadamente.  
  
        ```  
  
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))   
        {  
           // This is the case where the switch value was not set by the application.   
           // The library can choose to get the value of shouldThrow by other means.   
           // If no overrides nor default values are specified, the value should be 'false'.   
           // A false value implies the latest behavior.  
        }  
  
           // The library can use the value of shouldThrow to throw exceptions or not.  
           if (shouldThrow)   
           {  
              // old code  
           }  
           else {  
              // new code  
           }  
        }  
  
        ```  
  
         É útil usar um formato consistente para opções, já que elas são um contrato formal exposto por uma biblioteca. Veja a seguir dois formatos óbvios.  
  
        -   *Opção*.*namespace*.*nomedaopção*  
  
        -   *Opção*.*biblioteca*.*nomedaopção*  
  
    -   **Mudanças no TAP (padrão assíncrono baseado em tarefas)**  
  
         Para aplicativos direcionados ao .NET Framework 4.6, os objetos [Task](assetId:///T:System.Threading.Tasks.Task?qualifyHint=False&autoUpgrade=True) e [Task\<TResult>](assetId:///T:System.Threading.Tasks.Task`1?qualifyHint=False&autoUpgrade=True) herdam a cultura e cultura da interface do usuário do thread de chamada. O comportamento de aplicativos direcionados a versões anteriores do .NET Framework, ou que não são direcionados a uma versão específica do .NET Framework, não é afetado. Para saber mais, confira a seção "Cultura e operações assíncronas baseadas em tarefas" do tópico da classe [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True).  
  
         A classe [System.Threading.AsyncLocal\<T>](assetId:///T:System.Threading.AsyncLocal`1?qualifyHint=True&autoUpgrade=True) permite a representação dos dados do ambiente que sejam locais a um fluxo determinado de controle assíncrono, como um método `async`. Ele pode ser usado para persistir dados entre threads. Você também pode definir um método de retorno de chamada que será notificado sempre que os dados do ambiente mudarem, pois a propriedade [AsyncLocal<T\>.Value](assetId:///P:System.Threading.AsyncLocal`1.Value?qualifyHint=True&autoUpgrade=True) foi alterada explicitamente, ou porque o thread encontrou uma transição de contexto.  
  
         Três métodos de conveniência, [Task.CompletedTask](assetId:///P:System.Threading.Tasks.Task.CompletedTask?qualifyHint=True&autoUpgrade=True), [Task.FromCanceled](assetId:///M:System.Threading.Tasks.Task.FromCanceled(System.Threading.CancellationToken)?qualifyHint=True&autoUpgrade=True), e [Task.FromException](assetId:///M:System.Threading.Tasks.Task.FromException(System.Exception)?qualifyHint=True&autoUpgrade=True), foram adicionados ao TAP (padrão assíncrono baseado em tarefa) para retornar as tarefas concluídas em um estado específico.  
  
         Agora, a classe [NamedPipeClientStream](assetId:///T:System.IO.Pipes.NamedPipeClientStream?qualifyHint=False&autoUpgrade=True) dá suporte à comunicação assíncrona com seu novo [ConnectAsync](assetId:///M:System.IO.Pipes.NamedPipeClientStream.ConnectAsync?qualifyHint=False&autoUpgrade=True). ProcessOnStatus...  
  
    -   **O EventSource agora oferece suporte à gravação no Log de eventos**  
  
         Agora, você pode usar a classe [EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True) para registrar mensagens administrativas ou operacionais no log de eventos, além de quaisquer sessões ETW existentes criadas na máquina. No passado, era necessário usar o pacote Microsoft.Diagnostics.Tracing.EventSource NuGet para essa funcionalidade. Agora, essa funcionalidade está integrada ao .NET Framework 4.6.  
  
         O pacote do NuGet e o .NET Framework 4.6 foram atualizados com os seguintes recursos:  
  
        -   **Eventos dinâmicos**  
  
             Permite eventos definidos como "dinâmicos" sem a criação de métodos de evento.  
  
        -   **Cargas avançadas**  
  
             Permite que classes atribuídas especialmente e matrizes, bem como tipos primitivos, sejam passados como uma carga  
  
        -   **Acompanhamento de atividade**  
  
             Faz com que os eventos Iniciar e Parar marquem eventos entre eles com uma ID que representa todas as atividades ativas no momento.  
  
         Para oferecer suporte a esses recursos, o método sobrecarregado [Write](assetId:///M:System.Diagnostics.Tracing.EventSource.Write(System.String)?qualifyHint=False&autoUpgrade=True) foi adicionado à classe [EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True).  
  
-   **Windows Presentation Foundation (WPF)**  
  
    -   **Aprimoramentos de HDPI**  
  
         Agora, o suporte ao HDPI no WPF é melhor no .NET Framework 4.6. Foram feitas alterações no layout para reduzir as ocorrências de distorção em controles com bordas. Por padrão, esse recurso será habilitado somente se [TargetFrameworkAttribute](assetId:///T:System.Runtime.Versioning.TargetFrameworkAttribute?qualifyHint=False&autoUpgrade=True) estiver definido para o .NET 4.6.  Os aplicativos direcionados a versões anteriores do Framework, mas que são executados no .NET Framework 4.6 podem aceitar o novo comportamento adicionando o seguinte à seção [\<runtime>](../Topic/%3Cruntime%3E%20Element.md) do arquivo app.config:  
  
        ```  
  
        <AppContextSwitchOverrides  
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"  
        />  
  
        ```  
  
         Janelas do WPF invadindo vários monitores com configurações de DPI diferentes (configuração de DPI múltiplo) agora são renderizadas completamente sem regiões escurecidas. Você pode desativar esse comportamento adicionando a seguinte linha à seção `<appSettings>` do arquivo app.config:  
  
        ```  
  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
  
        ```  
  
         O suporte ao carregamento automático do cursor à direita com base na configuração de DPI foi adicionado a [System.Windows.Input.Cursor](assetId:///T:System.Windows.Input.Cursor?qualifyHint=True&autoUpgrade=True).  
  
    -   **O toque está melhor**  
  
         Os comentários de clientes no [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) informando que o toque produz um comportamento imprevisível foram resolvidos no .NET Framework 4.6. O limite de toque duplo para aplicativos da Windows Store e aplicativos do WPF agora é o mesmo no Windows 8.1 e em versões posteriores.  
  
    -   **Suporte para janela filho transparente**  
  
         O WPF no .NET Framework 4.6 oferece suporte a janelas filho transparente no Windows 8.1 e versões posteriores. Isso permite a criação de janelas filho não retangulares e janelas filho transparente em suas janelas de nível superior. Você pode ativar esse recurso definindo a propriedade [HwndSourceParameters.UsesPerPixelTransparency](assetId:///P:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency?qualifyHint=True&autoUpgrade=True) como `true`.  
  
-   **WCF (Windows Communication Foundation)**  
  
    -   **Suporte a SSL**  
  
         Agora, o WCF oferece suporte ao TLS 1.1 e TLS 1.2 versão SSL, além do SSL 3.0 e TLS 1.0, ao usar o NetTcp com autenticação de cliente e segurança de transporte. Agora é possível selecionar qual protocolo usar, ou desabilitar protocolos antigos e menos seguros. Isso pode ser feito definindo a propriedade [SslProtocols](assetId:///P:System.ServiceModel.TcpTransportSecurity.SslProtocols?qualifyHint=False&autoUpgrade=True) ou adicionando o seguinte ao arquivo de configuração.  
  
        ```  
        <netTcpBinding>  
           <binding>  
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                 <transport clientCredentialType="None|Windows|Certificate"  
                            protectionLevel="None|Sign|EncryptAndSign"  
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">  
                    </transport>  
              </security>  
           </binding>  
        </netTcpBinding>  
  
        ```  
  
    -   **Enviar mensagens usando conexões HTTP diferentes**  
  
         Agora, o WCF permite que os usuários garantam o envio de determinadas mensagens usando conexões HTTP subjacentes diferentes. Há duas formas de fazer isso:  
  
        -   **Usar um prefixo de nome de grupo de conexão**  
  
             Os usuários podem especificar uma cadeia de caracteres que o WCF usará como obtenção de prefixo para o nome do grupo de conexão. Duas mensagens com prefixos diferentes são enviadas usando conexões HTTP subjacentes diferentes. Defina o prefixo adicionando um par de chave/valor à propriedade [Message.Properties](assetId:///P:System.ServiceModel.Channels.Message.Properties?qualifyHint=True&autoUpgrade=True) da mensagem. A chave é "HttpTransportConnectionGroupNamePrefix"; o valor é o prefixo desejado.  
  
        -   **Usar fábricas de canal diferente**  
  
             Os usuários também podem habilitar um recurso que garante que as mensagens enviadas usando canais criados por fábricas de canal diferentes usarão conexões HTTP subjacentes diferentes. Para habilitar esse recurso, os usuários devem definir o seguinte `appSetting` como `true`:  
  
            ```  
  
            <appSettings>  
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />  
            </appSettings>  
  
            ```  
  
-   **Windows Workflow Foundation (WWF)**  
  
     Agora você pode especificar o número de segundos que um serviço de fluxo de trabalho manterá uma solicitação de operação fora de ordem quando houver um indicador de "não protocolo" pendentes antes do tempo limite da solicitação. Um indicador de "não protocolo" é um indicador que não está relacionado a atividades de Recebimento pendentes. Algumas atividades criam indicadores de não protocolo dentro de sua implementação, portanto, talvez a existência de um indicador não protocolo não seja óbvia. Entre elas estão Estado e Seleção. Então, se você tiver um serviço de fluxo de trabalho implementado com uma máquina de estado, ou que contenha uma atividade de Seleção, provavelmente você terá indicadores de não protocolo. Especifique o intervalo adicionando uma linha semelhante à seguinte à seção `appSettings` do arquivo app.config:  
  
    ```  
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>  
    ```  
  
     O valor padrão é 60 segundos. Se `value` estiver definido como 0, as solicitações de fora de ordem serão imediatamente rejeitadas com uma falha e o seguinte texto:  
  
    ```Output  
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.   
    ```  
  
     Essa é a mesma mensagem recebida se uma mensagem de operação fora de ordem for recebida e não houver nenhum indicador de não protocolo.  
  
     Se o valor do elemento `FilterResumeTimeoutInSeconds` for diferente de zero, houver indicadores de não protocolo e o intervalo de tempo limite expirar, a operação falhará com uma mensagem de tempo limite.  
  
-   **Transações**  
  
     Agora você pode incluir o identificador de transação distribuída para a transação que causou uma exceção derivada de [TransactionException](assetId:///T:System.Transactions.TransactionException?qualifyHint=False&autoUpgrade=True). Faça isso adicionando a seguinte chave à seção `appSettings` do arquivo app.config:  
  
    ```  
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>   
    ```  
  
     O valor padrão é `false`.  
  
-   **Rede**  
  
    -   **Reutilização de soquete**  
  
         O Windows 10 inclui um novo algoritmo de rede de alta escalabilidade que utiliza melhor os recursos da máquina reutilizando portas locais para conexões TCP de saída. O .NET Framework 4.6 oferece suporte ao novo algoritmo, permitindo que aplicativos .NET aproveitem o novo comportamento. Em versões anteriores do Windows, havia um limite de conexão simultânea artificial (normalmente 16.384, o tamanho padrão do intervalo de porta dinâmica), que pode limitar a escalabilidade de um serviço causando o esgotamento de porta sob carga.  
  
         No .NET Framework 4.6, duas novas APIs foram adicionadas para permitir a reutilização de porta, o que remove efetivamente o limite de 64 mil conexões simultâneas:  
  
        -   O valor de enumeração [SocketOptionName.ReuseUnicastPort](assetId:///T:System.Net.Sockets.SocketOptionName?qualifyHint=True&autoUpgrade=True).  
  
        -   A propriedade [ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True).  
  
         Por padrão, a propriedade [ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) é `false` a menos que o valor `HWRPortReuseOnSocketBind` da chave do Registro `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` seja definido como 0x1. Para habilitar a reutilização de porta local em conexões HTTP, defina a propriedade [ServicePointManager.ReusePort](assetId:///P:System.Net.ServicePointManager.ReusePort?qualifyHint=True&autoUpgrade=True) como `true`. Isso faz com que todas as conexões de soquete TCP externa do [HttpClient](assetId:///T:System.Net.Http.HttpClient?qualifyHint=False&autoUpgrade=True) e [HttpWebRequest](assetId:///T:System.Net.HttpWebRequest?qualifyHint=False&autoUpgrade=True) usem uma nova opção de soquete do Windows 10 [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx), que permite a reutilização de porta local.  
  
         Os desenvolvedores que criam um aplicativo somente para soquetes podem especificar a opção [SocketOptionName.ReuseUnicastPort](assetId:///T:System.Net.Sockets.SocketOptionName?qualifyHint=True&autoUpgrade=True) ao chamar um método, como [Socket.SetSocketOption](assetId:///M:System.Net.Sockets.Socket.SetSocketOption(System.Net.Sockets.SocketOptionLevel,System.Net.Sockets.SocketOptionName,System.Byte[])?qualifyHint=True&autoUpgrade=True), para que os soquetes de saídas reutilizem portas locais durante a associação.  
  
    -   **Suporte para nomes de domínio internacionais e PunyCode**  
  
         Uma nova propriedade, [IdnHost](assetId:///P:System.Uri.IdnHost?qualifyHint=False&autoUpgrade=True), foi adicionada à classe [Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) para oferecer melhor suporte a nomes de domínio internacionais e PunyCode.  
  
-   **Redimensionamento em controles do Windows Forms.**  
  
     Esse recurso foi expandido no .NET Framework 4.6 para incluir os tipos [DomainUpDown](assetId:///T:System.Windows.Forms.DomainUpDown?qualifyHint=False&autoUpgrade=True), [NumericUpDown](assetId:///T:System.Windows.Forms.NumericUpDown?qualifyHint=False&autoUpgrade=True), [DataGridViewComboBoxColumn](assetId:///T:System.Windows.Forms.DataGridViewComboBoxColumn?qualifyHint=False&autoUpgrade=True), [DataGridViewColumn](assetId:///T:System.Windows.Forms.DataGridViewColumn?qualifyHint=False&autoUpgrade=True) e [ToolStripSplitButton](assetId:///T:System.Windows.Forms.ToolStripSplitButton?qualifyHint=False&autoUpgrade=True) e o retângulo especificado pela propriedade [Bounds](assetId:///P:System.Drawing.Design.PaintValueEventArgs.Bounds?qualifyHint=False&autoUpgrade=True) usada ao desenhar um [UITypeEditor](assetId:///T:System.Drawing.Design.UITypeEditor?qualifyHint=False&autoUpgrade=True).  
  
     Esse é um recurso de opção de aceitação. Para habilitá-lo, defina o elemento `EnableWindowsFormsHighDpiAutoResizing` como `true` no arquivo de configuração do aplicativo (app.config):  
  
    ```  
  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
  
    ```  
  
-   **Suporte para codificações de página de código**  
  
     O .NET Core oferece suporte principalmente a codificações Unicode, e por padrão fornece suporte limitado a codificações de página de código. É possível adicionar suporte a codificações de página de código disponíveis no .NET Framework, mas não sejam suportados no .NET Core, ao registrar codificações de página de código com o método [Encoding.RegisterProvider](assetId:///M:System.Text.Encoding.RegisterProvider(System.Text.EncodingProvider)?qualifyHint=True&autoUpgrade=True). Para saber mais, confira a documentação da classe [System.Text.CodePagesEncodingProvider](xref:System.Text.CodePagesEncodingProvider).  
  
-   **.NET Nativo**  
  
     Aplicativos do Windows para Windows 10 direcionados ao .NET Core e escritos em C# ou Visual Basic podem tirar proveito de uma nova tecnologia que compila aplicativos para código nativo em vez de IL. Ela produz aplicativos caracterizados por inicialização e tempos de execução mais rápidos. Para saber mais, confira [Compilação de aplicativos com .NET Nativo](../Topic/Compiling%20Apps%20with%20.NET%20Native.md). Para obter uma visão geral do .NET Nativo, examinando qual é a diferente dele para a compilação JIT e o NGEN e o que isso significa para seu código, confira [.NET Nativo e compilação](../Topic/.NET%20Native%20and%20Compilation.md).  
  
     Seus aplicativos são compilados por padrão para código nativo quando você os compila com o Visual Studio 2015. Para saber mais, confira [Introdução ao .NET Nativo](../Topic/Getting%20Started%20with%20.NET%20Native.md).  
  
     Para oferecer suporte à depuração de aplicativos do .NET Nativo, foram adicionadas diversas interfaces e enumerações novas à API de depuração não gerenciada. Para saber mais, confira o tópico [Depuração (Referência de API não gerenciada)](../Topic/Debugging%20\(Unmanaged%20API%20Reference\).md).  
  
-   **Pacotes do código-fonte aberto do .NET Framework**  
  
     Pacotes do .NET Core,como coleções imutáveis, [APIs SIMD](http://go.microsoft.com/fwlink/?LinkID=518639) e APIs de rede, como aquelas encontrados no namespace [System.Net.Http](assetId:///N:System.Net.Http?qualifyHint=False&autoUpgrade=True) agora estão disponíveis como pacotes de código-fonte aberto no [GitHub](https://github.com/). Para acessar o código, confira [NetFx no GitHub](http://go.microsoft.com/fwlink/?LinkID=518634). Para saber mais e saber como contribuir com esses pacotes, confira [.NET Core e código-fonte aberto](../Topic/.NET%20Core%20and%20Open-Source.md), [Home Page do .NET no GitHub](http://go.microsoft.com/fwlink/?LinkID=518635).  
  
 [Voltar ao início](#introduction)  
  
<a name="v452"></a>   
## <a name="whats-new-in-the-net-framework-452"></a>Novidades no .NET Framework 4.5.2  
  
-   **Novas APIs para aplicativos do ASP.NET.** Os novos métodos [HttpResponse.AddOnSendingHeaders](assetId:///M:System.Web.HttpResponse.AddOnSendingHeaders(System.Action{System.Web.HttpContext})?qualifyHint=True&autoUpgrade=True) e [HttpResponseBase.AddOnSendingHeaders](assetId:///M:System.Web.HttpResponseBase.AddOnSendingHeaders(System.Action{System.Web.HttpContextBase})?qualifyHint=True&autoUpgrade=True) permitem a inspeção e a modificação de cabeçalhos de resposta e do código de status à medida que a resposta é liberada ao aplicativo cliente. Considere o uso desses métodos, em vez dos eventos [PreSendRequestHeaders](assetId:///E:System.Web.HttpApplication.PreSendRequestHeaders?qualifyHint=False&autoUpgrade=True) e [PreSendRequestContent](assetId:///E:System.Web.HttpApplication.PreSendRequestContent?qualifyHint=False&autoUpgrade=True); eles são mais eficientes e confiáveis.  
  
     O método [HostingEnvironment.QueueBackgroundWorkItem](assetId:///M:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem(System.Action{System.Threading.CancellationToken})?qualifyHint=True&autoUpgrade=True) permite que você agende itens pequenos de trabalho em segundo plano. ASP.NET rastreia esses itens e evita que IIS termine abruptamente o processo de trabalho até que todos os itens de trabalho em segundo plano tenham sido concluídos. Esse método não pode ser chamado fora de um domínio de aplicativo gerenciado pelo ASP.NET.  
  
     As novas propriedades [HttpResponse.HeadersWritten](assetId:///P:System.Web.HttpResponse.HeadersWritten?qualifyHint=True&autoUpgrade=False) e [HttpResponseBase.HeadersWritten](assetId:///P:System.Web.HttpResponseBase.HeadersWritten?qualifyHint=True&autoUpgrade=False) retornam valores Boolianos que indicam se os cabeçalhos de resposta foram gravados. É possível usar essas propriedades para certificar-se de que as chamadas para APIs como [HttpResponse.StatusCode](assetId:///P:System.Web.HttpResponse.StatusCode?qualifyHint=True&autoUpgrade=True) (que geram exceções se os cabeçalhos foram gravados) tiveram êxito.  
  
-   **Redimensionamento em controles do Windows Forms.** Esse recurso foi expandido. É possível usar a configuração do sistema DPI para redimensionar os componentes dos seguintes controles adicionais (por exemplo, a seta suspensa nas caixas de combinação):  
  
     [ComboBox](assetId:///T:System.Windows.Forms.ComboBox?qualifyHint=False&autoUpgrade=True)   
     [ToolStripComboBox](assetId:///T:System.Windows.Forms.ToolStripComboBox?qualifyHint=False&autoUpgrade=True)   
     [ToolStripMenuItem](assetId:///T:System.Windows.Forms.ToolStripMenuItem?qualifyHint=False&autoUpgrade=True)   
     [Cursor](assetId:///T:System.Windows.Forms.Cursor?qualifyHint=False&autoUpgrade=True)   
     [DataGridView](assetId:///T:System.Windows.Forms.DataGridView?qualifyHint=False&autoUpgrade=True)   
     [DataGridViewComboBoxColumn](assetId:///T:System.Windows.Forms.DataGridViewComboBoxColumn?qualifyHint=False&autoUpgrade=True)  
  
     Esse é um recurso de opção de aceitação. Para habilitá-lo, defina o elemento `EnableWindowsFormsHighDpiAutoResizing` como `true` no arquivo de configuração do aplicativo (app.config):  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
-   **Novo recurso de fluxo de trabalho.** Um gerenciador de recursos que está usando o método [EnlistPromotableSinglePhase](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification)?qualifyHint=False&autoUpgrade=True) (e, portanto, implementando a interface [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True)) pode usar o novo método [Transaction.PromoteAndEnlistDurable](assetId:///M:System.Transactions.Transaction.PromoteAndEnlistDurable(System.Guid,System.Transactions.IPromotableSinglePhaseNotification,System.Transactions.ISinglePhaseNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) para solicitar o seguinte:  
  
    -   Promover a transação para um Coordenador de transações distribuídas da Microsoft (MSDTC).  
  
    -   Substitua [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True) por um [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True), que é uma inscrição durável que oferece suporte a confirmações de fase única.  
  
     Isso pode ser feito dentro do mesmo domínio do aplicativo e não requer nenhum código extra não gerado para interagir com o MSDTC para executar a promoção. O novo método pode ser chamado somente quando houver uma chamada pendente do [System.Transactions](assetId:///N:System.Transactions?qualifyHint=True&autoUpgrade=True) para o método [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True)`Promote` que é implementado pela inscrição passível de promoção.  
  
-   **Melhorias na criação de perfis** As seguintes novas APIs não gerenciadas de criação de perfis fornecem uma criação de perfil mais robusta:  
  
     [Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO](../Topic/COR_PRF_ASSEMBLY_REFERENCE_INFO%20Structure.md)   
     [Enumeração COR_PRF_HIGH_MONITOR](../Topic/COR_PRF_HIGH_MONITOR%20Enumeration.md)   
     [Método GetAssemblyReferences](../Topic/ICorProfilerCallback6::GetAssemblyReferences%20Method.md)   
     [Método GetEventMask2](../Topic/ICorProfilerInfo5::GetEventMask2%20Method.md)   
     [Método SetEventMask2](../Topic/ICorProfilerInfo5::SetEventMask2%20Method.md)   
     [Método AddAssemblyReference](../Topic/ICorProfilerAssemblyReferenceProvider::AddAssemblyReference%20Method.md)  
  
     Implementações anteriores de `ICorProfiler` compatíveis com carregamento lento de montagens pendentes. As novas APIs de criação de perfis requerem montagens dependentes que são injetadas pelo criador de perfil a ser carregado imediatamente, em vez de ser carregado depois que o aplicativo for totalmente inicializado. Essa mudança não afeta os usuários das APIs `ICorProfiler` existentes.  
  
-   **Melhorias na depuração.** As seguintes APIs de depuração novas não gerenciadas fornecem uma melhor integração com um criador de perfil. Agora é possível acessar metadados inseridos por um criador de perfil bem como variáveis locais e código produzido por pedidos do ReJIT compilador quando despejo do depurador.  
  
     [Método SetWriteableMetadataUpdateMode](../Topic/ICorDebugProcess7::SetWriteableMetadataUpdateMode%20Method.md)   
     [Método EnumerateLocalVariablesEx](../Topic/ICorDebugILFrame4::EnumerateLocalVariablesEx%20Method.md)   
     [Método GetLocalVariableEx](../Topic/ICorDebugILFrame4::GetLocalVariableEx%20Method.md)   
     [Método GetCodeEx](../Topic/ICorDebugILFrame4::GetCodeEx%20Method.md)   
     [Método GetActiveReJitRequestILCode](../Topic/ICorDebugFunction3::GetActiveReJitRequestILCode%20Method.md)   
     [Método GetInstrumentedILMap](../Topic/ICorDebugILCode2::GetInstrumentedILMap%20Method.md)  
  
-   **Mudanças no rastreamento de eventos.** O .NET Framework 4.5.2 permite o rastreamento fora do processo para atividades baseadas no ETW (Rastreamento de Eventos para Windows) em uma área de superfície maior. Isso permite que fornecedores de Gerenciamento Avançado de Energia (APM) forneçam ferramentas que rastreiam com precisão os custos de pedidos individuais e atividades entre threads.  Esses eventos são gerados apenas quando os controladores ETW permitem e, portanto, as mudanças não afetam o código ETW gravado anteriormente ou o código executado com o ETW desabilitado.  
  
-   **Promover uma transação e convertê-la em uma inscrição durável**  
  
     [Transaction.PromoteAndEnlistDurable](assetId:///M:System.Transactions.Transaction.PromoteAndEnlistDurable(System.Guid,System.Transactions.IPromotableSinglePhaseNotification,System.Transactions.ISinglePhaseNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) é uma nova API adicionada ao .NET Framework 4.5.2 e 4.6:  
  
    ```  
  
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,  
                                              IPromotableSinglePhaseNotification promotableNotification,  
                                              ISinglePhaseNotification enlistmentNotification,  
                                              EnlistmentOptions enlistmentOptions)  
  
    ```  
  
     O método pode ser usado por uma inscrição criada anteriormente por [Transaction.EnlistPromotableSinglePhase](assetId:///M:System.Transactions.Transaction.EnlistPromotableSinglePhase(System.Transactions.IPromotableSinglePhaseNotification)?qualifyHint=True&autoUpgrade=True) em resposta ao método [ITransactionPromoter.Promote](assetId:///M:System.Transactions.ITransactionPromoter.Promote?qualifyHint=True&autoUpgrade=True). Ele pede que `System.Transactions` promova a transação a uma transação MSDTC e "converta" a inscrição passível de promoção em uma inscrição durável. Após a conclusão desse método, a interface [IPromotableSinglePhaseNotification](assetId:///T:System.Transactions.IPromotableSinglePhaseNotification?qualifyHint=False&autoUpgrade=True) não será mais referenciada por `System.Transactions`, e quaisquer notificações futuras chegarão na interface [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True) fornecida. A inscrição em questão deve agir como uma inscrição durável, oferecendo suporte à ao registro em log e recuperação da transação. Veja [Transaction.EnlistDurable](assetId:///M:System.Transactions.Transaction.EnlistDurable(System.Guid,System.Transactions.IEnlistmentNotification,System.Transactions.EnlistmentOptions)?qualifyHint=True&autoUpgrade=True) para obter detalhes. Além disso, a inscrição deve oferecer suporte a [ISinglePhaseNotification](assetId:///T:System.Transactions.ISinglePhaseNotification?qualifyHint=False&autoUpgrade=True).  Esse método *só* pode ser chamado durante o processamento de uma chamada [ITransactionPromoter.Promote](assetId:///M:System.Transactions.ITransactionPromoter.Promote?qualifyHint=True&autoUpgrade=True). Se esse não for o caso, uma exceção [TransactionException](assetId:///T:System.Transactions.TransactionException?qualifyHint=False&autoUpgrade=True) será gerada.  
  
 [Voltar ao início](#introduction)  
  
<a name="v451"></a>   
## <a name="whats-new-in-the-net-framework-451"></a>Novidades no .NET Framework 4.5.1  
 **Atualizações de abril de 2014**:  
  
-   [Atualização 2 do Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=393658) inclui atualizações para modelos de Biblioteca de Classes Portátil para suporte destes cenários:  
  
    -   É possível usar as APIs do Tempo de Execução do Windows em bibliotecas portáteis que tenham como destino Windows 8.1, Windows Phone 8.1 e Windows Phone Silverlight 8.1.   
  
    -   Você pode incluir XAML (Windows.UI.XAML types) em bibliotecas portáteis quando o destino for Windows 8.1 ou Windows Phone 8.1. Os seguintes modelos XAML são compatíveis: Blank Page, Resource Dictionary, Templated Control e User Control.  
  
    -   Você pode criar um componente de Tempo de Execução do Windows portátil (.winmd file) para uso em Store apps cujo destino seja Windows 8.1 e Windows Phone 8.1.  
  
    -   É possível redirecionar uma biblioteca de classes Windows Store ou Windows Phone Store novamente como uma Biblioteca de Classes Portátil.  
  
     Para saber mais sobre essas mudanças, confira [Biblioteca de classes portátil](../Topic/Cross-Platform%20Development%20with%20the%20Portable%20Class%20Library.md).  
  
-   O conjunto de conteúdo do .NET Framework agora inclui documentação para .NET Native, que é uma tecnologia de pré-compilação para construção e implantação dos aplicativos do Windows. Para melhorar o desempenho, o .NET Native compila seus aplicativos diretamente para o código nativo, ao invés de usar uma linguagem intermediária (IL). Para obter detalhes, confira [Compilação de aplicativos com o .NET Nativo](../Topic/Compiling%20Apps%20with%20.NET%20Native.md).  
  
-   O [.NET Framework Reference Source](http://referencesource.microsoft.com/) fornece experiências de navegação e de funcionalidade, novas e aprimoradas. É possível navegar através do código-fonte online do .NET Framework, [baixar a referência](http://referencesource.microsoft.com/download.html) para visualização offline e percorrer as fontes (incluindo correções e atualizações) durante a depuração. Para saber mais, confira a postagem no blog [A new look for .NET Reference Source](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx) (Um novo olhar sobre a fonte de referência do .NET).  
  
 Os novos recursos e aprimoramentos principais no .NET Framework 4.5.1 incluem:  
  
-   Redirecionamento de associação automático de assemblies. Desde o Visual Studio 2013, quando você compilar um aplicativo destinado ao .NET Framework 4.5.1, os redirecionamentos de associação poderão ser adicionados ao arquivo de configuração do aplicativo se o aplicativo ou seus componentes referenciarem várias versões do mesmo assembly. Você também pode habilitar esse recurso para projetos que se destinam a versões anteriores do .NET Framework. Para saber mais, confira [Como habilitar e desabilitar o redirecionamento automático de associações](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Binding%20Redirection.md).  
  
-   Capacidade de coletar informações de diagnóstico para ajudar desenvolvedores na melhoria do desempenho dos aplicativos de servidor e de nuvem. Para saber mais, veja os métodos [WriteEventWithRelatedActivityId](assetId:///M:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId(System.Int32,System.Guid,System.Object[])?qualifyHint=False&autoUpgrade=True) e [WriteEventWithRelatedActivityIdCore](assetId:///M:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore(System.Int32,System.Guid*,System.Int32,System.Diagnostics.Tracing.EventSource.EventData*)?qualifyHint=False&autoUpgrade=True) da classe [EventSource](assetId:///T:System.Diagnostics.Tracing.EventSource?qualifyHint=False&autoUpgrade=True).  
  
-   Capacidade de compactar explicitamente a LOH (pilha de objetos grandes) durante a coleta de lixo. Para saber mais, veja a propriedade [GCSettings.LargeObjectHeapCompactionMode](assetId:///P:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?qualifyHint=True&autoUpgrade=True).  
  
-   Aperfeiçoamentos de desempenho adicionais como a suspensão do aplicativo ASP.NET, aperfeiçoamentos JIT multicore e inicialização mais rápida do aplicativo após uma atualização do .NET Framework. Para obter detalhes, confira o [Comunicado do .NET Framework 4.5.1](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx) e a postagem de blog [Suspensão de aplicativos ASP.NET](http://blogs.msdn.com/b/dotnet/archive/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting.aspx).  
  
 Os aprimoramentos para Windows Forms incluem:  
  
-   Redimensionamento em controles do Windows Forms. É possível usar a configuração do sistema DPI para redimensionar os componentes de controle (por exemplo, os ícones que aparecem na grade de propriedade) optando por uma entrada no arquivo de configuração de aplicativo (app.config) do seu aplicativo. Atualmente, esse recurso é compatível com os seguintes controles do Windows Forms:  
  
     [PropertyGrid](assetId:///T:System.Windows.Forms.PropertyGrid?qualifyHint=False&autoUpgrade=True)   
     [TreeView](assetId:///T:System.Windows.Forms.TreeView?qualifyHint=False&autoUpgrade=True)   
     Alguns aspectos do [DataGridView](assetId:///T:System.Windows.Forms.DataGridView?qualifyHint=False&autoUpgrade=True) (consulte [novos recursos em 4.5.2](#v452) para obter os controles adicionais compatíveis)  
  
     Para habilitar esse recurso, adicione um novo elemento \<appSettings> ao arquivo de configuração (app.config) e defina o elemento `EnableWindowsFormsHighDpiAutoResizing` como `true`:  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
 Entre os aperfeiçoamentos durante a depuração de seus aplicativos do .NET Framework no Visual Studio 2013 estão:  
  
-   Valores de retorno no depurador do Visual Studio. Quando você depura um aplicativo gerenciado no Visual Studio 2013, a janela Autos exibe valores e tipos de retorno para os métodos. Essas informações estão disponíveis para aplicativos de área de trabalho, Windows Store e Windows Phone. Para saber mais, confira [Examinar valores de retorno de chamadas de método](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx) na biblioteca MSDN.  
  
-   Editar e continuar para aplicativos 64 bits. O Visual Studio 2013 dá suporte ao recurso Editar e continuar para aplicativos gerenciados de 64 bits para área de trabalho, Windows Store e Windows Phone. As limitações existentes permanecem em vigor para aplicativos 32 e 64 bits (confira a última seção do artigo [Alterações de código compatíveis (C#)](http://msdn.microsoft.com/library/ms164927\(v=vs.120\).aspx)).  
  
-   Depuração async-aware. Para facilitar a depuração de aplicativos assíncronos no Visual Studio 2013, a pilha de chamadas oculta o código de infraestrutura fornecido por compiladores para dar suporte à programação assíncrona e também as cadeias em quadros pai lógicos para que você possa acompanhar a execução lógica do programa com mais clareza. Uma janela Tarefas substitui a janela Tarefas Paralelas e exibe tarefas relacionadas a um ponto de interrupção específico e também exibe outras tarefas que estão ativas ou agendadas no aplicativo. Leia sobre esse recurso na seção "Depuração async-aware" do [Comunicado do .NET Framework 4.5.1.](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx).  
  
-   Melhor suporte à exceção para componentes do Tempo de Execução do Windows. No Windows 8.1, as exceções surgidas de aplicativos da Windows Store preservam as informações sobre o erro que causou a exceção, mesmo entre os limites de linguagem. Leia sobre esse recurso na seção "Desenvolvimento de aplicativos para a Windows Store" do [Comunicado do .NET Framework 4.5.1.](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx).  
  
 A partir do Visual Studio 2013, você pode usar a [Ferramenta de Otimização Orientada de Perfil Gerenciado (Mpgo.exe)](../Topic/Mpgo.exe%20\(Managed%20Profile%20Guided%20Optimization%20Tool\).md) para otimizar aplicativos Windows 8.x Store, bem como aplicativos da área de trabalho.  
  
 Para novos recursos no ASP.NET 4.5.1, confira [ASP.NET 4.5.1 e Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) no site do ASP.NET.  
  
 [Voltar ao início](#introduction)  
  
<a name="core"></a>   
## <a name="whats-new-in-the-net-framework-45"></a>Novidades no .NET Framework 4.5  
  
### <a name="core-new-features-and-improvements"></a>Novos recursos e aprimoramentos do Core  
  
-   Capacidade de reduzir as reinicializações do sistema detectando e fechando-se os aplicativos do .NET Framework 4 durante a implantação. Confira [Redução de reinicializações do sistema durante instalações do .NET Framework 4.5](../Topic/Reducing%20System%20Restarts%20During%20.NET%20Framework%204.5%20Installations.md).  
  
-   Suporte para matrizes maiores que 2 gigabytes (GB) em plataformas 64 bits. Esse recurso pode ser habilitado no arquivo de configuração do aplicativo. Confira o elemento [\<gcAllowVeryLargeObjects>](../Topic/%3CgcAllowVeryLargeObjects%3E%20Element.md) que também lista outras restrições ao tamanho do objeto e da matriz.  
  
-   Melhor desempenho por meio de coleta de lixo em segundo plano para servidores. Quando você usa a coleta de lixo do servidor no .NET Framework 4.5, a coleta de lixo em segundo plano é automaticamente ativada. Confira a seção Coleta de lixo de servidor em segundo plano do tópico [Noções básicas da coleta de lixo](../Topic/Fundamentals%20of%20Garbage%20Collection.md).  
  
-   Compilação JIT (just-in-time) em segundo plano, disponível como opção em vários processadores multicore para melhorar o desempenho do aplicativo. Veja [ProfileOptimization](assetId:///T:System.Runtime.ProfileOptimization?qualifyHint=False&autoUpgrade=True).  
  
-   Capacidade de limitar por quanto tempo o mecanismo de expressões regulares tentará resolver uma expressão regular antes de expirar. Veja a propriedade [Regex.MatchTimeout](assetId:///P:System.Text.RegularExpressions.Regex.MatchTimeout?qualifyHint=True&autoUpgrade=True).  
  
-   Capacidade de definir a cultura padrão para um domínio de aplicativo. Veja a classe [CultureInfo](assetId:///T:System.Globalization.CultureInfo?qualifyHint=False&autoUpgrade=True).  
  
-   Suporte de console para a codificação Unicode (UTF-16). Veja a classe [Console](assetId:///T:System.Console?qualifyHint=False&autoUpgrade=True).  
  
-   Suporte para controle de versão da ordenação de cadeia de caracteres culturais e dados de comparação. Veja a classe [SortVersion](assetId:///T:System.Globalization.SortVersion?qualifyHint=False&autoUpgrade=True).  
  
-   Melhor desempenho durante a recuperação de recursos. Confira [Empacotar e implantar recursos](../Topic/Packaging%20and%20Deploying%20Resources%20in%20Desktop%20Apps.md).  
  
-   Aperfeiçoamentos na compactação para reduzir o tamanho de um arquivo compactado. Veja o namespace [System.IO.Compression](assetId:///N:System.IO.Compression?qualifyHint=True&autoUpgrade=True).  
  
-   Capacidade de personalizar um contexto de reflexão para substituir o comportamento de reflexão padrão por meio da classe [CustomReflectionContext](assetId:///T:System.Reflection.Context.CustomReflectionContext?qualifyHint=False&autoUpgrade=True).  
  
-   Suporte para a versão 2008 do padrão IDNA (Internationalized Domain Names in Applications) quando a classe [System.Globalization.IdnMapping](assetId:///T:System.Globalization.IdnMapping?qualifyHint=True&autoUpgrade=True) é usada no Windows 8.  
  
-   A delegação da comparação de cadeia de caracteres para o sistema operacional, que implementa o Unicode 6.0, quando o .NET Framework é usado no Windows 8. Ao executar em outras plataformas, o .NET Framework inclui seus próprios dados de comparação da cadeia de caracteres, o que implementa o Unicode 5.x. Veja a classe [String](assetId:///T:System.String?qualifyHint=False&autoUpgrade=True) e a seção Comentários da classe [SortVersion](assetId:///T:System.Globalization.SortVersion?qualifyHint=False&autoUpgrade=True).  
  
-   Capacidade de computar os códigos de hash para cadeias de caracteres com base no domínio do aplicativo. Confira o elemento [\<UseRandomizedStringHashAlgorithm>](../Topic/%3CUseRandomizedStringHashAlgorithm%3E%20Element.md).  
  
-   Suporte à reflexão de tipo dividido entre as classes [Type](assetId:///T:System.Type?qualifyHint=False&autoUpgrade=True) e [TypeInfo](assetId:///T:System.Reflection.TypeInfo?qualifyHint=False&autoUpgrade=True). Confira [Reflexão no .NET Framework para aplicativos da Windows Store](../Topic/Reflection%20in%20the%20.NET%20Framework%20for%20Windows%20Store%20Apps.md).  
  
### <a name="managed-extensibility-framework-mef"></a>MEF (Managed Extensibility Framework)  
 No .NET Framework 4.5, a MEF (Managed Extensibility Framework) fornece os seguintes recursos novos:  
  
-   Suporte para tipos genéricos.  
  
-   O modelo de programação baseado na convenção permite criar partes com base em convenções de nomenclatura, em vez de atributos.  
  
-   Vários escopos.  
  
-   Um subconjunto da MEF que você pode usar ao criar aplicativos Windows 8.x Store. Esse subconjunto está disponível como um [pacote baixável](http://go.microsoft.com/fwlink/?LinkId=256238) da Galeria NuGet. Para instalar o pacote, abra o projeto no Visual Studio, escolha **Gerenciar Pacotes NuGet** no menu **Projeto** e procure o pacote `Microsoft.Composition` online.  
  
 Para saber mais, confira [Managed Extensibility Framework (MEF)](../Topic/Managed%20Extensibility%20Framework%20\(MEF\).md).  
  
### <a name="asynchronous-file-operations"></a>Operações de arquivo assíncronas  
 No .NET Framework 4.5, os novos recursos assíncronos foram adicionados às linguagens C# e Visual Basic. Esses recursos adicionam um modelo com base na tarefa para executar operações assíncronas. Para usar esse novo modelo, use os métodos assíncronos nas classes de E/S. Confira [E/S de arquivo assíncrona](../Topic/Asynchronous%20File%20I-O.md).  
  
<a name="tools"></a>   
### <a name="tools"></a>Ferramentas  
 No .NET Framework 4.5, o Gerador de Arquivos de Recurso (Resgen.exe) permite criar um arquivo .resw a ser usado em aplicativos Windows 8.x Store com base em um arquivo .resources inserido em um assembly do .NET Framework. Para saber mais, confira [Resgen.exe (Gerador de arquivo de recurso)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md).  
  
 A Ferramenta de Otimização Orientada de Perfil Gerenciado (Mpgo.exe) permite melhorar o tempo de inicialização do aplicativo, a utilização da memória (tamanho do conjunto de trabalho) e a produtividade otimizando-se assemblies de imagem nativa. A ferramenta de linha de comando gera dados de perfil para assemblies de aplicativo de imagem nativa. Confira [Mpgo.exe (Ferramenta de Otimização Guiada por Perfil Gerenciado)](../Topic/Mpgo.exe%20\(Managed%20Profile%20Guided%20Optimization%20Tool\).md). A partir do Visual Studio 2013, você pode usar a Mpgo.exe para otimizar aplicativos Windows 8.x Store, bem como aplicativos da área de trabalho.  
  
<a name="parallel"></a>   
### <a name="parallel-computing"></a>Computação paralela  
 O .NET Framework 4.5 fornece vários recursos e aperfeiçoamentos novos para computação paralela. Entre eles estão melhor desempenho, mais controle, maior suporte para programação assíncrona, uma nova biblioteca de fluxo de dados e o melhor suporte para a depuração paralela e a análise de desempenho. Confira a entrada [Novidades sobre paralelismo no .NET 4.5](http://go.microsoft.com/fwlink/?LinkId=235061) no blog Parallel Programming with .NET.  
  
<a name="web"></a>   
### <a name="web"></a>Web  
 ASP.NET 4.5 e 4.5.1 adicionam associação de modelo para formulários da Web, suporte WebSocket, manipuladores assíncronos, aperfeiçoamentos de desempenho e muitos outros recursos. Para obter mais informações, consulte os seguintes recursos:  
  
-   [ASP.NET 4.5 e Visual Studio 2012](../Topic/ASP.NET%20Core%20and%20Visual%20Studio%202015.md) na Biblioteca MSDN.  
  
-   [ASP.NET 4.5.1 e Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) no site do ASP.NET.  
  
<a name="networking"></a>   
### <a name="networking"></a>Rede  
 O .NET Framework 4.5 fornece uma nova interface de programação para aplicativos HTTP. Para saber mais, veja os novos namespaces [System.Net.Http](assetId:///N:System.Net.Http?qualifyHint=True&autoUpgrade=True) e [System.Net.Http.Headers](assetId:///N:System.Net.Http.Headers?qualifyHint=True&autoUpgrade=True).  
  
 O suporte também está incluído para uma nova interface de programação para aceitar e interagir com uma conexão WebSocket usando-se a classe [HttpListener](assetId:///T:System.Net.HttpListener?qualifyHint=False&autoUpgrade=True) existente e as classes relacionadas. Para saber mais, confira o novo namespace [System.Net.WebSockets](assetId:///N:System.Net.WebSockets?qualifyHint=False&autoUpgrade=True) e a classe [HttpListener](assetId:///T:System.Net.HttpListener?qualifyHint=False&autoUpgrade=True).  
  
 Além disso, o .NET Framework 4.5 inclui os seguintes aperfeiçoamentos de rede:  
  
-   Suporte ao URI compatível com RFC. Para saber mais, consulte [Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) e as classes relacionadas.  
  
-   Suporte para análise IDN. Para saber mais, consulte [Uri](assetId:///T:System.Uri?qualifyHint=False&autoUpgrade=True) e as classes relacionadas.  
  
-   Suporte para EAI (Email Address Internationalization). Para saber mais, confira o namespace [System.Net.Mail](assetId:///N:System.Net.Mail?qualifyHint=False&autoUpgrade=True).  
  
-   Suporte a IPv6 melhorado. Para saber mais, confira o namespace [System.Net.NetworkInformation](assetId:///N:System.Net.NetworkInformation?qualifyHint=False&autoUpgrade=True).  
  
-   Suporte a soquete de modo duplo. Para saber mais, confira as classes [Socket](assetId:///T:System.Net.Sockets.Socket?qualifyHint=False&autoUpgrade=True) e [TcpListener](assetId:///T:System.Net.Sockets.TcpListener?qualifyHint=False&autoUpgrade=True).  
  
<a name="client"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 No .NET Framework 4.5, o Windows Presentation Foundation (WPF) contém modificações e aperfeiçoamentos nas seguintes áreas:  
  
-   O novo controle [Ribbon](assetId:///T:System.Windows.Controls.Ribbon.Ribbon?qualifyHint=False&autoUpgrade=True), que permite que você implemente uma interface de usuário da faixa de opções que hospeda uma Barra de Ferramentas de Acesso Rápido, um menu do aplicativo e guias.  
  
-   A nova interface [INotifyDataErrorInfo](assetId:///T:System.ComponentModel.INotifyDataErrorInfo?qualifyHint=False&autoUpgrade=True), que dá suporte à validação de dados síncronos e assíncronos.  
  
-   Novos recursos para as classes [VirtualizingPanel](assetId:///T:System.Windows.Controls.VirtualizingPanel?qualifyHint=False&autoUpgrade=True) e [Dispatcher](assetId:///T:System.Windows.Threading.Dispatcher?qualifyHint=False&autoUpgrade=True).  
  
-   Desempenho melhorado durante a exibição de grandes conjuntos de dados agrupados e o acesso a coleções em threads que não sejam de IU.  
  
-   Associação de dados a propriedades estáticas, associação de dados a tipos personalizados que implementam a interface [ICustomTypeProvider](assetId:///T:System.Reflection.ICustomTypeProvider?qualifyHint=False&autoUpgrade=True) e a recuperação de informações de associação de dados de uma expressão de associação.  
  
-   Reposicionamento de dados à medida que os valores mudam (shaping dinâmico).  
  
-   Capacidade de verificar se o contexto de dados de um contêiner de itens está desconectado.  
  
-   Capacidade de definir o tempo que deve decorrer entre as alterações de propriedade e as atualizações da fonte de dados.  
  
-   Suporte melhorado para implementar padrões de evento fracos. Além disso, os eventos agora podem aceitar extensões de marcação.  
  
<a name="windows_communication_foundation"></a>   
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 No .NET Framework 4.5, os seguintes recursos foram adicionados para simplificar a gravação e a manutenção de aplicativos do Windows Communication Foundation (WCF):  
  
-   Simplificação de arquivos de configuração gerados.  
  
-   Suporte para desenvolvimento de primeiro contrato.  
  
-   Capacidade de configurar o modo de compatibilidade do ASP.NET mais facilmente.  
  
-   Alterações em valores de propriedade de transporte padrão para reduzir a probabilidade de você defini-los.  
  
-   Atualizações feitas na classe [XmlDictionaryReaderQuotas](assetId:///T:System.Xml.XmlDictionaryReaderQuotas?qualifyHint=False&autoUpgrade=True) reduzem a probabilidade de você precisar configurar manualmente as cotas para leitores de dicionário XML.  
  
-   Validação de arquivos de configuração WCF pelo Visual Studio como parte do processo de compilação, de forma que você possa detectar erros de configuração antes de executar o aplicativo.  
  
-   Novo suporte de streaming assíncrono.  
  
-   Novo mapeamento de protocolo HTTPS para facilitar a exposição de um ponto de extremidade em HTTPS com o IIS (Serviços de Informações da Internet).  
  
-   Capacidade de gerar metadados em um único documento WSDL acrescentando `?singleWSDL` à URL de serviço.  
  
-   Suporte de Websockets para habilitar comunicação bidirecional real em portas 80 e 443 com as características de desempenho semelhantes ao transporte TCP.  
  
-   Suporte para configurar serviços no código.  
  
-   Dicas de ferramenta do Editor de XML  
  
-   Suporte ao armazenamento em cache de [ChannelFactory](assetId:///T:System.ServiceModel.ChannelFactory?qualifyHint=False&autoUpgrade=True).  
  
-   Suporte à compactação de codificador binário.  
  
-   Suporte para um transporte UDP que permite que os desenvolvedores gravem serviços que usem o sistema de mensagens "acionar e esquecer". Um cliente envia uma mensagem para um serviço e não espera nenhuma resposta do serviço.  
  
-   Capacidade de dar suporte a vários modos de autenticação em um único ponto de extremidade WCF durante o uso do transporte HTTP e da segurança de transporte.  
  
-   Suporte para serviços WCF que usam IDNs (nomes de domínio internacionalizados).  
  
 Para saber mais, confira [Novidades no Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=228173).  
  
<a name="windows_workflow_foundation"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 No .NET Framework 4.5, vários recursos novos foram adicionados ao Windows Workflow Foundation (WF), incluindo:  
  
-   Os fluxos de trabalho do computador de estado, que foram introduzidos pela primeira vez como parte do .Net Framework 4.0.1 ([Atualização 1 da Plataforma .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=215092)). Essa atualização incluiu várias classes e atividades novas que permitiram que os desenvolvedores criassem fluxos de trabalho de computador do estado. Essas classes e atividades foram atualizadas para que o .NET Framework 4.5 inclua:  
  
    -   A capacidade de definir pontos de interrupção em estados.  
  
    -   A capacidade de copiar e colar transições no designer de fluxo de trabalho.  
  
    -   Suporte de designer para criação de transição do disparador compartilhado.  
  
    -   Atividades para criar fluxos de trabalho de computador de estado, incluindo: [StateMachine](assetId:///T:System.Activities.Statements.StateMachine?qualifyHint=False&autoUpgrade=True), [State](assetId:///T:System.Activities.Statements.State?qualifyHint=False&autoUpgrade=True) e [Transition](assetId:///T:System.Activities.Statements.Transition?qualifyHint=False&autoUpgrade=True).  
  
-   Recursos do Designer de Fluxo de Trabalho aperfeiçoados, como o seguinte:  
  
    -   Capacidades de pesquisa do fluxo de trabalho aperfeiçoado no Visual Studio, incluindo **Localização Rápida** e **Localizar nos Arquivos**.  
  
    -   Capacidade de criar automaticamente uma atividade de Sequência quando uma segunda atividade filho é adicionada a uma atividade de contêiner e de incluir ambas as atividades na atividade de Sequência.  
  
    -   Suporte a movimento panorâmico, o que permite que a parte visível de um fluxo de trabalho seja alterada sem o uso das barras de rolagem.  
  
    -   Uma nova exibição **Estrutura de Tópicos de Documentos** mostra os componentes de um fluxo de trabalho em uma exibição de contorno em estilo árvore e permite selecionar um componente na exibição **Estrutura de Tópicos de Documentos**.  
  
    -   Capacidade de adicionar anotações a atividades.  
  
    -   Capacidade de definir e consumir representantes de atividade usando-se o designer de fluxo de trabalho.  
  
    -   Conexão e inserção automática para atividades e transições na máquina de estado e fluxos de trabalho do fluxograma.  
  
-   Armazenamento das informações do estado de exibição para um fluxo de trabalho em um único elemento no arquivo XAML, logo, você pode localizar e editar facilmente as informações de estado de exibição.  
  
-   Uma atividade de contêiner NoPersistScope para impedir que as atividades filho persistam.  
  
-   Suporte para expressões do C#:  
  
    -   Os projetos de fluxo de trabalho que usam o Visual Basic usarão expressões do Visual Basic e os projetos de fluxo de trabalho do C# usarão as expressões do C#.  
  
    -   Projetos de fluxo de trabalho do C# criados no Visual Studio 2010 e com expressões do Visual Basic são compatíveis com projetos do fluxo de trabalho do C# que usem expressões do C#.  
  
-   Aperfeiçoamentos do controle de versão:  
  
    -   A nova classe [WorkflowIdentity](assetId:///T:System.Activities.WorkflowIdentity?qualifyHint=False&autoUpgrade=True), que fornece um mapeamento entre uma instância mantida de fluxo de trabalho e sua definição de fluxo de trabalho.  
  
    -   Execução lado a lado de várias versões de fluxo de trabalho no mesmo host, incluindo [WorkflowServiceHost](assetId:///T:System.ServiceModel.Activities.WorkflowServiceHost?qualifyHint=False&autoUpgrade=True).  
  
    -   Na Atualização Dinâmica, a capacidade de modificar a definição de uma instância do fluxo de trabalho persistente.  
  
-   Implantação do serviço de fluxo de trabalho de primeiro contrato, que fornece suporte para gerar automaticamente atividades para corresponder um contrato de serviço existente.  
  
 Para saber mais, confira [Novidades no Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=228176).  
  
<a name="tailored"></a>   
### <a name="net-for-windows-8x-store-apps"></a>.NET para aplicativos Windows 8.x Store  
 Os aplicativos Windows 8.x Store foram projetados para fatores forma específicos e aproveitam a capacidade do sistema operacional Windows. Um subconjunto do .NET Framework 4.5 ou 4.5.1 está disponível para compilar aplicativos Windows 8.x Store para o Windows usando o C# ou o Visual Basic. Esse subconjunto é chamado de Windows 8.x Store e abordado em uma [visão geral](http://go.microsoft.com/fwlink/?LinkId=228491) no Centro de Desenvolvimento do Windows.  
  
<a name="portable"></a>   
### <a name="portable-class-libraries"></a>Bibliotecas de Classes Portáteis  
 O projeto Biblioteca de Classes Portátil no Visual Studio 2012 (e em versões posteriores) permite gravar e compilar assemblies gerenciados que funcionem em várias plataformas do .NET Framework. Ao usar um projeto Biblioteca de Classes Portátil, você escolhe as plataformas (como o Windows Phone e aplicativos do .NET para Windows 8.x Store) para direcionar. Os tipos e membros disponíveis em seu projeto são restritos automaticamente aos tipos e membros comuns através dessas plataformas. Para saber mais, confira [Biblioteca de Classes Portátil](../Topic/Cross-Platform%20Development%20with%20the%20Portable%20Class%20Library.md).  
  
## <a name="see-also"></a>Consulte também  
 [O .NET Framework e lançamentos fora da banda](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Novidades no Visual Studio 2013](http://msdn.microsoft.com/library/bb386063\(v=vs.120\).aspx)   
 [ASP.NET 4.5.1 e Ferramentas da Web para Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)   
 [ASP.NET e Visual Studio para Web](../Topic/ASP.NET%20and%20Visual%20Studio%20for%20Web.md)   
 [Novidades no Windows Communication Foundation 4.5](http://go.microsoft.com/fwlink/?LinkId=228173)   
 [Novidades no Windows Foundation Workflow](http://go.microsoft.com/fwlink/?LinkId=228176)   
 [Novidades no Visual C++](http://msdn.microsoft.com/library/hh409293\(v=vs.120\).aspx)

