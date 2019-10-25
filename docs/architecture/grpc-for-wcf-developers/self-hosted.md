---
title: Aplicativos gRPC de hospedagem interna – gRPC para desenvolvedores do WCF
description: Implantando ASP.NET Core aplicativos gRPC como serviços hospedados internamente.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4983cad1dd075480c6d83a5350a323ab348cdaaf
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846116"
---
# <a name="self-hosted-grpc-applications"></a>Aplicativos gRPC auto-hospedados

Embora ASP.NET Core aplicativos 3,0 possam ser hospedados no IIS no Windows Server, atualmente não é possível hospedar um aplicativo gRPC no IIS porque ainda não há suporte para algumas das funcionalidades HTTP/2. Essa funcionalidade é esperada em uma atualização futura do Windows Server.

Você pode executar seu aplicativo como um serviço do Windows ou como um serviço do Linux controlado pelo [sistema](https://en.wikipedia.org/wiki/Systemd), graças a alguns recursos novos nas extensões de hospedagem do .net Core 3,0.

## <a name="run-your-app-as-a-windows-service"></a>Executar seu aplicativo como um serviço do Windows

Para configurar seu aplicativo ASP.NET Core para ser executado como um serviço do Windows, instale o pacote [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) do NuGet. Em seguida, adicione uma chamada para `UseWindowsService` ao método `CreateHostBuilder` no `Program.cs`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> Se o aplicativo não estiver sendo executado como um serviço do Windows, o método `UseWindowsService` não fará nada.

Agora, publique seu aplicativo, seja no Visual Studio, clicando com o botão direito do mouse no projeto e escolhendo *publicar* no menu de contexto ou na CLI do .NET Core.

Ao publicar um aplicativo .NET Core, você pode optar por criar uma implantação *dependente da estrutura* ou uma implantação *independente* . As implantações dependentes da estrutura exigem que o tempo de execução compartilhado do .NET Core seja instalado no host onde eles são executados. As implantações independentes são publicadas com uma cópia completa do tempo de execução e da estrutura do .NET Core e podem ser executadas em qualquer host. Para obter mais informações, incluindo as vantagens e desvantagens de cada abordagem, consulte a documentação de [implantação do aplicativo .NET Core](https://docs.microsoft.com/dotnet/core/deploying/) .

Para publicar uma compilação independente do aplicativo que não exige que o tempo de execução do .NET Core 3,0 seja instalado no host, especifique o tempo de execução a ser incluído no aplicativo usando o sinalizador `-r` (ou `--runtime`).

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

Para publicar uma compilação dependente de estrutura, omita o sinalizador `-r`.

```console
dotnet publish -c Release -o ./publish
```

Copie todo o conteúdo do diretório `publish` para uma pasta de instalação e use o [utilitário SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) para criar um serviço do Windows para o executável.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a>Registrar no log de eventos do Windows

O método `UseWindowsService` adiciona automaticamente um provedor de [log](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) que grava mensagens de log no log de eventos do Windows. Você pode configurar o log para esse provedor adicionando uma entrada de `EventLog` à seção `Logging` de `appsettings.json` ou outra fonte de configuração. O nome de origem usado no log de eventos pode ser substituído pela definição de uma propriedade `SourceName` nessas configurações; Se você não especificar um nome, o nome do aplicativo padrão (normalmente, o nome do assembly executável) será usado.

Mais informações sobre o registro em log estão no final deste capítulo.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Execute seu aplicativo como um serviço Linux com o sistema

Para configurar seu aplicativo ASP.NET Core para ser executado como um serviço do Linux (ou *daemon* no linguagem Linux), instale o pacote [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) do NuGet. Em seguida, adicione uma chamada para `UseSystemd` ao método `CreateHostBuilder` no `Program.cs`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> Se o aplicativo não estiver sendo executado como um serviço do Linux, o método `UseSystemd` não fará nada.

Agora, publique seu aplicativo (dependente de estrutura ou independente para o tempo de execução do Linux relevante, por exemplo, `linux-x64`), seja no Visual Studio, clicando com o botão direito do mouse no projeto e escolhendo *publicar* no menu de contexto ou na CLI do .NET Core usando o comando a seguir.

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

Copie todo o conteúdo do diretório `publish` para uma pasta de instalação no host do Linux. O registro do serviço requer um arquivo especial, chamado "arquivo de unidade", a ser adicionado ao diretório `/etc/systemd/system`. Você precisará de permissão de raiz para criar um arquivo nessa pasta. Nomeie o arquivo com o identificador que você deseja `systemd` para usar e a extensão `.service`. Por exemplo, `/etc/systemd/system/myapp.service`.

O arquivo de serviço usa o formato INI, conforme mostrado neste exemplo.

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

A propriedade `Type=notify` informa `systemd` que o aplicativo irá notificá-lo na inicialização e no desligamento. A configuração de `WantedBy=multi-user.target` fará com que o serviço seja iniciado quando o sistema Linux atingir "runlevel 2", o que significa que um shell de vários usuários não gráficos está ativo.

Antes que `systemd` reconheça o serviço, ele precisa recarregar sua configuração. Você controla `systemd` usando o comando `systemctl`. Após o recarregamento, use o subcomando `status` para confirmar se o aplicativo foi registrado com êxito.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Se você tiver configurado o serviço corretamente, a seguinte saída será mostrada:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Use o comando `start` para iniciar o serviço.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> A extensão de `.service` é opcional ao usar `systemctl start`.

Para informar `systemd` iniciar o serviço automaticamente na inicialização do sistema, use o comando `enable`.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Log no diário

O equivalente do Linux do log de eventos do Windows é `journald`, um serviço de sistema de registro em log estruturado que faz parte do `systemd`. As mensagens de log gravadas na saída padrão por um daemon do Linux são gravadas automaticamente no `journald`, portanto, para configurar níveis de log, use a seção `Console` da configuração de log. O método `UseSystemd` host Builder configura automaticamente o formato de saída do console para se adequar ao diário.

Como `journald` é o padrão para os logs do Linux, há uma variedade de ferramentas que se integram a ela, e você pode facilmente rotear logs de `journald` para um sistema de log externo. Trabalhando localmente no host, você pode usar o comando `journalctl` para exibir os logs da linha de comando.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Se você tiver um ambiente de GUI disponível em seu host, alguns visualizadores de log gráficos estarão disponíveis para Linux, como *QJournalctl* e *logs GNOME*.

Para saber mais sobre como consultar o diário do sistema na linha de comando com `journalctl`, consulte [as páginas do manual](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certificados HTTPS para aplicativos de hospedagem interna

Ao executar um aplicativo gRPC em produção, você deve usar um certificado TLS de uma AC (autoridade de certificação) confiável. Essa autoridade de certificação pode ser uma CA pública ou uma interna para sua organização.

Em hosts do Windows, o certificado pode ser carregado de um [repositório de certificados](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) seguro usando a [classe X509Store](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0). A classe `X509Store` também pode ser usada com o armazenamento de chaves OpenSSL em alguns hosts Linux.

Os certificados também podem ser criados usando um dos [construtores X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), seja de um arquivo (por exemplo, um arquivo `.pfx` protegido por uma senha forte) ou de dados binários recuperados de um serviço de armazenamento seguro, como [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) .

O Kestrel pode ser configurado para usar um certificado de duas maneiras: da configuração ou no código.

### <a name="set-https-certificates-using-configuration"></a>Definir certificados HTTPS usando a configuração

A abordagem de configuração requer a definição do caminho para o arquivo de `.pfx` de certificado e a senha na seção de configuração Kestrel. Em `appsettings.json` que teria a seguinte aparência.

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

A senha deve ser fornecida usando uma fonte de configuração segura, como o Azure keyvault ou o cofre do Hashicorp.

Você não deve armazenar senhas não criptografadas em arquivos de configuração.

### <a name="set-https-certificates-in-code"></a>Definir certificados HTTPS no código

Para configurar HTTPS em Kestrel no código, use o método `ConfigureKestrel` em `IWebHostBuilder` na classe `Program`.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

Novamente, a senha para o arquivo de `.pfx` deve ser armazenada e recuperada de uma fonte de configuração segura.

>[!div class="step-by-step"]
>[Anterior](grpc-in-production.md)
>[Próximo](docker.md)
