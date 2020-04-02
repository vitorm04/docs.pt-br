---
title: Configuração do aplicativo
description: Aprenda a configurar aplicativos Blazor sem usar o ConfigurationManager.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588242"
---
# <a name="app-configuration"></a>Configuração do aplicativo

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

A principal maneira de carregar a configuração do aplicativo no&mdash;Web Forms é com entradas no arquivo *Web.config* no servidor ou em um arquivo de configuração relacionado referenciado por *web.config*. Você pode usar `ConfigurationManager` o objeto estático para interagir com as configurações do aplicativo, as strings de conexão do repositório de dados e outros provedores de configuração estendida que são adicionados ao aplicativo. É típico ver interações com a configuração do aplicativo como visto no seguinte código:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

Com ASP.NET Core e o Lado do Servidor Blazor, o arquivo *web.config* pode estar presente se o seu aplicativo estiver hospedado em um servidor Windows IIS. No entanto, `ConfigurationManager` não há interação com essa configuração, e você pode receber configuração de aplicativo mais estruturada de outras fontes. Vamos dar uma olhada em como a configuração é coletada e como você ainda pode acessar informações de configuração a partir de um arquivo *web.config.*

## <a name="configuration-sources"></a>Fontes de configuração

ASP.NET Core reconhece que existem muitas fontes de configuração que você pode querer usar para o seu aplicativo. O framework tenta oferecer o melhor desses recursos por padrão. A configuração é lida e agregada a partir dessas várias fontes pelo ASP.NET Core. Valores carregados posteriormente para a mesma chave de configuração têm precedência sobre valores anteriores.

ASP.NET Core foi projetado para ter reconhecimento na nuvem e facilitar a configuração de aplicativos tanto para operadores quanto para desenvolvedores. ASP.NET Core é ambientalmente consciente e sabe `Production` se `Development` está funcionando em seu ambiente ou em seu ambiente. O indicador de ambiente `ASPNETCORE_ENVIRONMENT` é definido na variável ambiente do sistema. Se nenhum valor for configurado, o aplicativo `Production` não será executado no ambiente.

Seu aplicativo pode acionar e adicionar configuração de várias fontes com base no nome do ambiente. Por padrão, a configuração é carregada a partir dos seguintes recursos na ordem listada:

1. *appsettings.json* arquivo, se presente
1. *ajustes. {ENVIRONMENT_NAME}.json,* se presente
1. Arquivo de segredos do usuário em disco, se presente
1. Variáveis de ambiente
1. Argumentos de linha de comando

## <a name="appsettingsjson-format-and-access"></a>appsettings.json formato e acesso

O arquivo *appsettings.json* pode ser hierárquico com valores estruturados como o seguinte JSON:

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

Quando apresentado com o JSON anterior, o sistema de configuração achata os valores da criança e faz referência aos seus caminhos hierárquicos totalmente qualificados. Um caractere`:`de cólon separa cada propriedade na hierarquia. Por exemplo, a `section1:key0` chave `section1` de configuração `key0` acessa o valor do objeto literal.

## <a name="user-secrets"></a>Segredos do usuário

Os segredos do usuário são:

* Valores de configuração armazenados em um arquivo JSON na estação de trabalho do desenvolvedor, fora da pasta de desenvolvimento do aplicativo.
* Só é carregado quando `Development` executado no ambiente.
* Associado a um aplicativo específico.
* Gerenciado com o `user-secrets` comando .NET Core CLI.

Configure seu aplicativo para armazenamento `user-secrets` de segredos executando o comando:

```dotnetcli
dotnet user-secrets init
```

O comando anterior `UserSecretsId` adiciona um elemento ao arquivo do projeto. O elemento contém um GUID, que é usado para associar segredos com o aplicativo. Você pode então definir `set` um segredo com o comando. Por exemplo: 

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

O comando anterior `Parent:ApiKey` disponibiliza a chave de configuração `12345`na estação de trabalho de um desenvolvedor com o valor .

Para obter mais informações sobre como criar, armazenar e gerenciar segredos de usuários, consulte o armazenamento seguro de segredos de aplicativos em desenvolvimento em ASP.NET documento [Core.](/aspnet/core/security/app-secrets)

## <a name="environment-variables"></a>Variáveis de ambiente

O próximo conjunto de valores carregados na configuração do aplicativo são as variáveis de ambiente do sistema. Todas as configurações de variáveis de ambiente do seu sistema estão agora acessíveis a você através da API de configuração. Valores hierárquicos são achatados e separados por caracteres de cólon quando lidos dentro do seu aplicativo. No entanto, alguns sistemas operacionais não permitem nomes de variáveis de ambiente de caracteres de cólon. ASP.NET Core aborda essa limitação convertendo valores que têm sublinhados duplos ()`__`em um cólon quando são acessados. O `Parent:ApiKey` valor da seção segredos do usuário acima `Parent__ApiKey`pode ser substituído com a variável ambiente .

## <a name="command-line-arguments"></a>Argumentos de linha de comando

A configuração também pode ser fornecida como argumentos de linha de comando quando o aplicativo é iniciado. Use a notação`--`de duplo traço`/`() ou forward-slash ( ) para indicar o nome do valor de configuração a definir e o valor a ser configurado. A sintaxe se assemelha aos seguintes comandos:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>O retorno do web.config

Se você implantou seu aplicativo no Windows no IIS, o arquivo *web.config* ainda configura o IIS para gerenciar seu aplicativo. Por padrão, o IIS adiciona uma referência ao ASP.NET Módulo Núcleo (ANCM). ANCM é um módulo IIS nativo que hospeda seu aplicativo no lugar do servidor web Kestrel. Esta seção *web.config* se assemelha à seguinte marcação XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

A configuração específica do aplicativo `environmentVariables` pode ser `aspNetCore` definida aninhando um elemento no elemento. Os valores definidos nesta seção são apresentados ao aplicativo ASP.NET Core como variáveis de ambiente. As variáveis de ambiente carregam adequadamente durante esse segmento de inicialização do aplicativo.

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>Leia a configuração no aplicativo

ASP.NET Core fornece a <xref:Microsoft.Extensions.Configuration.IConfiguration> configuração do aplicativo através da interface. Esta interface de configuração deve ser solicitada por seus componentes Blazor, páginas Blazor e qualquer outra ASP.NET classe gerenciada pelo Core que precise de acesso à configuração. A estrutura ASP.NET Core preencherá automaticamente essa interface com a configuração resolvida configurada anteriormente. Em uma página blazor ou na marcação Razor `IConfiguration` de um `@inject` componente, você pode injetar o objeto com uma diretiva na parte superior do arquivo *.razor* como este:

```razor
@inject IConfiguration Configuration
```

Esta declaração `IConfiguration` anterior torna `Configuration` o objeto disponível como a variável em todo o resto do modelo Razor.

As configurações individuais podem ser lidas especificando a hierarquia de configuração procurada como parâmetro de indexador:

```csharp
var mySetting = Configuration["section1:key0"];
```

Você pode buscar seções de <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> configuração inteiras usando o método para recuperar uma `GetSection("section1")` coleção de chaves em um local específico com uma sintaxe semelhante a recuperar a configuração para a seção1 do exemplo anterior.

## <a name="strongly-typed-configuration"></a>Configuração fortemente digitada

Com o Web Forms, foi possível criar um tipo de <xref:System.Configuration.ConfigurationSection> configuração fortemente digitado que herdou do tipo e tipos associados. A `ConfigurationSection` permitiu configurar algumas regras de negócios e processamento para esses valores de configuração.

Em ASP.NET Core, você pode especificar uma hierarquia de classe que receberá os valores de configuração. Estas classes:

* Não precisa herdar de uma classe de pais.
* Deve `public` incluir propriedades que correspondam às propriedades e referências de tipo para a estrutura de configuração que você deseja capturar.

Para a amostra de *appsettings.json* anterior, você pode definir as seguintes classes para capturar os valores:

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

Esta hierarquia de classe pode ser preenchida adicionando a seguinte linha ao `Startup.ConfigureServices` método:

```csharp
services.Configure<MyConfig>(Configuration);
```

No resto do aplicativo, você pode adicionar um parâmetro `@inject` de entrada às `IOptions<MyConfig>` classes ou uma diretiva em modelos de tipo Razor para receber as configurações fortemente digitadas. A `IOptions<MyConfig>.Value` propriedade produzirá o `MyConfig` valor preenchido a partir das configurações.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Mais informações sobre o recurso Opções podem ser encontradas no [padrão Opções no](/aspnet/core/fundamentals/configuration/options#options-interfaces) documento ASP.NET Core.

>[!div class="step-by-step"]
>[Próximo](middleware.md)
>[anterior](security-authentication-authorization.md)
