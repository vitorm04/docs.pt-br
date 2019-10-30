---
title: Como criar uma política de editor
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 346671d4febd5f3999f1f4fbf2fe4b7e475ae5fa
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040188"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="c415d-102">Como criar uma política de editor</span><span class="sxs-lookup"><span data-stu-id="c415d-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="c415d-103">Os fornecedores de assemblies podem declarar que os aplicativos devem usar uma versão mais recente de um assembly, incluindo um arquivo de política do Publicador com o assembly atualizado.</span><span class="sxs-lookup"><span data-stu-id="c415d-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="c415d-104">O arquivo de política do Publicador especifica as configurações de redirecionamento de assembly e base de código e usa o mesmo formato que um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c415d-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="c415d-105">O arquivo de política do Publicador é compilado em um assembly e colocado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="c415d-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="c415d-106">Há três etapas envolvidas na criação de uma política de editor:</span><span class="sxs-lookup"><span data-stu-id="c415d-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="c415d-107">Crie um arquivo de política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="c415d-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="c415d-108">Crie um assembly de política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="c415d-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="c415d-109">Adicione o assembly de política do Publicador ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="c415d-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="c415d-110">O esquema para a política do Publicador é descrito em [redirecionar versões de assembly](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="c415d-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="c415d-111">O exemplo a seguir mostra um arquivo de política do Publicador que redireciona uma versão do `myAssembly` para outra.</span><span class="sxs-lookup"><span data-stu-id="c415d-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="c415d-112">Para saber como especificar uma base de código, consulte [especificando o local de um assembly](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="c415d-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="c415d-113">Criando o assembly de política do Publicador</span><span class="sxs-lookup"><span data-stu-id="c415d-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="c415d-114">Use o [vinculador de assembly (al. exe)](../tools/al-exe-assembly-linker.md) para criar o assembly de política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="c415d-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="c415d-115">Para criar um assembly de política do Publicador</span><span class="sxs-lookup"><span data-stu-id="c415d-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="c415d-116">Digite o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="c415d-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="c415d-117">Neste comando:</span><span class="sxs-lookup"><span data-stu-id="c415d-117">In this command:</span></span>

- <span data-ttu-id="c415d-118">O argumento `publisherPolicyFile` é o nome do arquivo de política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="c415d-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="c415d-119">O argumento `publisherPolicyAssemblyFile` é o nome do assembly de política do Publicador que resulta desse comando.</span><span class="sxs-lookup"><span data-stu-id="c415d-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="c415d-120">O nome do arquivo de assembly deve seguir o formato:</span><span class="sxs-lookup"><span data-stu-id="c415d-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="c415d-121">' Policy. majorNumber. minorNumber. mainAssemblyName. dll '</span><span class="sxs-lookup"><span data-stu-id="c415d-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="c415d-122">O argumento `keyPairFile` é o nome do arquivo que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="c415d-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="c415d-123">Você deve assinar o assembly e o assembly da política do Publicador com o mesmo par de chaves.</span><span class="sxs-lookup"><span data-stu-id="c415d-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="c415d-124">O argumento `processorArchitecture` identifica a plataforma de destino de um assembly específico do processador.</span><span class="sxs-lookup"><span data-stu-id="c415d-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c415d-125">A capacidade de direcionar uma arquitetura de processador específica está disponível a partir do .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c415d-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="c415d-126">A capacidade de direcionar uma arquitetura de processador específica está disponível a partir do .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c415d-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="c415d-127">O comando a seguir cria um assembly de política do publicador chamado `policy.1.0.myAssembly` de um arquivo de política do publicador chamado `pub.config`, atribui um nome forte ao assembly usando o par de chaves no arquivo `sgKey.snk` e especifica que o assembly tem como alvo o processador x86 arquitectura.</span><span class="sxs-lookup"><span data-stu-id="c415d-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="c415d-128">O assembly de política do Publicador deve corresponder à arquitetura de processador do assembly ao qual ele se aplica.</span><span class="sxs-lookup"><span data-stu-id="c415d-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="c415d-129">Portanto, se o assembly tiver um valor <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> de <xref:System.Reflection.ProcessorArchitecture.MSIL>, o assembly de política de editor para esse assembly deverá ser criado com `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="c415d-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="c415d-130">Você deve fornecer um assembly de política de Publicador separado para cada assembly específico de processador.</span><span class="sxs-lookup"><span data-stu-id="c415d-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="c415d-131">Uma consequência dessa regra é que, para alterar a arquitetura do processador de um assembly, você deve alterar o componente principal ou secundário do número de versão, para que você possa fornecer um novo assembly de política de Publicador com a arquitetura de processador correta.</span><span class="sxs-lookup"><span data-stu-id="c415d-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="c415d-132">O antigo assembly de política do Publicador não pode atender ao seu assembly depois que o assembly tem uma arquitetura de processador diferente.</span><span class="sxs-lookup"><span data-stu-id="c415d-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="c415d-133">Outra consequência é que o vinculador da versão 2,0 não pode ser usado para criar um assembly de política do Publicador para um assembly compilado usando versões anteriores do .NET Framework, porque ele sempre especifica a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="c415d-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="c415d-134">Adicionando o assembly de política do Publicador ao cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="c415d-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="c415d-135">Use a [ferramenta global assembly cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) para adicionar o assembly de política do Publicador ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="c415d-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="c415d-136">Para adicionar o assembly de política do Publicador ao cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="c415d-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="c415d-137">Digite o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="c415d-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="c415d-138">O comando a seguir adiciona `policy.1.0.myAssembly.dll` ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="c415d-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="c415d-139">O assembly de política do Publicador não pode ser adicionado ao cache de assembly global, a menos que o arquivo de política original do Publicador esteja localizado no mesmo diretório que o assembly.</span><span class="sxs-lookup"><span data-stu-id="c415d-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="c415d-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c415d-140">See also</span></span>

- [<span data-ttu-id="c415d-141">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="c415d-141">Programming with Assemblies</span></span>](../../standard/assembly/program.md)
- [<span data-ttu-id="c415d-142">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="c415d-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c415d-143">Configurando aplicativos usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c415d-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="c415d-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c415d-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="c415d-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c415d-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="c415d-146">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="c415d-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
