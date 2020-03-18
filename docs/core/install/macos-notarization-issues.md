---
title: Trabalhando com nota nota notardo pelo macOS Catalina
description: Como lidar com problemas de autenticação e certificado com macOS quando você instala o tempo de execução do .NET Core, SDK e aplicativos construídos com o .NET Core.
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146743"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina Notarization e o impacto em downloads e projetos do .NET Core

A partir do macOS Catalina (versão 10.15), todos os softwares construídos após 1º de junho de 2019, e distribuídos com o Developer ID, devem ser autenticados em cartório. Esse requisito se aplica ao tempo de execução do .NET Core, .NET Core SDK e software criado com o .NET Core. Este artigo descreve os cenários comuns que você pode enfrentar com a autenticação de nota notsio.

## <a name="installing-net-core"></a>Instalando o .NET Core

Os instaladores das versões .NET Core (tempo de execução e SDK) 3.1, 3.0 e 2.1, foram reconhecidos em cartório desde 18 de fevereiro de 2020. As versões lançadas anteriormente não são autenticadas em cartório. Você pode instalar manualmente uma versão não autenticada do .NET Core baixando `sudo installer` primeiro o instalador e, em seguida, usando o comando. Para obter mais informações, consulte [Baixar e instalar manualmente para macOS](sdk.md?pivots=os-macos#download-and-manually-install).

Começando com as seguintes versões, os instaladores .NET Core são autenticados em cartório:

- Runtime do .NET Core
  - 2.1.16
  - 3.0.3
  - 3.1.2

- SDK do .Net Core
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost é desativado por padrão

Por padrão, versões não autenticadas do .NET Core SDK 3.0 e acima produzem um executável Mach-O nativo (conhecido como **appHost)** quando seu projeto compila, publica ou é executado. Este executável é uma maneira conveniente de executar o seu aplicativo. Caso contrário, seu aplicativo deve `dotnet <filename.dll>`ser iniciado executando . Quando o appHost está `dotnet run` ativado, o comando é invocado no contexto do appHost. Para obter mais informações, consulte [Contexto do aplicativoHost](#context-of-the-apphost).

Começando com as versões autenticadas do .NET Core SDK 3.0 e acima, o aplicativoHost executável não é gerado por padrão. Você pode ativar a geração [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) appHost com a configuração booleana no arquivo do projeto. Você também pode alternar o `-p:UseAppHost` aplicativoHost com o parâmetro `dotnet` na linha de comando para o comando específico executado:

- Arquivo de projeto

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parâmetro de linha de comando

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Um aplicativoHost é sempre criado quando você publica seu aplicativo [independente](../deploying/index.md#publish-self-contained).

Para obter mais `UseAppHost` informações sobre a configuração, consulte [as propriedades MSBuild para Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="context-of-the-apphost"></a>Contexto do appHost

Quando o appHost está ativado em seu `dotnet run` projeto e você usa o comando para executar seu aplicativo, o aplicativo é invocado `dotnet` no contexto do appHost e não no host padrão (o host padrão é o comando). Se o aplicativoHost estiver desativado `dotnet run` em seu projeto, o comando será executado no contexto do host padrão. Mesmo que o aplicativoHost esteja desativado, publicar seu aplicativo como autônomo gera um aplicativoExecutável host, e os usuários usam esse executável para executar seu aplicativo. Executar seu `dotnet <filename.dll>` aplicativo com invoca o aplicativo com o host padrão, o tempo de execução compartilhado.

Quando um aplicativo usando o aplicativoHost é invocado, a partição de certificado acessada pelo aplicativo é diferente do host padrão autenticado em cartório. Se o aplicativo tiver que acessar os certificados `dotnet run` instalados através do host padrão, use `dotnet <filename.dll>` o comando para executar seu aplicativo a partir de seu arquivo de projeto ou use o comando para iniciar o aplicativo diretamente.

Mais informações sobre esse cenário são fornecidas na seção [ASP.NET Core e macOS e certificados.](#aspnet-core-and-macos-and-certificates)

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core e macOS e certificados

O .NET Core oferece a capacidade de gerenciar certificados no chaveiro macOS com a <xref:System.Security.Cryptography.X509Certificates> classe. O acesso ao chaveiro macOS usa a identidade dos aplicativos como chave principal ao decidir qual partição considerar. Por exemplo, aplicativos não assinados armazenam segredos na partição não assinada, mas aplicativos assinados armazenam seus segredos em partições que só eles podem acessar. A fonte de execução que invoca seu aplicativo decide qual partição usar.

O .NET Core fornece três fontes de execução: [appHost,](#apphost-is-disabled-by-default)host padrão (o `dotnet` comando) e um host personalizado. Cada modelo de execução pode ter identidades diferentes, assinadas ou não, e tem acesso a diferentes partições dentro do Chaveiro. Os certificados importados por um modo podem não estar acessíveis de outro. Por exemplo, as versões autenticadas em cartório do .NET Core têm um host padrão que é assinado. Os certificados são importados para uma partição segura com base em sua identidade. Esses certificados não estão acessíveis a partir de um aplicativo geradoHost, pois o aplicativoHost não está assinado.

Outro exemplo, por padrão, ASP.NET O Core importa um certificado SSL padrão através do host padrão. ASP.NET Os aplicativos Core que usam um aplicativoHost não terão acesso a este certificado e receberão um erro quando o .NET Core detectar que o certificado não está acessível. A mensagem de erro fornece instruções sobre como corrigir este problema.

Se o compartilhamento de certificadofor necessário, `security` o macOS fornecerá opções de configuração com o utilitário.

Para obter mais informações sobre como solucionar problemas ASP.NET problemas de certificado Core, consulte [Impor HTTPS no ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).

## <a name="default-entitlements"></a>Direitos padrão

O host padrão do .NET Core (o `dotnet` comando) tem um conjunto de direitos padrão. Esses direitos são necessários para o bom funcionamento do .NET Core. É possível que sua aplicação precise de direitos adicionais, nesse caso você precisará gerar e usar um [appHost](#apphost-is-disabled-by-default) e, em seguida, adicionar os direitos necessários localmente.

Conjunto padrão de direitos para .NET Core:

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Nota notar um aplicativo .NET Core

Se você quiser que seu aplicativo seja executado no macOS Catalina (versão 10.15) ou superior, você vai querer autenticar seu aplicativo. O aplicativoHost que você envia com seu pedido de autenticação de cartório deve ser usado com pelo menos os [mesmos direitos padrão](#default-entitlements) do .NET Core.

## <a name="next-steps"></a>Próximas etapas

- [.NET Core dependências e requisitos](dependencies.md).
- [Instale o .NET Core SDK](sdk.md).
- [Instale o tempo de execução do .NET Core](runtime.md)
