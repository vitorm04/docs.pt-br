---
title: Configuração de tempo de execução
description: Saiba como configurar aplicativos .NET Core usando as definições de configuração de tempo de execução.
ms.date: 11/13/2019
ms.openlocfilehash: 2665026347e94d26026821beb2bfcf8441f755f6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801921"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="45d77-103">Definições de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="45d77-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="45d77-104">O .NET Core dá suporte ao uso de arquivos de configuração e variáveis de ambiente para configurar o comportamento de aplicativos .NET Core em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="45d77-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="45d77-105">A configuração de tempo de execução é uma opção atraente se:</span><span class="sxs-lookup"><span data-stu-id="45d77-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="45d77-106">Você não possui ou controla o código-fonte de um aplicativo e, portanto, não é possível configurá-lo programaticamente.</span><span class="sxs-lookup"><span data-stu-id="45d77-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="45d77-107">Várias instâncias do seu aplicativo são executadas ao mesmo tempo em um único sistema e você deseja configurar cada uma para obter um desempenho ideal.</span><span class="sxs-lookup"><span data-stu-id="45d77-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="45d77-108">Esta documentação é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="45d77-108">This documentation is a work in progress.</span></span> <span data-ttu-id="45d77-109">Se você observar que as informações apresentadas aqui estão incompletas ou imprecisas, [abra um problema](https://github.com/dotnet/docs/issues) para nos informar sobre ela ou [envie uma solicitação de pull](https://github.com/dotnet/docs/pulls) para resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="45d77-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="45d77-110">Para obter informações sobre como enviar solicitações pull para o repositório dotnet/docs, consulte o [Guia do colaborador](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="45d77-110">For information on submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="45d77-111">O .NET Core fornece os seguintes mecanismos para configurar aplicativos em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="45d77-111">.NET Core provides the following mechanisms for configuring applications at run time:</span></span>

- <span data-ttu-id="45d77-112">O [arquivo runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="45d77-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="45d77-113">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="45d77-113">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="45d77-114">Os artigos nesta seção da documentação incluem são organizados por categoria, por exemplo, depuração e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="45d77-114">The articles in this section of the documentation include are organized by category, for example, debugging and garbage collection.</span></span> <span data-ttu-id="45d77-115">Quando aplicável, as opções de configuração são mostradas para *runtimeconfig. JSON* (somente no .NET Core), *app. config* (somente .NET Framework) e variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="45d77-115">Where applicable, configuration options are shown for *runtimeconfig.json* (.NET Core only), *app.config* (.NET Framework only), and environment variables.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="45d77-116">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="45d77-116">runtimeconfig.json</span></span>

<span data-ttu-id="45d77-117">Especifique as opções de configuração de tempo de execução na seção **configproperties** do arquivo *runtimeconfig. JSON* do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45d77-117">Specify run-time configuration options in the **configProperties** section of the app's *runtimeconfig.json* file.</span></span> <span data-ttu-id="45d77-118">Esta seção tem o formato:</span><span class="sxs-lookup"><span data-stu-id="45d77-118">This section has the form:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

<span data-ttu-id="45d77-119">Este é um arquivo de exemplo:</span><span class="sxs-lookup"><span data-stu-id="45d77-119">Here is an example file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

<span data-ttu-id="45d77-120">O arquivo *runtimeconfig. JSON* é criado automaticamente no diretório de compilação pelo comando [dotnet Build](../tools/dotnet-build.md) .</span><span class="sxs-lookup"><span data-stu-id="45d77-120">The *runtimeconfig.json* file is automatically created in the build directory by the [dotnet build](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="45d77-121">Ele também é criado quando você seleciona a opção de menu **Build** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45d77-121">It's also created when you select the **Build** menu option in Visual Studio.</span></span> <span data-ttu-id="45d77-122">Em seguida, você pode editar o arquivo depois de ele ser criado.</span><span class="sxs-lookup"><span data-stu-id="45d77-122">You can then edit the file once it's created.</span></span>

<span data-ttu-id="45d77-123">Alguns valores de configuração também podem ser definidos programaticamente chamando o método <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45d77-123">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="45d77-124">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="45d77-124">Environment variables</span></span>

<span data-ttu-id="45d77-125">As variáveis de ambiente podem ser usadas para fornecer algumas informações de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="45d77-125">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="45d77-126">Os botões de configuração especificados como variáveis de ambiente geralmente têm o prefixo **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="45d77-126">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="45d77-127">Você pode definir variáveis de ambiente no painel de controle do Windows, na linha de comando ou programaticamente chamando o método <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> em sistemas baseados no Windows e no UNIX.</span><span class="sxs-lookup"><span data-stu-id="45d77-127">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="45d77-128">Os exemplos a seguir mostram como definir uma variável de ambiente na linha de comando:</span><span class="sxs-lookup"><span data-stu-id="45d77-128">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
