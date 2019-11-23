---
title: Aplicativos gRPC de hospedagem interna – gRPC para desenvolvedores do WCF
description: Implantando ASP.NET Core aplicativos gRPC como serviços hospedados internamente.
ms.date: 09/02/2019
ms.openlocfilehash: 59f6275dbf85442bca3a98a1521597ef40e9675b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967219"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="0470f-103">Aplicativos gRPC auto-hospedados</span><span class="sxs-lookup"><span data-stu-id="0470f-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="0470f-104">Embora ASP.NET Core aplicativos 3,0 possam ser hospedados no IIS no Windows Server, atualmente não é possível hospedar um aplicativo gRPC no IIS porque ainda não há suporte para algumas das funcionalidades HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="0470f-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't yet supported.</span></span> <span data-ttu-id="0470f-105">Essa funcionalidade é esperada em uma atualização futura do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="0470f-105">This functionality is expected in a future update to Windows Server.</span></span>

<span data-ttu-id="0470f-106">Você pode executar seu aplicativo como um serviço do Windows ou como um serviço do Linux controlado pelo [sistema](https://en.wikipedia.org/wiki/Systemd), graças a alguns recursos novos nas extensões de hospedagem do .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0470f-106">You can run your application as a Windows Service, or as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), thanks to some new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="0470f-107">Executar seu aplicativo como um serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="0470f-107">Run your app as a Windows service</span></span>

<span data-ttu-id="0470f-108">Para configurar seu aplicativo ASP.NET Core para ser executado como um serviço do Windows, instale o pacote [Microsoft. Extensions. Hosting. WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) do NuGet.</span><span class="sxs-lookup"><span data-stu-id="0470f-108">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="0470f-109">Em seguida, adicione uma chamada para `UseWindowsService` ao método `CreateHostBuilder` no `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="0470f-109">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="0470f-110">Se o aplicativo não estiver sendo executado como um serviço do Windows, o método `UseWindowsService` não fará nada.</span><span class="sxs-lookup"><span data-stu-id="0470f-110">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="0470f-111">Agora, publique seu aplicativo, seja no Visual Studio, clicando com o botão direito do mouse no projeto e escolhendo *publicar* no menu de contexto ou na CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0470f-111">Now publish your application, either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI.</span></span>

<span data-ttu-id="0470f-112">Ao publicar um aplicativo .NET Core, você pode optar por criar uma implantação *dependente da estrutura* ou uma implantação *independente* .</span><span class="sxs-lookup"><span data-stu-id="0470f-112">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="0470f-113">As implantações dependentes da estrutura exigem que o tempo de execução compartilhado do .NET Core seja instalado no host onde eles são executados.</span><span class="sxs-lookup"><span data-stu-id="0470f-113">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="0470f-114">As implantações independentes são publicadas com uma cópia completa do tempo de execução e da estrutura do .NET Core e podem ser executadas em qualquer host.</span><span class="sxs-lookup"><span data-stu-id="0470f-114">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="0470f-115">Para obter mais informações, incluindo as vantagens e desvantagens de cada abordagem, consulte a documentação de [implantação do aplicativo .NET Core](https://docs.microsoft.com/dotnet/core/deploying/) .</span><span class="sxs-lookup"><span data-stu-id="0470f-115">For more information, including the advantages and disadvantages of each approach, refer to the [.NET Core application deployment](https://docs.microsoft.com/dotnet/core/deploying/) documentation.</span></span>

<span data-ttu-id="0470f-116">Para publicar uma compilação independente do aplicativo que não exige que o tempo de execução do .NET Core 3,0 seja instalado no host, especifique o tempo de execução a ser incluído no aplicativo usando o sinalizador `-r` (ou `--runtime`).</span><span class="sxs-lookup"><span data-stu-id="0470f-116">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application using the `-r` (or `--runtime`) flag.</span></span>

```console
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="0470f-117">Para publicar uma compilação dependente de estrutura, omita o sinalizador `-r`.</span><span class="sxs-lookup"><span data-stu-id="0470f-117">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```console
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="0470f-118">Copie todo o conteúdo do diretório `publish` para uma pasta de instalação e use o [utilitário SC](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) para criar um serviço do Windows para o executável.</span><span class="sxs-lookup"><span data-stu-id="0470f-118">Copy the complete contents of the `publish` directory to an installation folder, and use the [sc utility](https://docs.microsoft.com/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-windows-event-log"></a><span data-ttu-id="0470f-119">Registrar no log de eventos do Windows</span><span class="sxs-lookup"><span data-stu-id="0470f-119">Log to Windows Event Log</span></span>

<span data-ttu-id="0470f-120">O método `UseWindowsService` adiciona automaticamente um provedor de [log](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) que grava mensagens de log no log de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="0470f-120">The `UseWindowsService` method automatically adds a [Logging](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) provider that writes log messages to the Windows Event Log.</span></span> <span data-ttu-id="0470f-121">Você pode configurar o log para esse provedor adicionando uma entrada de `EventLog` à seção `Logging` de `appsettings.json` ou outra fonte de configuração.</span><span class="sxs-lookup"><span data-stu-id="0470f-121">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or other configuration source.</span></span> <span data-ttu-id="0470f-122">O nome de origem usado no log de eventos pode ser substituído pela definição de uma propriedade `SourceName` nessas configurações; Se você não especificar um nome, o nome do aplicativo padrão (normalmente, o nome do assembly executável) será usado.</span><span class="sxs-lookup"><span data-stu-id="0470f-122">The source name used in Event Log can be overridden by setting a `SourceName` property in these settings; if you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="0470f-123">Mais informações sobre o registro em log estão no final deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="0470f-123">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="0470f-124">Execute seu aplicativo como um serviço Linux com o sistema</span><span class="sxs-lookup"><span data-stu-id="0470f-124">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="0470f-125">Para configurar seu aplicativo ASP.NET Core para ser executado como um serviço do Linux (ou *daemon* no linguagem Linux), instale o pacote [Microsoft. Extensions. Hosting. systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) do NuGet.</span><span class="sxs-lookup"><span data-stu-id="0470f-125">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="0470f-126">Em seguida, adicione uma chamada para `UseSystemd` ao método `CreateHostBuilder` no `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="0470f-126">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="0470f-127">Se o aplicativo não estiver sendo executado como um serviço do Linux, o método `UseSystemd` não fará nada.</span><span class="sxs-lookup"><span data-stu-id="0470f-127">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="0470f-128">Agora, publique seu aplicativo (dependente de estrutura ou independente para o tempo de execução do Linux relevante, por exemplo, `linux-x64`), seja no Visual Studio, clicando com o botão direito do mouse no projeto e escolhendo *publicar* no menu de contexto ou na CLI do .NET Core usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="0470f-128">Now publish your application (either framework-dependent, or self-contained for the relevant Linux runtime, e.g. `linux-x64`), either from Visual Studio by right-clicking the project and choosing *Publish* from the context menu, or from the .NET Core CLI using the following command.</span></span>

```console
dotnet publish -c Release -r linux-x64 -o ./publish
```

<span data-ttu-id="0470f-129">Copie todo o conteúdo do diretório `publish` para uma pasta de instalação no host do Linux.</span><span class="sxs-lookup"><span data-stu-id="0470f-129">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="0470f-130">O registro do serviço requer um arquivo especial, chamado "arquivo de unidade", a ser adicionado ao diretório `/etc/systemd/system`.</span><span class="sxs-lookup"><span data-stu-id="0470f-130">Registering the service requires a special file, called a "unit file", to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="0470f-131">Você precisará de permissão de raiz para criar um arquivo nessa pasta.</span><span class="sxs-lookup"><span data-stu-id="0470f-131">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="0470f-132">Nomeie o arquivo com o identificador que você deseja `systemd` para usar e a extensão `.service`.</span><span class="sxs-lookup"><span data-stu-id="0470f-132">Name the file with the identifier you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="0470f-133">Por exemplo, `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="0470f-133">For example, `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="0470f-134">O arquivo de serviço usa o formato INI, conforme mostrado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="0470f-134">The service file uses INI format, as shown in this example.</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="0470f-135">A propriedade `Type=notify` informa `systemd` que o aplicativo irá notificá-lo na inicialização e no desligamento.</span><span class="sxs-lookup"><span data-stu-id="0470f-135">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="0470f-136">A configuração de `WantedBy=multi-user.target` fará com que o serviço seja iniciado quando o sistema Linux atingir "runlevel 2", o que significa que um shell de vários usuários não gráficos está ativo.</span><span class="sxs-lookup"><span data-stu-id="0470f-136">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2", meaning a non-graphical multi-user shell is active.</span></span>

<span data-ttu-id="0470f-137">Antes que `systemd` reconheça o serviço, ele precisa recarregar sua configuração.</span><span class="sxs-lookup"><span data-stu-id="0470f-137">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="0470f-138">Você controla `systemd` usando o comando `systemctl`.</span><span class="sxs-lookup"><span data-stu-id="0470f-138">You control `systemd` using the `systemctl` command.</span></span> <span data-ttu-id="0470f-139">Após o recarregamento, use o subcomando `status` para confirmar se o aplicativo foi registrado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0470f-139">After reloading, use the `status` subcommand to confirm the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="0470f-140">Se você tiver configurado o serviço corretamente, a seguinte saída será mostrada:</span><span class="sxs-lookup"><span data-stu-id="0470f-140">If you've configured the service correctly, the following output will be shown:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="0470f-141">Use o comando `start` para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0470f-141">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="0470f-142">A extensão de `.service` é opcional ao usar `systemctl start`.</span><span class="sxs-lookup"><span data-stu-id="0470f-142">The `.service` extension is optional when using `systemctl start`.</span></span>

<span data-ttu-id="0470f-143">Para informar `systemd` iniciar o serviço automaticamente na inicialização do sistema, use o comando `enable`.</span><span class="sxs-lookup"><span data-stu-id="0470f-143">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="0470f-144">Log no diário</span><span class="sxs-lookup"><span data-stu-id="0470f-144">Log to journald</span></span>

<span data-ttu-id="0470f-145">O equivalente do Linux do log de eventos do Windows é `journald`, um serviço de sistema de registro em log estruturado que faz parte do `systemd`.</span><span class="sxs-lookup"><span data-stu-id="0470f-145">The Linux equivalent of the Windows Event Log is `journald`, a structured logging system service that is part of `systemd`.</span></span> <span data-ttu-id="0470f-146">As mensagens de log gravadas na saída padrão por um daemon do Linux são gravadas automaticamente no `journald`, portanto, para configurar níveis de log, use a seção `Console` da configuração de log.</span><span class="sxs-lookup"><span data-stu-id="0470f-146">Log messages written to the standard output by a Linux daemon are automatically written to `journald`, so to configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="0470f-147">O método `UseSystemd` host Builder configura automaticamente o formato de saída do console para se adequar ao diário.</span><span class="sxs-lookup"><span data-stu-id="0470f-147">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="0470f-148">Como `journald` é o padrão para os logs do Linux, há uma variedade de ferramentas que se integram a ela, e você pode facilmente rotear logs de `journald` para um sistema de log externo.</span><span class="sxs-lookup"><span data-stu-id="0470f-148">Because `journald` is the standard for Linux logs, there are a variety of tools that integrate with it, and you can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="0470f-149">Trabalhando localmente no host, você pode usar o comando `journalctl` para exibir os logs da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0470f-149">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="0470f-150">Se você tiver um ambiente de GUI disponível em seu host, alguns visualizadores de log gráficos estarão disponíveis para Linux, como *QJournalctl* e *logs GNOME*.</span><span class="sxs-lookup"><span data-stu-id="0470f-150">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="0470f-151">Para saber mais sobre como consultar o diário do sistema na linha de comando com `journalctl`, consulte [as páginas do manual](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="0470f-151">To learn more about querying the systemd journal from the command line with `journalctl`, see [the man pages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="0470f-152">Certificados HTTPS para aplicativos de hospedagem interna</span><span class="sxs-lookup"><span data-stu-id="0470f-152">HTTPS Certificates for self-hosted applications</span></span>

<span data-ttu-id="0470f-153">Ao executar um aplicativo gRPC em produção, você deve usar um certificado TLS de uma AC (autoridade de certificação) confiável.</span><span class="sxs-lookup"><span data-stu-id="0470f-153">When running a gRPC application in production, you should use a TLS certificate from a trusted Certificate Authority (CA).</span></span> <span data-ttu-id="0470f-154">Essa autoridade de certificação pode ser uma CA pública ou uma interna para sua organização.</span><span class="sxs-lookup"><span data-stu-id="0470f-154">This CA could be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="0470f-155">Em hosts do Windows, o certificado pode ser carregado de um [repositório de certificados](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) seguro usando a [classe X509Store](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="0470f-155">On Windows hosts, the certificate may be loaded from a secure [Certificate Store](https://docs.microsoft.com/windows/win32/seccrypto/managing-certificates-with-certificate-stores) using the [X509Store class](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509store?view=netcore-3.0).</span></span> <span data-ttu-id="0470f-156">A classe `X509Store` também pode ser usada com o armazenamento de chaves OpenSSL em alguns hosts Linux.</span><span class="sxs-lookup"><span data-stu-id="0470f-156">The `X509Store` class can also be used with the OpenSSL key-store on some Linux hosts.</span></span>

<span data-ttu-id="0470f-157">Os certificados também podem ser criados usando um dos [construtores X509Certificate2](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), seja de um arquivo (por exemplo, um arquivo `.pfx` protegido por uma senha forte) ou de dados binários recuperados de um serviço de armazenamento seguro, como [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="0470f-157">Certificates may also be created using one of the [X509Certificate2 constructors](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates.x509certificate.-ctor?view=netcore-3.0), either from a file (for example a `.pfx` file protected by a strong password), or from binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="0470f-158">O Kestrel pode ser configurado para usar um certificado de duas maneiras: da configuração ou no código.</span><span class="sxs-lookup"><span data-stu-id="0470f-158">Kestrel can be configured to use a certificate in two ways: from configuration, or in code.</span></span>

### <a name="set-https-certificates-using-configuration"></a><span data-ttu-id="0470f-159">Definir certificados HTTPS usando a configuração</span><span class="sxs-lookup"><span data-stu-id="0470f-159">Set HTTPS certificates using configuration</span></span>

<span data-ttu-id="0470f-160">A abordagem de configuração requer a definição do caminho para o arquivo de `.pfx` de certificado e a senha na seção de configuração Kestrel.</span><span class="sxs-lookup"><span data-stu-id="0470f-160">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="0470f-161">Em `appsettings.json` que teria a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="0470f-161">In `appsettings.json` that would look like this.</span></span>

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

<span data-ttu-id="0470f-162">A senha deve ser fornecida usando uma fonte de configuração segura, como o Azure keyvault ou o cofre do Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="0470f-162">The password should be provided using a secure configuration source such as Azure KeyVault or Hashicorp Vault.</span></span>

<span data-ttu-id="0470f-163">Você não deve armazenar senhas não criptografadas em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="0470f-163">You SHOULD NOT store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="0470f-164">Definir certificados HTTPS no código</span><span class="sxs-lookup"><span data-stu-id="0470f-164">Set HTTPS certificates in code</span></span>

<span data-ttu-id="0470f-165">Para configurar HTTPS em Kestrel no código, use o método `ConfigureKestrel` em `IWebHostBuilder` na classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="0470f-165">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="0470f-166">Novamente, a senha para o arquivo de `.pfx` deve ser armazenada e recuperada de uma fonte de configuração segura.</span><span class="sxs-lookup"><span data-stu-id="0470f-166">Again, the password for the `.pfx` file should be stored in and retrieved from a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0470f-167">[Anterior](grpc-in-production.md)
>[Próximo](docker.md)</span><span class="sxs-lookup"><span data-stu-id="0470f-167">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
