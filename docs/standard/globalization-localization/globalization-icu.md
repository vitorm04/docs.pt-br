---
title: Globalização e ICU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: e0ca78871d1ddf851148096c8c6cfd10076763ab
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400873"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="a875a-102">Globalização e ICU do .NET</span><span class="sxs-lookup"><span data-stu-id="a875a-102">.NET globalization and ICU</span></span>

<span data-ttu-id="a875a-103">No passado, as APIs de globalização do .NET usavam diferentes bibliotecas subjacentes em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="a875a-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="a875a-104">No UNIX, as APIs usaram os [componentes internacionais para Unicode (ICU)](http://site.icu-project.org/home)e no Windows, eles usaram [NLS (suporte ao idioma nacional)](/windows/win32/intl/national-language-support).</span><span class="sxs-lookup"><span data-stu-id="a875a-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="a875a-105">Isso resultou em algumas diferenças comportamentais em várias APIs de globalização ao executar aplicativos em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="a875a-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="a875a-106">As diferenças de comportamento foram evidentes nessas áreas:</span><span class="sxs-lookup"><span data-stu-id="a875a-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="a875a-107">Culturas e dados de cultura</span><span class="sxs-lookup"><span data-stu-id="a875a-107">Cultures and culture data</span></span>
- <span data-ttu-id="a875a-108">Maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="a875a-108">String casing</span></span>
- <span data-ttu-id="a875a-109">Classificação e pesquisa de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a875a-109">String sorting and searching</span></span>
- <span data-ttu-id="a875a-110">Chaves de classificação</span><span class="sxs-lookup"><span data-stu-id="a875a-110">Sort keys</span></span>
- <span data-ttu-id="a875a-111">Normalização de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a875a-111">String normalization</span></span>
- <span data-ttu-id="a875a-112">Suporte a IDNs (nomes de domínio internacionalizados)</span><span class="sxs-lookup"><span data-stu-id="a875a-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="a875a-113">Nome de exibição de fuso horário no Linux</span><span class="sxs-lookup"><span data-stu-id="a875a-113">Time zone display name on Linux</span></span>

<span data-ttu-id="a875a-114">A partir do .NET 5,0, os desenvolvedores têm mais controle sobre qual biblioteca subjacente é usada, permitindo que os aplicativos evitem diferenças entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="a875a-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="a875a-115">ICU no Windows</span><span class="sxs-lookup"><span data-stu-id="a875a-115">ICU on Windows</span></span>

<span data-ttu-id="a875a-116">O Windows 10 pode 2019 atualização e as versões posteriores incluem [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) como parte do sistema operacional, e o .NET 5,0 e versões posteriores usam o ICU por padrão.</span><span class="sxs-lookup"><span data-stu-id="a875a-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="a875a-117">Ao executar no Windows, o .NET 5,0 e versões posteriores tentam carregar `icu.dll` e, se estiver disponível, usá-lo para a implementação da globalização.</span><span class="sxs-lookup"><span data-stu-id="a875a-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and, if it's available, use it for the globalization implementation.</span></span> <span data-ttu-id="a875a-118">Se a biblioteca ICU não puder ser encontrada ou carregada, como quando executada em versões mais antigas do Windows, o .NET 5,0 e versões posteriores retornem à implementação baseada em NLS.</span><span class="sxs-lookup"><span data-stu-id="a875a-118">If the ICU library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="a875a-119">Mesmo ao usar o ICU, `CurrentCulture` os `CurrentUICulture` Membros, e `CurrentRegion` ainda usam as APIs do sistema operacional Windows para honrar as configurações do usuário.</span><span class="sxs-lookup"><span data-stu-id="a875a-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="use-nls-instead-of-icu"></a><span data-ttu-id="a875a-120">Usar NLS em vez de ICU</span><span class="sxs-lookup"><span data-stu-id="a875a-120">Use NLS instead of ICU</span></span>

<span data-ttu-id="a875a-121">Usar o ICU em vez do NLS pode resultar em diferenças comportamentais com algumas operações relacionadas à globalização.</span><span class="sxs-lookup"><span data-stu-id="a875a-121">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="a875a-122">Para reverter para o uso do NLS, um desenvolvedor pode recusar a implementação do ICU.</span><span class="sxs-lookup"><span data-stu-id="a875a-122">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="a875a-123">Os aplicativos podem habilitar o modo NLS de qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="a875a-123">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="a875a-124">No arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="a875a-124">In the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="a875a-125">No arquivo `runtimeconfig.json`:</span><span class="sxs-lookup"><span data-stu-id="a875a-125">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.UseNls": true
        }
    }
  }
  ```

- <span data-ttu-id="a875a-126">Definindo a variável de ambiente `DOTNET_SYSTEM_GLOBALIZATION_USENLS` para o valor `true` ou `1` .</span><span class="sxs-lookup"><span data-stu-id="a875a-126">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="a875a-127">Um valor definido no projeto ou no `runtimeconfig.json` arquivo tem precedência sobre a variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="a875a-127">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="a875a-128">Para obter mais informações, consulte [definições de configuração de tempo de execução](../../core/run-time-config/globalization.md#nls).</span><span class="sxs-lookup"><span data-stu-id="a875a-128">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="a875a-129">ICU de aplicativo local</span><span class="sxs-lookup"><span data-stu-id="a875a-129">App-local ICU</span></span>

<span data-ttu-id="a875a-130">Cada versão do ICU pode trazer suas correções de bug de ti, bem como dados de CLDR (repositório de dados de localidade comum) que descrevem os idiomas do mundo.</span><span class="sxs-lookup"><span data-stu-id="a875a-130">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="a875a-131">A movimentação entre versões do ICU pode afetar sutilmente o comportamento do aplicativo quando se trata de operações relacionadas à globalização.</span><span class="sxs-lookup"><span data-stu-id="a875a-131">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span> <span data-ttu-id="a875a-132">Para ajudar os desenvolvedores de aplicativos a garantir a consistência em todas as implantações, o .NET 5,0 e versões posteriores permitem que os aplicativos no Windows e no UNIX executem e usem sua própria cópia do ICU.</span><span class="sxs-lookup"><span data-stu-id="a875a-132">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="a875a-133">Os aplicativos podem aceitar um modo de implementação do ICU local do aplicativo de qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="a875a-133">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="a875a-134">No arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="a875a-134">In  the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
  </ItemGroup>
  ```

- <span data-ttu-id="a875a-135">No arquivo `runtimeconfig.json`:</span><span class="sxs-lookup"><span data-stu-id="a875a-135">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
       }
    }
  }
  ```

- <span data-ttu-id="a875a-136">Definindo a variável de ambiente `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` para o valor `<suffix>:<version>` ou `<version>` .</span><span class="sxs-lookup"><span data-stu-id="a875a-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

  <span data-ttu-id="a875a-137">`<suffix>`: Sufixo opcional com menos de 36 caracteres de comprimento, seguindo as convenções de empacotamento do ICU público.</span><span class="sxs-lookup"><span data-stu-id="a875a-137">`<suffix>`: Optional suffix of fewer than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="a875a-138">Ao criar um ICU personalizado, você pode personalizá-lo para produzir os nomes de lib e os nomes de símbolo exportados para conter um sufixo, por exemplo, `libicuucmyapp` , em que `myapp` é o sufixo.</span><span class="sxs-lookup"><span data-stu-id="a875a-138">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

  <span data-ttu-id="a875a-139">`<version>`: Uma versão do ICU válida, por exemplo, 67,1.</span><span class="sxs-lookup"><span data-stu-id="a875a-139">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="a875a-140">Esta versão é usada para carregar os binários e obter os símbolos exportados.</span><span class="sxs-lookup"><span data-stu-id="a875a-140">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="a875a-141">Para carregar o ICU quando a opção de aplicativo local é definida, o .NET usa o <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> método, que investiga vários caminhos.</span><span class="sxs-lookup"><span data-stu-id="a875a-141">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="a875a-142">O método primeiro tenta localizar a biblioteca na `NATIVE_DLL_SEARCH_DIRECTORIES` propriedade, que é criada pelo host dotnet com base no `deps.json` arquivo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a875a-142">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="a875a-143">Para obter mais informações, consulte [investigação padrão](../../core/dependency-loading/default-probing.md).</span><span class="sxs-lookup"><span data-stu-id="a875a-143">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="a875a-144">Para aplicativos independentes, nenhuma ação especial é exigida pelo usuário, a não ser garantir que o ICU esteja no diretório do aplicativo (para aplicativos independentes, o diretório de trabalho usa como padrão `NATIVE_DLL_SEARCH_DIRECTORIES` ).</span><span class="sxs-lookup"><span data-stu-id="a875a-144">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="a875a-145">Se você estiver consumindo o ICU por meio de um pacote NuGet, isso funcionará em aplicativos dependentes da estrutura.</span><span class="sxs-lookup"><span data-stu-id="a875a-145">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="a875a-146">O NuGet resolve os ativos nativos e os inclui no `deps.json` arquivo e no diretório de saída para o aplicativo no `runtimes` diretório.</span><span class="sxs-lookup"><span data-stu-id="a875a-146">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="a875a-147">O .NET o carrega a partir daí.</span><span class="sxs-lookup"><span data-stu-id="a875a-147">.NET loads it from there.</span></span>

<span data-ttu-id="a875a-148">Para aplicativos dependentes da estrutura (não independentes) em que o ICU é consumido de uma compilação local, você deve executar etapas adicionais.</span><span class="sxs-lookup"><span data-stu-id="a875a-148">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="a875a-149">O SDK do .NET ainda não tem um recurso para binários nativos "flexíveis" a serem incorporados ao `deps.json` (consulte [este problema do SDK](https://github.com/dotnet/sdk/issues/11373)).</span><span class="sxs-lookup"><span data-stu-id="a875a-149">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="a875a-150">Em vez disso, você pode habilitar isso adicionando informações adicionais ao arquivo de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a875a-150">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="a875a-151">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a875a-151">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="a875a-152">Isso deve ser feito para todos os binários do ICU para os tempos de execução com suporte.</span><span class="sxs-lookup"><span data-stu-id="a875a-152">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="a875a-153">Além disso, os `NuGetPackageId` metadados no `RuntimeTargetsCopyLocalItems` grupo de itens precisam corresponder a um pacote NuGet que o projeto realmente referencia.</span><span class="sxs-lookup"><span data-stu-id="a875a-153">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="a875a-154">comportamento do macOS</span><span class="sxs-lookup"><span data-stu-id="a875a-154">macOS behavior</span></span>

<span data-ttu-id="a875a-155">`macOS` tem um comportamento diferente para resolver bibliotecas dinâmicas dependentes dos comandos de carregamento especificados no `match-o` arquivo do que o carregador do Linux.</span><span class="sxs-lookup"><span data-stu-id="a875a-155">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="a875a-156">No carregador do Linux, o .NET pode tentar `libicudata` , `libicuuc` e `libicui18n` (nessa ordem) para satisfazer o grafo de dependências do ICU.</span><span class="sxs-lookup"><span data-stu-id="a875a-156">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="a875a-157">No entanto, no macOS, isso não funciona.</span><span class="sxs-lookup"><span data-stu-id="a875a-157">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="a875a-158">Ao criar o ICU no macOS, você, por padrão, obtém uma biblioteca dinâmica com esses comandos de carregamento no `libicuuc` .</span><span class="sxs-lookup"><span data-stu-id="a875a-158">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="a875a-159">O trecho a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="a875a-159">The following snippet shows an example.</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="a875a-160">Esses comandos apenas referenciam o nome das bibliotecas dependentes para os outros componentes do ICU.</span><span class="sxs-lookup"><span data-stu-id="a875a-160">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="a875a-161">O carregador executa a pesquisa seguindo as `dlopen` convenções, que envolve ter essas bibliotecas nos diretórios do sistema ou definir os `LD_LIBRARY_PATH` VARs de env ou ter o ICU no diretório de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a875a-161">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="a875a-162">Se você não puder definir `LD_LIBRARY_PATH` ou garantir que os binários ICU estejam no diretório de nível de aplicativo, será necessário fazer um trabalho extra.</span><span class="sxs-lookup"><span data-stu-id="a875a-162">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="a875a-163">Há algumas diretivas para o carregador, como `@loader_path` , que dizem ao carregador para pesquisar essa dependência no mesmo diretório que o binário com esse comando de carregamento.</span><span class="sxs-lookup"><span data-stu-id="a875a-163">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="a875a-164">Há duas maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="a875a-164">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="a875a-165">Execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="a875a-165">Run the following commands:</span></span>

  ```bash
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
  install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
  ```

- <span data-ttu-id="a875a-166">Patch ICU para produzir os nomes de instalação `@loader_path`</span><span class="sxs-lookup"><span data-stu-id="a875a-166">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="a875a-167">Antes de executar autoconf ( `./runConfigureICU` ), altere [estas linhas](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) para:</span><span class="sxs-lookup"><span data-stu-id="a875a-167">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

  ```
  LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
  ```

## <a name="icu-on-webassembly"></a><span data-ttu-id="a875a-168">ICU no Webassembly</span><span class="sxs-lookup"><span data-stu-id="a875a-168">ICU on WebAssembly</span></span>

<span data-ttu-id="a875a-169">Uma versão do ICU está disponível especificamente para cargas de trabalho do Webassembly.</span><span class="sxs-lookup"><span data-stu-id="a875a-169">A version of ICU is available that's specifically for WebAssembly workloads.</span></span> <span data-ttu-id="a875a-170">Esta versão fornece compatibilidade de globalização com perfis de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a875a-170">This version provides globalization compatibility with desktop profiles.</span></span> <span data-ttu-id="a875a-171">Para reduzir o tamanho do arquivo de dados ICU de 24 MB a 1,4 MB (ou ~ 0,3 MB se estiver compactado com Brotli), essa carga de trabalho tem algumas limitações.</span><span class="sxs-lookup"><span data-stu-id="a875a-171">To reduce the ICU data file size from 24 MB to 1.4 MB (or ~0.3 MB if compressed with Brotli), this workload has a handful of limitations.</span></span>

<span data-ttu-id="a875a-172">Não há suporte para as seguintes APIs:</span><span class="sxs-lookup"><span data-stu-id="a875a-172">The following APIs are not supported:</span></span>

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

<span data-ttu-id="a875a-173">As seguintes APIs têm suporte com limitações:</span><span class="sxs-lookup"><span data-stu-id="a875a-173">The following APIs are supported with limitations:</span></span>

- <span data-ttu-id="a875a-174"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> e <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> não dão suporte às raramente usadas <xref:System.Text.NormalizationForm.FormKC> e <xref:System.Text.NormalizationForm.FormKD> formulários.</span><span class="sxs-lookup"><span data-stu-id="a875a-174"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> and <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> don't support the rarely used <xref:System.Text.NormalizationForm.FormKC> and <xref:System.Text.NormalizationForm.FormKD> forms.</span></span>
- <span data-ttu-id="a875a-175"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> retorna o mesmo valor que <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a875a-175"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> returns the same value as <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a875a-176">Além disso, uma lista de localidades com suporte pode ser encontrada no [repositório dotnet/ICU](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span><span class="sxs-lookup"><span data-stu-id="a875a-176">In addition, a list of supported locales can be found on the [dotnet/icu repo](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span></span>
