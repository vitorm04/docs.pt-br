---
title: 'Como: Assinar um assembly com um nome forte'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973057"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="b8cc8-102">Como: Assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="b8cc8-102">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="b8cc8-103">Embora o .NET Core dê suporte a assemblies de nome forte e todos os assemblies na biblioteca do .NET Core sejam assinados, a maioria dos assemblies de terceiros não precisa de nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-103">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="b8cc8-104">Para obter mais informações, consulte [assinatura de nome forte](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) no github.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-104">For more information, see [Strong Name Signing](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="b8cc8-105">Há vários modos de assinar um assembly com um nome forte:</span><span class="sxs-lookup"><span data-stu-id="b8cc8-105">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="b8cc8-106">Usando a guia **Assinatura** na caixa de diálogo **Propriedades** de um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-106">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="b8cc8-107">Esta é a forma mais fácil e conveniente de assinar um assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-107">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="b8cc8-108">Usando o [vinculador do assembly (al. exe)](../../framework/tools/al-exe-assembly-linker.md) para vincular um módulo de código de .NET Framework (um arquivo *. netmodule* ) a um arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-108">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="b8cc8-109">Usando atributos de assembly para inserir as informações do nome forte no seu código.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-109">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="b8cc8-110">Você pode usar o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute>, dependendo do local em que o arquivo de chave a ser usado se encontra.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-110">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="b8cc8-111">Usando opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-111">By using compiler options.</span></span>  
  
 <span data-ttu-id="b8cc8-112">Você deve ter um par de chaves de criptografia para assinar um assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-112">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="b8cc8-113">Para obter mais informações de como criar um par de chaves, confira [Como Como criar um par de chaves pública/privada](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="b8cc8-113">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="b8cc8-114">Criar e assinar um assembly com um nome forte usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8cc8-114">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="b8cc8-115">No **Gerenciador de Soluções**, abra o menu de atalho do projeto e, em seguida, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-115">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="b8cc8-116">Escolha a guia **Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-116">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="b8cc8-117">Marque a caixa **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-117">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="b8cc8-118">Na caixa **escolher um arquivo de chave de nome forte** , escolha **procurar**e, em seguida, navegue até o arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-118">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="b8cc8-119">Para criar um novo arquivo de chave, escolha **novo** e digite seu nome na caixa de diálogo **criar chave de nome forte** .</span><span class="sxs-lookup"><span data-stu-id="b8cc8-119">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8cc8-120">Para [assinar um assembly com atraso](delay-sign.md), escolha um arquivo de chave pública.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-120">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="b8cc8-121">Criar e assinar um assembly com um nome forte usando o vinculador de assembly</span><span class="sxs-lookup"><span data-stu-id="b8cc8-121">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="b8cc8-122">No [prompt de comando do desenvolvedor para o Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b8cc8-122">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="b8cc8-123">**al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="b8cc8-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="b8cc8-124">Sendo que:</span><span class="sxs-lookup"><span data-stu-id="b8cc8-124">Where:</span></span>  

- <span data-ttu-id="b8cc8-125">*AssemblyName* é o nome do assembly com assinatura forte (um arquivo *. dll* ou *. exe* ) que o vinculador de assembly emitirá.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-125">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="b8cc8-126">*ModuleName* é o nome de um módulo de código .NET Framework (um arquivo *. netmodule* ) que inclui um ou mais tipos.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-126">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="b8cc8-127">Você pode criar um arquivo *. netmodule* compilando seu código com o `/target:module` switch in C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-127">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="b8cc8-128">*fileFileName* é o nome do contêiner ou arquivo que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-128">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="b8cc8-129">O vinculador de assembly interpreta um caminho relativo em relação ao diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-129">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="b8cc8-130">O exemplo a seguir assina o assembly *myAssembly. dll* com um nome forte usando o arquivo de chave *sgKey. SNK*.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-130">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="b8cc8-131">Para saber mais sobre essa ferramenta, veja [Vinculador de Assembly](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="b8cc8-131">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="b8cc8-132">Assinar um assembly com um nome forte usando atributos</span><span class="sxs-lookup"><span data-stu-id="b8cc8-132">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="b8cc8-133">Adicione o atributo <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> ao seu arquivo de código-fonte e especifique o nome do arquivo ou contêiner que contém o par de chaves a ser usado ao assinar o assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
   
2. <span data-ttu-id="b8cc8-134">Compile o arquivo de código-fonte normalmente.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-134">Compile the source code file normally.</span></span>  
   
   > [!NOTE]
   > <span data-ttu-id="b8cc8-135">Os compiladores de C# e Visual Basic emitem avisos do compilador (CS1699 e BC41008, respectivamente) quando encontram o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="b8cc8-136">Você pode ignorar os avisos.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-136">You can ignore the warnings.</span></span>  

<span data-ttu-id="b8cc8-137">O exemplo a seguir usa <xref:System.Reflection.AssemblyKeyFileAttribute> o atributo com um arquivo de chave chamado *keyfile. SNK*, que está localizado no diretório em que o assembly é compilado.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="b8cc8-138">Você também pode atrasar a assinatura de um assembly ao compilar seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="b8cc8-139">Para obter mais informações, veja [assinar um assembly com atraso](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="b8cc8-139">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="b8cc8-140">Assinar um assembly com um nome forte usando o compilador</span><span class="sxs-lookup"><span data-stu-id="b8cc8-140">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="b8cc8-141">Compile seu arquivo ou arquivos de código-fonte com a opção de compilador `/keyfile` ou `/delaysign` no C# e em Visual Basic, ou a opção de vinculador `/KEYFILE` ou `/DELAYSIGN` em C++.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="b8cc8-142">Depois do nome da opção, adicione um dois-pontos e o nome do arquivo da chave.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="b8cc8-143">Ao usar compiladores de linha de comando, você pode copiar o arquivo de chave para o diretório que contém seus arquivos de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="b8cc8-144">Para obter informações sobre assinatura de atraso, consulte [assinar um assembly com atraso](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="b8cc8-144">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="b8cc8-145">O exemplo a seguir usa C# o compilador e assina o assembly *UtilityLibrary. dll* com um nome forte usando o arquivo de chave *sgKey. SNK*.</span><span class="sxs-lookup"><span data-stu-id="b8cc8-145">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="b8cc8-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8cc8-146">See also</span></span>

- [<span data-ttu-id="b8cc8-147">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="b8cc8-147">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="b8cc8-148">Como: Criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="b8cc8-148">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="b8cc8-149">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="b8cc8-149">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="b8cc8-150">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="b8cc8-150">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="b8cc8-151">Gerenciar assinatura de assembly e de manifesto</span><span class="sxs-lookup"><span data-stu-id="b8cc8-151">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="b8cc8-152">Página de assinatura, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="b8cc8-152">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
