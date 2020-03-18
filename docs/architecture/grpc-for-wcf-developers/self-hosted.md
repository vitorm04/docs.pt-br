---
title: Aplicativos gRPC auto-hospedados - gRPC para desenvolvedores WCF
description: Implantação de ASP.NET principais aplicativos gRPC como serviços auto-hospedados.
ms.date: 09/02/2019
ms.openlocfilehash: 00fb1453e19a02469f80af79672e0c1f72c7280f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147796"
---
# <a name="self-hosted-grpc-applications"></a>Aplicativos gRPC auto-hospedados

Embora ASP.NET aplicativos Core 3.0 possam ser hospedados no IIS no Windows Server, atualmente não é possível hospedar um aplicativo gRPC no IIS porque algumas das funcionalidades HTTP/2 não são suportadas. Essa funcionalidade é uma meta para uma futura atualização para o Windows Server.

Você pode executar seu aplicativo como um serviço do Windows. Ou você pode executá-lo como um serviço Linux controlado por [sistema,](https://en.wikipedia.org/wiki/Systemd)devido a novos recursos nas extensões de hospedagem .NET Core 3.0.

## <a name="run-your-app-as-a-windows-service"></a>Execute seu aplicativo como um serviço do Windows

Para configurar o aplicativo ASP.NET Core para ser executado como um serviço do Windows, instale o pacote [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) da NuGet. Em seguida, `UseWindowsService` adicione `CreateHostBuilder` uma `Program.cs`chamada ao método em .

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
> Se o aplicativo não estiver sendo executado `UseWindowsService` como um serviço do Windows, o método não fará nada.

Agora publique seu aplicativo usando um desses métodos:

* No Visual Studio clicando com o botão direito do mouse no projeto e selecionando **Publish** no menu de atalho.
* Do .NET Core CLI.

Quando você publica um aplicativo .NET Core, você pode optar por criar uma implantação *dependente da estrutura* ou uma implantação *independente.* As implantações dependentes de framework exigem que o .NET Core Shared Runtime seja instalado no host onde são executados. As implantações independentes são publicadas com uma cópia completa do tempo de execução e da estrutura do .NET Core e podem ser executadas em qualquer host. Para obter mais informações, incluindo as vantagens e desvantagens de cada abordagem, consulte a documentação de implantação do [aplicativo .NET Core.](../../core/deploying/index.md)

Para publicar uma compilação independente do aplicativo que não exija que o tempo de execução do .NET Core 3.0 seja instalado no host, especifique o tempo de execução a ser incluído no aplicativo. Use `-r` a `--runtime`(ou) bandeira.

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

Para publicar uma compilação dependente da `-r` estrutura, omita a bandeira.

```dotnetcli
dotnet publish -c Release -o ./publish
```

Copie o conteúdo `publish` completo do diretório para uma pasta de instalação. Em seguida, use a [ferramenta sc](/windows/desktop/services/controlling-a-service-using-sc) para criar um serviço do Windows para o arquivo executável.

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Faça login no registro de eventos do Windows

O `UseWindowsService` método adiciona automaticamente um provedor [de registro](/aspnet/core/fundamentals/logging/) que grava mensagens de registro no registro de eventos do Windows. Você pode configurar o registro para `EventLog` este `Logging` provedor `appsettings.json` adicionando uma entrada na seção de ou outra fonte de configuração.

Você pode substituir o nome de origem usado `SourceName` no registro de eventos definindo uma propriedade nessas configurações. Se você não especificar um nome, o nome padrão do aplicativo (normalmente o nome de montagem executável) será usado.

Mais informações sobre o registro estão no final deste capítulo.

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Execute seu aplicativo como um serviço Linux com sistema

Para configurar seu aplicativo ASP.NET Core para ser executado como um serviço Linux (ou *daemon* no Linux), instale o pacote [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) do NuGet. Em seguida, `UseSystemd` adicione `CreateHostBuilder` uma `Program.cs`chamada ao método em .

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
> Se o aplicativo não estiver sendo executado `UseSystemd` como um serviço Linux, o método não fará nada.

Agora publique seu aplicativo. O aplicativo pode ser dependente de estrutura ou independente para o `linux-x64`tempo de execução do Linux relevante (por exemplo, ). Você pode publicar usando um desses métodos:

* No Visual Studio clicando com o botão direito do mouse no projeto e selecionando **Publish** no menu de atalho.
* A partir do .NET Core CLI, usando o seguinte comando:

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
Copie o conteúdo `publish` completo do diretório para uma pasta de instalação no host Linux. O registro do serviço requer um arquivo especial, chamado `/etc/systemd/system` de arquivo *unitário,* para ser adicionado ao diretório. Você precisará de permissão de raiz para criar um arquivo nesta pasta. Nomeie o arquivo com `systemd` o identificador `.service` que deseja usar e a extensão. Por exemplo, use `/etc/systemd/system/myapp.service`.

O arquivo de serviço usa o formato INI, como mostrado neste exemplo:

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

O `Type=notify` imóvel `systemd` informa que o aplicativo irá notificá-lo sobre inicialização e desligamento. A `WantedBy=multi-user.target` configuração fará com que o serviço seja inicializado quando o sistema Linux atingir o "runlevel 2", o que significa que um shell multiusuário não gráfico está ativo.

Antes `systemd` de reconhecer o serviço, ele precisa recarregar sua configuração. Você `systemd` controla `systemctl` usando o comando. Após a recarga, use o `status` subcomando para confirmar se o aplicativo foi registrado com sucesso.

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

Se você configurou o serviço corretamente, você terá a seguinte saída:

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

Use `start` o comando para iniciar o serviço.

```console
sudo systemctl start myapp.service
```

> [!TIP]
> A `.service` extensão é opcional `systemctl start`quando você está usando .

Para `systemd` dizer para iniciar o serviço automaticamente `enable` na inicialização do sistema, use o comando.

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Log para diário

O equivalente ao Linux do `journald`registro de eventos do Windows é `systemd`, um serviço de sistema de registro estruturado que faz parte de . As mensagens de log escritas na saída padrão por `journald`um daemon Linux são automaticamente escritas para . Para configurar os níveis `Console` de registro, use a seção da configuração de registro. O `UseSystemd` método host builder configura automaticamente o formato de saída do console para se adequar ao diário.

Porque `journald` é o padrão para logs Linux, uma variedade de ferramentas se integram a ele. Você pode facilmente direcionar `journald` logs de um sistema de registro externo. Trabalhando localmente no host, `journalctl` você pode usar o comando para exibir logs da linha de comando.

```console
sudo journalctl -u myapp
```

> [!TIP]
> Se você tiver um ambiente de GUI disponível no seu host, alguns espectadores de log gráfico estão disponíveis para Linux, como *QJournalctl* e *gnomo-logs*.

Para saber mais sobre `systemd` como consultar o diário `journalctl`a partir da linha de comando usando , consulte [as páginas do homem](https://manpages.debian.org/buster/systemd/journalctl.1).

## <a name="https-certificates-for-self-hosted-applications"></a>Certificados HTTPS para aplicativos auto-hospedados

Quando você está executando um aplicativo gRPC em produção, você deve usar um certificado TLS de uma autoridade de certificado confiável (CA). Este CA pode ser um CA público, ou um interno para sua organização.

Nos hosts do Windows, você pode carregar o <xref:System.Security.Cryptography.X509Certificates.X509Store> certificado de uma loja de [certificados](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) seguro usando a classe. Você também pode `X509Store` usar a classe com a loja de chaves OpenSSL em alguns hosts Linux.

Você também pode criar certificados usando um dos [construtores X509Certificate2,](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)de qualquer um:

* Um arquivo, como `.pfx` um arquivo protegido por uma senha forte
* Dados binários recuperados de um serviço de armazenamento seguro, como [o Azure Key Vault](https://azure.microsoft.com/services/key-vault/)

Você pode configurar o Kestrel para usar um certificado de duas maneiras: a partir da configuração ou em código.

### <a name="set-https-certificates-by-using-configuration"></a>Defina certificados HTTPS usando a configuração

A abordagem de configuração `.pfx` requer a definição do caminho para o arquivo de certificado e a senha na seção de configuração do Kestrel. Em `appsettings.json`, que seria assim:

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

Forneça a senha usando uma fonte de configuração segura, como o Azure Key Vault ou o Hashicorp Vault.

> [!IMPORTANT]
> Não armazene senhas não criptografadas em arquivos de configuração.

### <a name="set-https-certificates-in-code"></a>Defina certificados HTTPS em código

Para configurar HTTPS no Código Kestrel, `IWebHostBuilder` use `Program` o `ConfigureKestrel` método ligado na classe.

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

Novamente, certifique-se de armazenar `.pfx` a senha do arquivo e recuperá-la de uma fonte de configuração segura.

>[!div class="step-by-step"]
>[Próximo](grpc-in-production.md)
>[anterior](docker.md)
