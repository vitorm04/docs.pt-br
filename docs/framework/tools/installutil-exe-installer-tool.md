---
title: Installutil.exe (Ferramenta de Instalação)
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04074c8120ad2bc4e279ca0c60624bde9d5e42d9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496673"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="1b580-102">Installutil.exe (Ferramenta de Instalação)</span><span class="sxs-lookup"><span data-stu-id="1b580-102">Installutil.exe (Installer Tool)</span></span>

<span data-ttu-id="1b580-103">A ferramenta Instalador é um utilitário de linha de comando que permite instalar e desinstalar recursos de servidor executando-se os componentes do instalador em assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="1b580-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="1b580-104">Essa ferramenta funciona com classes no namespace <xref:System.Configuration.Install>.</span><span class="sxs-lookup"><span data-stu-id="1b580-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>

<span data-ttu-id="1b580-105">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b580-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="1b580-106">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="1b580-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="1b580-107">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1b580-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="1b580-108">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1b580-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="1b580-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b580-109">Syntax</span></span>

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a><span data-ttu-id="1b580-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b580-110">Parameters</span></span>

|<span data-ttu-id="1b580-111">Argumento</span><span class="sxs-lookup"><span data-stu-id="1b580-111">Argument</span></span>|<span data-ttu-id="1b580-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b580-112">Description</span></span>|
|--------------|-----------------|
|`assembly`|<span data-ttu-id="1b580-113">O nome do arquivo do assembly no qual os componentes do instalador devem ser executados.</span><span class="sxs-lookup"><span data-stu-id="1b580-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="1b580-114">Omita esse parâmetro se você quiser especificar o nome forte do assembly usando a opção `/AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="1b580-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|

<a name="options"></a>

## <a name="options"></a><span data-ttu-id="1b580-115">Opções</span><span class="sxs-lookup"><span data-stu-id="1b580-115">Options</span></span>

|<span data-ttu-id="1b580-116">Opção</span><span class="sxs-lookup"><span data-stu-id="1b580-116">Option</span></span>|<span data-ttu-id="1b580-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b580-117">Description</span></span>|
|------------|-----------------|
|`/h[elp]`<br /><br /> <span data-ttu-id="1b580-118">- ou -</span><span class="sxs-lookup"><span data-stu-id="1b580-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="1b580-119">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="1b580-119">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="1b580-120">`/help` *assembly*</span><span class="sxs-lookup"><span data-stu-id="1b580-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="1b580-121">- ou -</span><span class="sxs-lookup"><span data-stu-id="1b580-121">-or-</span></span><br /><br /> <span data-ttu-id="1b580-122">`/?` *assembly*</span><span class="sxs-lookup"><span data-stu-id="1b580-122">`/?` *assembly*</span></span>|<span data-ttu-id="1b580-123">Exibe opções adicionais reconhecidas por instaladores individuais dentro do assembly especificado, com a sintaxe do comando e as opções de InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="1b580-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="1b580-124">Essa opção adiciona o texto retornado pela propriedade <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> de cada componente do instalador para o texto de ajuda de InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="1b580-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|
|<span data-ttu-id="1b580-125">`/AssemblyName` "*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="1b580-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="1b580-126">,Version=*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="1b580-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="1b580-127">,Culture=*locale*</span><span class="sxs-lookup"><span data-stu-id="1b580-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="1b580-128">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="1b580-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="1b580-129">Especifica o nome forte de um assembly, que deve ser registrado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="1b580-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="1b580-130">O nome do assembly deve ser totalmente qualificado com a versão, a cultura e o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="1b580-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="1b580-131">O nome totalmente qualificado deve estar entre aspas.</span><span class="sxs-lookup"><span data-stu-id="1b580-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="1b580-132">Por exemplo, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" é um nome de assembly totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="1b580-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|
|<span data-ttu-id="1b580-133">`/InstallStateDir=[` *directoryName* `]`</span><span class="sxs-lookup"><span data-stu-id="1b580-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="1b580-134">Especifica o diretório do arquivo .InstallState que contém os dados usados para desinstalar o assembly.</span><span class="sxs-lookup"><span data-stu-id="1b580-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="1b580-135">O padrão é o diretório que contém o assembly.</span><span class="sxs-lookup"><span data-stu-id="1b580-135">The default is the directory that contains the assembly.</span></span>|
|<span data-ttu-id="1b580-136">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="1b580-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="1b580-137">Especifica o nome do arquivo de log em que o andamento da instalação é registrado.</span><span class="sxs-lookup"><span data-stu-id="1b580-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="1b580-138">Por padrão, se a opção `/LogFile` for omitida, um arquivo de log chamado *assemblyname*.InstallLog será criado.</span><span class="sxs-lookup"><span data-stu-id="1b580-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="1b580-139">Se *filename* for omitido, nenhum arquivo de log será gerado.</span><span class="sxs-lookup"><span data-stu-id="1b580-139">If *filename* is omitted, no log file is generated.</span></span>|
|<span data-ttu-id="1b580-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="1b580-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="1b580-141">Se `true`, exibirá a saída no console.</span><span class="sxs-lookup"><span data-stu-id="1b580-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="1b580-142">Se `false` (o padrão), suprimirá a saída no console.</span><span class="sxs-lookup"><span data-stu-id="1b580-142">If `false` (the default), suppresses output to the console.</span></span>|
|`/ShowCallStack`|<span data-ttu-id="1b580-143">A saída da pilha de chamadas será para o arquivo de log se ocorrer uma exceção a qualquer momento durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="1b580-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|
|<span data-ttu-id="1b580-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="1b580-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="1b580-145">Desinstala os assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="1b580-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="1b580-146">Diferentemente das outras opções, `/u` se aplica a todos os assemblies, independentemente de onde a opção seja exibida na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1b580-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a><span data-ttu-id="1b580-147">Opções Adicionais do Instalador</span><span class="sxs-lookup"><span data-stu-id="1b580-147">Additional Installer Options</span></span>

<span data-ttu-id="1b580-148">Os instaladores individuais usados em um assembly podem reconhecer opções além das listadas na seção [Opções](#options).</span><span class="sxs-lookup"><span data-stu-id="1b580-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="1b580-149">Para saber mais sobre essas opções, execute InstallUtil.exe com os caminhos dos assemblies na linha de comando com a opção `/?` ou `/help`.</span><span class="sxs-lookup"><span data-stu-id="1b580-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="1b580-150">Para especificar essas opções, você as inclui na linha de comando com as opções reconhecidas por InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="1b580-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="1b580-151">O texto da ajuda nas opções compatíveis com componentes do instalador individuais é retornado pela propriedade <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b580-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1b580-152">As opções individuais que foram inseridas na linha de comando são acessíveis programaticamente com base na propriedade <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b580-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="1b580-153">Todas as opções e os parâmetros de linha de comando são gravados no arquivo de log da instalação.</span><span class="sxs-lookup"><span data-stu-id="1b580-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="1b580-154">No entanto, se você usar o parâmetro `/Password`, reconhecido por alguns componentes do instalador, as informações da senha serão substituídas por oito asteriscos (\*) e não serão exibidas no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="1b580-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b580-155">Em alguns casos, os parâmetros passados para o instalador podem incluir informações confidenciais ou de identificação pessoal que, por padrão, são gravadas em um arquivo de log de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="1b580-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="1b580-156">Para evitar esse comportamento, é possível suprimir o arquivo de log especificando `/LogFile=` (sem nenhum argumento *filename*) após Installutil.exe na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1b580-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b580-157">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b580-157">Remarks</span></span>

<span data-ttu-id="1b580-158">Os aplicativos do .NET Framework consistem em arquivos de programa tradicionais e recursos associados como, por exemplo, filas de mensagens, logs de eventos e contadores de desempenho que devem ser criados quando o aplicativo é implantado.</span><span class="sxs-lookup"><span data-stu-id="1b580-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="1b580-159">É possível usar componentes do instalador de um assembly para criar esses recursos quando o aplicativo é instalado e para removê-los quando o aplicativo é desinstalado.</span><span class="sxs-lookup"><span data-stu-id="1b580-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="1b580-160">Installutil.exe detecta e executa esses componentes do instalador.</span><span class="sxs-lookup"><span data-stu-id="1b580-160">Installutil.exe detects and executes these installer components.</span></span>

<span data-ttu-id="1b580-161">É possível especificar vários assemblies na mesma linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1b580-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="1b580-162">Qualquer opção ocorrida antes de um nome de assembly se aplica à instalação desse assembly.</span><span class="sxs-lookup"><span data-stu-id="1b580-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="1b580-163">Com exceção de `/u` e `/AssemblyName`, as opções são cumulativas, mas substituíveis.</span><span class="sxs-lookup"><span data-stu-id="1b580-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="1b580-164">Ou seja, as opções especificadas para um assembly se aplicam a todos os assemblies subsequentes, a menos que a opção seja especificada com um valor novo.</span><span class="sxs-lookup"><span data-stu-id="1b580-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>

<span data-ttu-id="1b580-165">Se você executar Installutil.exe em um assembly sem especificar nenhuma opção, ele colocará estes três arquivos no diretório do assembly:</span><span class="sxs-lookup"><span data-stu-id="1b580-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>

- <span data-ttu-id="1b580-166">InstallUtil.InstallLog - Contém uma descrição geral do andamento da instalação.</span><span class="sxs-lookup"><span data-stu-id="1b580-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>

- <span data-ttu-id="1b580-167">*assemblyname*.InstallLog – Contém informações específicas para a fase de confirmação do processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="1b580-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="1b580-168">Para obter mais informações sobre a fase de confirmação, consulte o método <xref:System.Configuration.Install.Installer.Commit%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b580-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>

- <span data-ttu-id="1b580-169">*assemblyname*.InstallState – Contém dados usados para desinstalar o assembly.</span><span class="sxs-lookup"><span data-stu-id="1b580-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>

<span data-ttu-id="1b580-170">Installutil.exe usa reflexão para inspecionar os assemblies especificados e encontrar todos os tipos de <xref:System.Configuration.Install.Installer> que têm o atributo <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="1b580-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="1b580-171">Em seguida, a ferramenta executa o método <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> ou <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> em cada instância do tipo de <xref:System.Configuration.Install.Installer>.</span><span class="sxs-lookup"><span data-stu-id="1b580-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="1b580-172">Installutil.exe realiza a instalação de maneira transacional; ou seja, se um dos assemblies não for instalado, ele reverterá as instalações de todos os outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="1b580-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="1b580-173">A desinstalação não é transacional.</span><span class="sxs-lookup"><span data-stu-id="1b580-173">Uninstall is not transactional.</span></span>

<span data-ttu-id="1b580-174">Installutil.exe não pode instalar ou desinstalar assemblies assinados com atraso, mas pode instalar ou desinstalar assemblies de nome forte.</span><span class="sxs-lookup"><span data-stu-id="1b580-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>

<span data-ttu-id="1b580-175">Desde o .NET Framework versão 2.0, a versão 32 bits do CLR (Common Language Runtime) acompanha apenas a versão 32 bits da ferramenta Instalador, mas a versão 64 bits do CLR acompanha as versões 32 e 64 bits da ferramenta Instalador.</span><span class="sxs-lookup"><span data-stu-id="1b580-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="1b580-176">Ao usar o CLR 64 bits, use a ferramenta Instalador 32 bits para instalar assemblies 32 bits, e a ferramenta Instalador 64 bits para instalar assemblies 64 bits e MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="1b580-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="1b580-177">Ambas as versões da ferramenta Instalador se comportam da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="1b580-177">Both versions of the Installer tool behave the same.</span></span>

<span data-ttu-id="1b580-178">Não é possível usar Installutil.exe para implantar um serviço do Windows criado usando-se o C++, porque Installutil.exe pode não reconhecer o código nativo inserido produzido pelo compilador do C++.</span><span class="sxs-lookup"><span data-stu-id="1b580-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="1b580-179">Se você tentar implantar um serviço do Windows do C++ com Installutil.exe como, por exemplo, <xref:System.BadImageFormatException> uma exceção será acionada.</span><span class="sxs-lookup"><span data-stu-id="1b580-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="1b580-180">Para trabalhar com esse cenário, mova o código de serviço para o módulo do C++ e, em seguida, grave o objeto do instalador no C# ou no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b580-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>

## <a name="examples"></a><span data-ttu-id="1b580-181">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1b580-181">Examples</span></span>

<span data-ttu-id="1b580-182">O comando a seguir exibe uma descrição da sintaxe e das opções de comando para InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="1b580-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>

```console
installutil /?
```

<span data-ttu-id="1b580-183">O comando a seguir exibe uma descrição da sintaxe e das opções de comando para InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="1b580-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="1b580-184">Ele também exibirá uma descrição e uma lista de opções com suporte pelos componentes do instalador em `myAssembly.exe` se o texto de ajuda tiver sido atribuído à propriedade <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> do instalador.</span><span class="sxs-lookup"><span data-stu-id="1b580-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>

```console
installutil /? myAssembly.exe
```

<span data-ttu-id="1b580-185">O comando a seguir executa os componentes do instalador no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="1b580-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>

```console
installutil myAssembly.exe
```

<span data-ttu-id="1b580-186">O comando a seguir executa os componentes do instalador em um assembly usando-se a opção `/AssemblyName` e um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="1b580-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="1b580-187">O comando a seguir executa os componentes do instalador em um assembly especificado pelo nome de arquivo e em um assembly especificado pelo nome forte.</span><span class="sxs-lookup"><span data-stu-id="1b580-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="1b580-188">Todos os assemblies especificados pelo nome de arquivo devem anteceder assemblies especificados pelo nome forte na linha de comando, porque a opção `/AssemblyName` não pode ser substituída.</span><span class="sxs-lookup"><span data-stu-id="1b580-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="1b580-189">O comando a seguir executa os componentes do desinstalador no assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="1b580-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>

```console
installutil /u myAssembly.exe
```

<span data-ttu-id="1b580-190">O comando a seguir executa os componentes do desinstalador nos assemblies `myAssembly1.exe` e `myAssembly2.exe`.</span><span class="sxs-lookup"><span data-stu-id="1b580-190">The following command executes the uninstaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

<span data-ttu-id="1b580-191">Como a posição da opção `/u` na linha de comando não é importante, ela equivale ao comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="1b580-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

<span data-ttu-id="1b580-192">O comando a seguir executa os instaladores no assembly `myAssembly.exe` e especifica que as informações de andamento serão gravadas em `myLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="1b580-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

<span data-ttu-id="1b580-193">O comando a seguir executa os instaladores no assembly `myAssembly.exe`, especifica que as informações de andamento devem ser gravadas em `myLog.InstallLog` e usa a opção `/reg` personalizada dos instaladores para especificar que as atualizações devem ser feitas no Registro do sistema.</span><span class="sxs-lookup"><span data-stu-id="1b580-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

<span data-ttu-id="1b580-194">O comando a seguir executa os instaladores no assembly `myAssembly.exe`, usa a opção `/email` personalizada do instalador para especificar o endereço de email do usuário e suprime saída para o arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="1b580-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

<span data-ttu-id="1b580-195">O comando a seguir grava o andamento da instalação de `myAssembly.exe` em `myLog.InstallLog` e grava o andamento de `myTestAssembly.exe` em `myTestLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="1b580-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a><span data-ttu-id="1b580-196">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b580-196">See also</span></span>

- <xref:System.Configuration.Install>
- [<span data-ttu-id="1b580-197">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="1b580-197">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="1b580-198">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="1b580-198">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
