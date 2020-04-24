---
title: Como criar uma política de editor
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646056"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="59c42-102">Como criar uma política de editor</span><span class="sxs-lookup"><span data-stu-id="59c42-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="59c42-103">Os fornecedores de assembléias podem afirmar que os aplicativos devem usar uma versão mais recente de um conjunto, incluindo um arquivo de diretiva de editor com o conjunto atualizado.</span><span class="sxs-lookup"><span data-stu-id="59c42-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="59c42-104">O arquivo de diretiva do editor especifica o redirecionamento de montagem e as configurações de base de código e usa o mesmo formato de um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59c42-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="59c42-105">O arquivo de diretiva do editor é compilado em uma montagem e colocado no cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="59c42-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="59c42-106">Existem três etapas envolvidas na criação de uma política de editores:</span><span class="sxs-lookup"><span data-stu-id="59c42-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="59c42-107">Crie um arquivo de política de editor.</span><span class="sxs-lookup"><span data-stu-id="59c42-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="59c42-108">Crie uma montagem de política de editores.</span><span class="sxs-lookup"><span data-stu-id="59c42-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="59c42-109">Adicione a montagem da diretiva do editor ao cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="59c42-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="59c42-110">O esquema para a política do editor é descrito no [Redirecionamento de Versões de Montagem](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="59c42-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="59c42-111">O exemplo a seguir mostra um arquivo de `myAssembly` diretiva de editor que redireciona uma versão para outra.</span><span class="sxs-lookup"><span data-stu-id="59c42-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="59c42-112">Para saber como especificar uma base de código, consulte [Especificando a localização de um conjunto](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="59c42-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="59c42-113">Criando a Assembléia de Políticas de Editores</span><span class="sxs-lookup"><span data-stu-id="59c42-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="59c42-114">Use o [Linker de montagem (Al.exe)](../tools/al-exe-assembly-linker.md) para criar a montagem da diretiva do editor.</span><span class="sxs-lookup"><span data-stu-id="59c42-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="59c42-115">Para criar uma montagem de política de editores</span><span class="sxs-lookup"><span data-stu-id="59c42-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="59c42-116">Digite o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="59c42-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="59c42-117">Neste comando:</span><span class="sxs-lookup"><span data-stu-id="59c42-117">In this command:</span></span>

- <span data-ttu-id="59c42-118">O `publisherPolicyFile` argumento é o nome do arquivo de política do editor.</span><span class="sxs-lookup"><span data-stu-id="59c42-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="59c42-119">O `publisherPolicyAssemblyFile` argumento é o nome da assembléia de política do editor que resulta deste comando.</span><span class="sxs-lookup"><span data-stu-id="59c42-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="59c42-120">O nome do arquivo de montagem deve seguir o formato:</span><span class="sxs-lookup"><span data-stu-id="59c42-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="59c42-121">'policy.majorNumber.minorNumber.mainAssemblyName.dll'</span><span class="sxs-lookup"><span data-stu-id="59c42-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="59c42-122">O `keyPairFile` argumento é o nome do arquivo que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="59c42-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="59c42-123">Você deve assinar a montagem e a montagem da política do editor com o mesmo par de chaves.</span><span class="sxs-lookup"><span data-stu-id="59c42-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="59c42-124">O `processorArchitecture` argumento identifica a plataforma direcionada por um conjunto específico do processador.</span><span class="sxs-lookup"><span data-stu-id="59c42-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="59c42-125">A capacidade de segmentar uma arquitetura específica de processador está disponível a partir do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="59c42-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="59c42-126">A capacidade de segmentar uma arquitetura específica de processador está disponível a partir do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="59c42-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="59c42-127">O comando a seguir cria `policy.1.0.myAssembly` uma montagem de `pub.config`diretiva de editor chamada a partir de `sgKey.snk` um arquivo de diretiva de editor chamado, atribui um nome forte ao conjunto usando o par de chaves no arquivo e especifica que o conjunto tem como alvo a arquitetura do processador x86.</span><span class="sxs-lookup"><span data-stu-id="59c42-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="59c42-128">A montagem da diretiva do editor deve corresponder à arquitetura do processador do conjunto a que se aplica.</span><span class="sxs-lookup"><span data-stu-id="59c42-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="59c42-129">Assim, se a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> sua <xref:System.Reflection.ProcessorArchitecture.MSIL>montagem tiver um valor de , a `/platform:anycpu`montagem da política do editor para essa montagem deve ser criada com .</span><span class="sxs-lookup"><span data-stu-id="59c42-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="59c42-130">Você deve fornecer uma montagem de diretiva de editor separada para cada conjunto específico do processador.</span><span class="sxs-lookup"><span data-stu-id="59c42-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="59c42-131">Uma conseqüência desta regra é que, para alterar a arquitetura do processador para um conjunto, você deve alterar o componente principal ou menor do número da versão, para que você possa fornecer um novo conjunto de políticas de editor com a arquitetura correta do processador.</span><span class="sxs-lookup"><span data-stu-id="59c42-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="59c42-132">A antiga montagem de diretiva de editor não pode atender seu conjunto uma vez que seu conjunto tenha uma arquitetura de processador diferente.</span><span class="sxs-lookup"><span data-stu-id="59c42-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="59c42-133">Outra conseqüência é que o linker versão 2.0 não pode ser usado para criar um conjunto de políticas de editorpara um conjunto compilado usando versões anteriores do .NET Framework, porque ele sempre especifica a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="59c42-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="59c42-134">Adicionando a Assembléia de Políticas de Editores ao Cache de Montagem Global</span><span class="sxs-lookup"><span data-stu-id="59c42-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="59c42-135">Use a [ferramenta Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para adicionar a montagem da diretiva do editor ao cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="59c42-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="59c42-136">Para adicionar a montagem da diretiva do editor ao cache de montagem global</span><span class="sxs-lookup"><span data-stu-id="59c42-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="59c42-137">Digite o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="59c42-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="59c42-138">O comando `policy.1.0.myAssembly.dll` a seguir adiciona-se ao cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="59c42-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="59c42-139">A montagem da diretiva do editor não pode ser adicionada ao `/link` cache de montagem global, a menos que o arquivo de diretiva de editor original especificado no argumento esteja localizado no mesmo diretório da montagem.</span><span class="sxs-lookup"><span data-stu-id="59c42-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="59c42-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="59c42-140">See also</span></span>

- [<span data-ttu-id="59c42-141">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="59c42-141">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="59c42-142">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="59c42-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="59c42-143">Configurando aplicativos usando arquivos de configuração </span><span class="sxs-lookup"><span data-stu-id="59c42-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="59c42-144">Esquema de configurações em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="59c42-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="59c42-145">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="59c42-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="59c42-146">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="59c42-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
