---
title: 'Como: Criar uma política de editor'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3969f066c0a17424d2c4527d2b4661b30f5bb6d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530519"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="06c81-102">Como: Criar uma política de editor</span><span class="sxs-lookup"><span data-stu-id="06c81-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="06c81-103">Os fornecedores de assemblies podem declarar que os aplicativos devem usar uma versão mais recente de um assembly, incluindo um arquivo de política do publicador com o assembly atualizado.</span><span class="sxs-lookup"><span data-stu-id="06c81-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="06c81-104">O arquivo de política de publicador Especifica as configurações de base de código e redirecionamento de assembly e usa o mesmo formato que o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06c81-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="06c81-105">O arquivo de política de publicador é compilado em um assembly e colocado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="06c81-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="06c81-106">Há três etapas envolvidas na criação de uma política de editor:</span><span class="sxs-lookup"><span data-stu-id="06c81-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="06c81-107">Crie um arquivo de política do publicador.</span><span class="sxs-lookup"><span data-stu-id="06c81-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="06c81-108">Crie um assembly de política do publicador.</span><span class="sxs-lookup"><span data-stu-id="06c81-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="06c81-109">Adicione o assembly de política do publicador para o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="06c81-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="06c81-110">O esquema para a política de editor é descrito na [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="06c81-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="06c81-111">O exemplo a seguir mostra um editor de arquivo de política que redireciona uma versão do `myAssembly` para outro.</span><span class="sxs-lookup"><span data-stu-id="06c81-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
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
  
 <span data-ttu-id="06c81-112">Para saber como especificar uma base de código, consulte [especificando o local do Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="06c81-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="06c81-113">Criar o Assembly de política do publicador</span><span class="sxs-lookup"><span data-stu-id="06c81-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="06c81-114">Use o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para criar o assembly de política do publicador.</span><span class="sxs-lookup"><span data-stu-id="06c81-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="06c81-115">Para criar um assembly de política do publicador</span><span class="sxs-lookup"><span data-stu-id="06c81-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="06c81-116">Digite o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="06c81-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="06c81-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="06c81-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="06c81-118">Neste comando:</span><span class="sxs-lookup"><span data-stu-id="06c81-118">In this command:</span></span>  
  
    -   <span data-ttu-id="06c81-119">O *publisherPolicyFile* argumento é o nome do arquivo de política de publicador.</span><span class="sxs-lookup"><span data-stu-id="06c81-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="06c81-120">O *publisherPolicyAssemblyFile* argumento é o nome do assembly da diretiva de editor que é o resultado desse comando.</span><span class="sxs-lookup"><span data-stu-id="06c81-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="06c81-121">O nome de arquivo do assembly deve seguir o formato:</span><span class="sxs-lookup"><span data-stu-id="06c81-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="06c81-122">**policy.**</span><span class="sxs-lookup"><span data-stu-id="06c81-122">**policy.**</span></span> <span data-ttu-id="06c81-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="06c81-123">*majorNumber* **.**</span></span> <span data-ttu-id="06c81-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="06c81-124">*minorNumber* **.**</span></span> <span data-ttu-id="06c81-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="06c81-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="06c81-126">O *keyPairFile* argumento é o nome do arquivo que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="06c81-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="06c81-127">Você deve assinar o assembly e o assembly de política do publicador com o mesmo par de chaves.</span><span class="sxs-lookup"><span data-stu-id="06c81-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="06c81-128">O *processorArchitecture* argumento identifica a plataforma de destino por um assembly específico do processador.</span><span class="sxs-lookup"><span data-stu-id="06c81-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="06c81-129">A capacidade de direcionar uma arquitetura de processador específico é nova no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="06c81-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="06c81-130">O comando a seguir cria um assembly de política de publicador chamado `policy.1.0.myAssembly` de um arquivo de política de publicador chamado `pub.config`, atribui um nome forte ao assembly usando o par de chaves no `sgKey.snk` de arquivo e especifica que o assembly é destinado a x86 arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="06c81-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="06c81-131">O assembly de política do publicador deve corresponder à arquitetura do processador do assembly que ele se aplica ao.</span><span class="sxs-lookup"><span data-stu-id="06c81-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="06c81-132">Portanto, se seu assembly tiver um <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valor de <xref:System.Reflection.ProcessorArchitecture.MSIL>, o assembly de política de publicador para esse assembly deve ser criado com `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="06c81-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="06c81-133">Você deve fornecer um separado assembly de política de publicador para cada assembly específico do processador.</span><span class="sxs-lookup"><span data-stu-id="06c81-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="06c81-134">Uma consequência dessa regra é que, para alterar a arquitetura do processador para um assembly, você deve alterar o componente principal ou secundário do número de versão, para que você pode fornecer um novo assembly de política do publicador com a arquitetura de processador correta.</span><span class="sxs-lookup"><span data-stu-id="06c81-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="06c81-135">O assembly de política de publicador antigo não pode atender a seu assembly depois que o assembly tem uma arquitetura de processador diferente.</span><span class="sxs-lookup"><span data-stu-id="06c81-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="06c81-136">Outra consequência é que o vinculador versão 2.0 não pode ser usado para criar um assembly de política de publicador para um assembly compilado usando versões anteriores do .NET Framework, pois ele sempre Especifica a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="06c81-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="06c81-137">Adicionando o Assembly de política do publicador para o Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="06c81-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="06c81-138">Use o [ferramenta de Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) para adicionar o assembly de política de publicador para o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="06c81-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="06c81-139">Para adicionar o assembly de política de publicador para o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="06c81-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="06c81-140">Digite o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="06c81-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="06c81-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="06c81-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="06c81-142">O comando a seguir adiciona `policy.1.0.myAssembly.dll` ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="06c81-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="06c81-143">O assembly de política do publicador não pode ser adicionado ao cache de assembly global, a menos que o arquivo de política do publicador original está localizado no mesmo diretório que o assembly.</span><span class="sxs-lookup"><span data-stu-id="06c81-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c81-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06c81-144">See also</span></span>
- [<span data-ttu-id="06c81-145">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="06c81-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="06c81-146">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="06c81-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="06c81-147">Configurando aplicativos</span><span class="sxs-lookup"><span data-stu-id="06c81-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="06c81-148">Configuração de aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06c81-148">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
- [<span data-ttu-id="06c81-149">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="06c81-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="06c81-150">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="06c81-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="06c81-151">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="06c81-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
