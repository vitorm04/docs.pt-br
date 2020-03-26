---
title: Aplicativos gRPC auto-hospedados - gRPC para desenvolvedores WCF
description: Implantação de ASP.NET principais aplicativos gRPC como serviços auto-hospedados.
ms.date: 09/02/2019
ms.openlocfilehash: 69f70e4077247fd07eba7abeee82f257dd1f4f90
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110900"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="d412c-103">Aplicativos gRPC auto-hospedados</span><span class="sxs-lookup"><span data-stu-id="d412c-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="d412c-104">Embora ASP.NET aplicativos Core 3.0 possam ser hospedados no IIS no Windows Server, atualmente não é possível hospedar um aplicativo gRPC no IIS porque algumas das funcionalidades HTTP/2 não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="d412c-104">Although ASP.NET Core 3.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="d412c-105">Essa funcionalidade é uma meta para uma futura atualização para o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d412c-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="d412c-106">Você pode executar seu aplicativo como um serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="d412c-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="d412c-107">Ou você pode executá-lo como um serviço Linux controlado por [sistema,](https://en.wikipedia.org/wiki/Systemd)devido a novos recursos nas extensões de hospedagem .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d412c-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET Core 3.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="d412c-108">Execute seu aplicativo como um serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="d412c-108">Run your app as a Windows service</span></span>

<span data-ttu-id="d412c-109">Para configurar o aplicativo ASP.NET Core para ser executado como um serviço do Windows, instale o pacote [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) da NuGet.</span><span class="sxs-lookup"><span data-stu-id="d412c-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="d412c-110">Em seguida, `UseWindowsService` adicione `CreateHostBuilder` uma `Program.cs`chamada ao método em .</span><span class="sxs-lookup"><span data-stu-id="d412c-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="d412c-111">Se o aplicativo não estiver sendo executado `UseWindowsService` como um serviço do Windows, o método não fará nada.</span><span class="sxs-lookup"><span data-stu-id="d412c-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="d412c-112">Agora publique seu aplicativo usando um desses métodos:</span><span class="sxs-lookup"><span data-stu-id="d412c-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="d412c-113">No Visual Studio clicando com o botão direito do mouse no projeto e selecionando **Publish** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="d412c-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="d412c-114">Do .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="d412c-114">From the .NET Core CLI.</span></span>

<span data-ttu-id="d412c-115">Quando você publica um aplicativo .NET Core, você pode optar por criar uma implantação *dependente da estrutura* ou uma implantação *independente.*</span><span class="sxs-lookup"><span data-stu-id="d412c-115">When you publish a .NET Core application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="d412c-116">As implantações dependentes de framework exigem que o .NET Core Shared Runtime seja instalado no host onde são executados.</span><span class="sxs-lookup"><span data-stu-id="d412c-116">Framework-dependent deployments require the .NET Core Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="d412c-117">As implantações independentes são publicadas com uma cópia completa do tempo de execução e da estrutura do .NET Core e podem ser executadas em qualquer host.</span><span class="sxs-lookup"><span data-stu-id="d412c-117">Self-contained deployments are published with a complete copy of the .NET Core runtime and framework and can be run on any host.</span></span> <span data-ttu-id="d412c-118">Para obter mais informações, incluindo as vantagens e desvantagens de cada abordagem, consulte a documentação de implantação do [aplicativo .NET Core.](../../core/deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="d412c-118">For more information, including the advantages and disadvantages of each approach, see the [.NET Core application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="d412c-119">Para publicar uma compilação independente do aplicativo que não exija que o tempo de execução do .NET Core 3.0 seja instalado no host, especifique o tempo de execução a ser incluído no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d412c-119">To publish a self-contained build of the application that does not require the .NET Core 3.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="d412c-120">Use `-r` a `--runtime`(ou) bandeira.</span><span class="sxs-lookup"><span data-stu-id="d412c-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="d412c-121">Para publicar uma compilação dependente da `-r` estrutura, omita a bandeira.</span><span class="sxs-lookup"><span data-stu-id="d412c-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="d412c-122">Copie o conteúdo `publish` completo do diretório para uma pasta de instalação.</span><span class="sxs-lookup"><span data-stu-id="d412c-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="d412c-123">Em seguida, use a [ferramenta sc](/windows/desktop/services/controlling-a-service-using-sc) para criar um serviço do Windows para o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="d412c-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="d412c-124">Faça login no registro de eventos do Windows</span><span class="sxs-lookup"><span data-stu-id="d412c-124">Log to the Windows event log</span></span>

<span data-ttu-id="d412c-125">O `UseWindowsService` método adiciona automaticamente um provedor [de registro](/aspnet/core/fundamentals/logging/) que grava mensagens de registro no registro de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="d412c-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="d412c-126">Você pode configurar o registro para `EventLog` este `Logging` provedor `appsettings.json` adicionando uma entrada na seção de ou outra fonte de configuração.</span><span class="sxs-lookup"><span data-stu-id="d412c-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="d412c-127">Você pode substituir o nome de origem usado `SourceName` no registro de eventos definindo uma propriedade nessas configurações.</span><span class="sxs-lookup"><span data-stu-id="d412c-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="d412c-128">Se você não especificar um nome, o nome padrão do aplicativo (normalmente o nome de montagem executável) será usado.</span><span class="sxs-lookup"><span data-stu-id="d412c-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="d412c-129">Mais informações sobre o registro estão no final deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="d412c-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="d412c-130">Execute seu aplicativo como um serviço Linux com sistema</span><span class="sxs-lookup"><span data-stu-id="d412c-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="d412c-131">Para configurar seu aplicativo ASP.NET Core para ser executado como um serviço Linux (ou *daemon* no Linux), instale o pacote [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) do NuGet.</span><span class="sxs-lookup"><span data-stu-id="d412c-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="d412c-132">Em seguida, `UseSystemd` adicione `CreateHostBuilder` uma `Program.cs`chamada ao método em .</span><span class="sxs-lookup"><span data-stu-id="d412c-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

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
> <span data-ttu-id="d412c-133">Se o aplicativo não estiver sendo executado `UseSystemd` como um serviço Linux, o método não fará nada.</span><span class="sxs-lookup"><span data-stu-id="d412c-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="d412c-134">Agora publique seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d412c-134">Now publish your application.</span></span> <span data-ttu-id="d412c-135">O aplicativo pode ser dependente de estrutura ou independente para o `linux-x64`tempo de execução do Linux relevante (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="d412c-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="d412c-136">Você pode publicar usando um desses métodos:</span><span class="sxs-lookup"><span data-stu-id="d412c-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="d412c-137">No Visual Studio clicando com o botão direito do mouse no projeto e selecionando **Publish** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="d412c-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="d412c-138">A partir do .NET Core CLI, usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d412c-138">From the .NET Core CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="d412c-139">Copie o conteúdo `publish` completo do diretório para uma pasta de instalação no host Linux.</span><span class="sxs-lookup"><span data-stu-id="d412c-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="d412c-140">O registro do serviço requer um arquivo especial, chamado `/etc/systemd/system` de arquivo *unitário,* para ser adicionado ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d412c-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="d412c-141">Você precisará de permissão de raiz para criar um arquivo nesta pasta.</span><span class="sxs-lookup"><span data-stu-id="d412c-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="d412c-142">Nomeie o arquivo com `systemd` o identificador `.service` que deseja usar e a extensão.</span><span class="sxs-lookup"><span data-stu-id="d412c-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="d412c-143">Por exemplo, use `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="d412c-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="d412c-144">O arquivo de serviço usa o formato INI, como mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="d412c-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="d412c-145">O `Type=notify` imóvel `systemd` informa que o aplicativo irá notificá-lo sobre inicialização e desligamento.</span><span class="sxs-lookup"><span data-stu-id="d412c-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="d412c-146">A `WantedBy=multi-user.target` configuração fará com que o serviço seja inicializado quando o sistema Linux atingir o "runlevel 2", o que significa que um shell não gráfico e multiusuário está ativo.</span><span class="sxs-lookup"><span data-stu-id="d412c-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="d412c-147">Antes `systemd` de reconhecer o serviço, ele precisa recarregar sua configuração.</span><span class="sxs-lookup"><span data-stu-id="d412c-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="d412c-148">Você `systemd` controla `systemctl` usando o comando.</span><span class="sxs-lookup"><span data-stu-id="d412c-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="d412c-149">Após a recarga, use o `status` subcomando para confirmar se o aplicativo foi registrado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="d412c-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="d412c-150">Se você configurou o serviço corretamente, você terá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d412c-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="d412c-151">Use `start` o comando para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="d412c-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="d412c-152">A `.service` extensão é opcional `systemctl start`quando você está usando .</span><span class="sxs-lookup"><span data-stu-id="d412c-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="d412c-153">Para `systemd` dizer para iniciar o serviço automaticamente `enable` na inicialização do sistema, use o comando.</span><span class="sxs-lookup"><span data-stu-id="d412c-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="d412c-154">Log para diário</span><span class="sxs-lookup"><span data-stu-id="d412c-154">Log to journald</span></span>

<span data-ttu-id="d412c-155">O equivalente ao Linux do `journald`registro de eventos do Windows é `systemd`, um serviço de sistema de registro estruturado que faz parte de .</span><span class="sxs-lookup"><span data-stu-id="d412c-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="d412c-156">As mensagens de log escritas na saída padrão por `journald`um daemon Linux são automaticamente escritas para .</span><span class="sxs-lookup"><span data-stu-id="d412c-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="d412c-157">Para configurar os níveis `Console` de registro, use a seção da configuração de registro.</span><span class="sxs-lookup"><span data-stu-id="d412c-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="d412c-158">O `UseSystemd` método host builder configura automaticamente o formato de saída do console para se adequar ao diário.</span><span class="sxs-lookup"><span data-stu-id="d412c-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="d412c-159">Porque `journald` é o padrão para logs Linux, uma variedade de ferramentas se integram a ele.</span><span class="sxs-lookup"><span data-stu-id="d412c-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="d412c-160">Você pode facilmente direcionar `journald` logs de um sistema de registro externo.</span><span class="sxs-lookup"><span data-stu-id="d412c-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="d412c-161">Trabalhando localmente no host, `journalctl` você pode usar o comando para exibir logs da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d412c-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="d412c-162">Se você tiver um ambiente de GUI disponível no seu host, alguns espectadores de log gráfico estão disponíveis para Linux, como *QJournalctl* e *gnomo-logs*.</span><span class="sxs-lookup"><span data-stu-id="d412c-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="d412c-163">Para saber mais sobre `systemd` como consultar o diário `journalctl`a partir da linha de comando usando , consulte [as páginas de homem](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="d412c-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="d412c-164">Certificados HTTPS para aplicativos auto-hospedados</span><span class="sxs-lookup"><span data-stu-id="d412c-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="d412c-165">Quando você está executando um aplicativo gRPC em produção, você deve usar um certificado TLS de uma autoridade de certificado confiável (CA).</span><span class="sxs-lookup"><span data-stu-id="d412c-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="d412c-166">Este CA pode ser um CA público, ou um interno para sua organização.</span><span class="sxs-lookup"><span data-stu-id="d412c-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="d412c-167">Nos hosts do Windows, você pode carregar o <xref:System.Security.Cryptography.X509Certificates.X509Store> certificado de uma loja de [certificados](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) seguro usando a classe.</span><span class="sxs-lookup"><span data-stu-id="d412c-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="d412c-168">Você também pode `X509Store` usar a classe com a loja de chaves OpenSSL em alguns hosts Linux.</span><span class="sxs-lookup"><span data-stu-id="d412c-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="d412c-169">Você também pode criar certificados usando um dos [construtores X509Certificate2,](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)de qualquer um:</span><span class="sxs-lookup"><span data-stu-id="d412c-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="d412c-170">Um arquivo, como `.pfx` um arquivo protegido por uma senha forte</span><span class="sxs-lookup"><span data-stu-id="d412c-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="d412c-171">Dados binários recuperados de um serviço de armazenamento seguro, como [o Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="d412c-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="d412c-172">Você pode configurar o Kestrel para usar um certificado de duas maneiras: a partir da configuração ou em código.</span><span class="sxs-lookup"><span data-stu-id="d412c-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="d412c-173">Defina certificados HTTPS usando a configuração</span><span class="sxs-lookup"><span data-stu-id="d412c-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="d412c-174">A abordagem de configuração `.pfx` requer a definição do caminho para o arquivo de certificado e a senha na seção de configuração do Kestrel.</span><span class="sxs-lookup"><span data-stu-id="d412c-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="d412c-175">Em `appsettings.json`, que seria assim:</span><span class="sxs-lookup"><span data-stu-id="d412c-175">In `appsettings.json`, that would look like this:</span></span>

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

<span data-ttu-id="d412c-176">Forneça a senha usando uma fonte de configuração segura, como o Azure Key Vault ou o Hashicorp Vault.</span><span class="sxs-lookup"><span data-stu-id="d412c-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d412c-177">Não armazene senhas não criptografadas em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="d412c-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="d412c-178">Defina certificados HTTPS em código</span><span class="sxs-lookup"><span data-stu-id="d412c-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="d412c-179">Para configurar HTTPS no Código Kestrel, `IWebHostBuilder` use `Program` o `ConfigureKestrel` método ligado na classe.</span><span class="sxs-lookup"><span data-stu-id="d412c-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

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

<span data-ttu-id="d412c-180">Novamente, certifique-se de armazenar `.pfx` a senha do arquivo e recuperá-la de uma fonte de configuração segura.</span><span class="sxs-lookup"><span data-stu-id="d412c-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d412c-181">[Próximo](grpc-in-production.md)
>[anterior](docker.md)</span><span class="sxs-lookup"><span data-stu-id="d412c-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
