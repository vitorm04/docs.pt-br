---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937289"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Hospedagem: Redirecionamento HTTPS ativado para aplicativos fora de processo do IIS

A versão 13.0.19218.0 do [ASP.NET Módulo Central (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) para hospedagem via IIS fora de processo permite um recurso de redirecionamento HTTPS existente para ASP.NET aplicativos Core 3.0 e 2.2.

Para discussão, consulte [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O modelo de projeto ASP.NET Core 2.1 introduziu <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> pela <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>primeira vez o suporte para métodos de middleware HTTPS como e . Habilitar o redirecionamento HTTPS exigia a adição da configuração, uma vez que os aplicativos em desenvolvimento não usam a porta padrão do 443. [HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) só está ativo se a solicitação já estiver usando HTTPS. Localhost é ignorado por padrão.

#### <a name="new-behavior"></a>Novo comportamento

Em ASP.NET Núcleo 3.0, o cenário IIS HTTPS foi [aprimorado](https://github.com/dotnet/AspNetCore/pull/4685). Com o aprimoramento, um aplicativo poderia descobrir as `UseHttpsRedirection` portas HTTPS do servidor e fazer funcionar por padrão. O componente em processo realizou `IServerAddresses` a descoberta da porta com o recurso, o que só afeta ASP.NET aplicativos Core 3.0 porque a biblioteca em processo é versionada com a estrutura. O componente fora de processo foi alterado `ASPNETCORE_HTTPS_PORT` para adicionar automaticamente a variável de ambiente. Essa mudança afetou tanto ASP.NET aplicativos Core 2.2 quanto 3.0 porque o componente fora do processo é compartilhado globalmente. ASP.NET os aplicativos Core 2.1 não são afetados porque usam uma versão anterior do ANCM por padrão.

O comportamento anterior foi modificado em ASP.NET Núcleo 3.0.1 e 3.1.0 Preview 3 para reverter as mudanças de comportamento no ASP.NET Core 2.x. Essas alterações afetam apenas os aplicativos fora de processo do IIS.

Como detalhado acima, a instalação ASP.NET Core 3.0.0 teve `UseHttpsRedirection` o efeito colateral de também ativar o middleware em ASP.NET aplicativos Core 2.x. Uma alteração foi feita no ANCM em ASP.NET Core 3.0.1 e 3.1.0 Preview 3 de tal forma que instalá-los não tem mais esse efeito nos aplicativos ASP.NET Core 2.x. A `ASPNETCORE_HTTPS_PORT` variável de ambiente que o ANCM preencheu em `ASPNETCORE_ANCM_HTTPS_PORT` ASP.NET Núcleo 3.0.0 foi alterada para ASP.NET Núcleo 3.0.1 e 3.1.0 Visualização 3. `UseHttpsRedirection`também foi atualizado nessas versões para entender as variáveis novas e antigas. ASP.NET Core 2.x não será atualizado. Como resultado, ele reverte para o comportamento anterior de ser desativado por padrão.

#### <a name="reason-for-change"></a>Motivo da mudança

Funcionalidade melhorada do ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária se você quiser que todos os clientes usem HTTPS. Para permitir que alguns clientes usem HTTP, tome uma das seguintes etapas:

* Remova as `UseHttpsRedirection` chamadas `UseHsts` para e `Startup.Configure` do método do seu projeto e reimplante o aplicativo.
* Em seu arquivo *web.config,* defina a `ASPNETCORE_HTTPS_PORT` variável ambiente como uma seqüência de string vazia. Essa alteração pode ocorrer diretamente no servidor sem reimplantar o aplicativo. Por exemplo: 

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection`ainda pode ser:

* Ativado manualmente em ASP.NET Núcleo 2.x definindo a `ASPNETCORE_HTTPS_PORT` variável ambiente para o número de porta apropriado (443 na maioria dos cenários de produção).
* Desativado em ASP.NET Núcleo 3.x `ASPNETCORE_ANCM_HTTPS_PORT` definindo com um valor de string vazio. Este valor é definido da mesma `ASPNETCORE_HTTPS_PORT` forma que o exemplo anterior.

As máquinas que executam ASP.NET aplicativos Core 3.0.0 devem instalar o tempo de execução do ASP.NET Core 3.0.1 antes de instalar o ASP.NET Core 3.1.0 Preview 3 ANCM. Isso garante que `UseHttpsRedirection` continue funcionando como esperado para os ASP.NET apps Core 3.0.

No Azure App Service, o ANCM implanta em um cronograma separado do tempo de execução devido à sua natureza global. O ANCM foi implantado no Azure com essas alterações depois que ASP.NET Núcleo 3.0.1 e 3.1.0 foram implantados.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
