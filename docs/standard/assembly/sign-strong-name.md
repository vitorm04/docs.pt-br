---
title: Como assinar um assembly com um nome forte
description: Este artigo mostra como assinar um assembly .NET com um nome forte usando a guia assinatura, o vinculador de assembly, os atributos do assembly ou as opções do compilador.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET], signing
- assemblies [.NET], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 5192f7f372b9ef7927930c3599aebc6fca9f1f0f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687658"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="a5b64-103">Como assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="a5b64-103">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="a5b64-104">Embora o .NET Core dê suporte a assemblies de nome forte e todos os assemblies na biblioteca do .NET Core sejam assinados, a maioria dos assemblies de terceiros não precisa de nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="a5b64-104">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="a5b64-105">Para obter mais informações, consulte [assinatura de nome forte](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) no github.</span><span class="sxs-lookup"><span data-stu-id="a5b64-105">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="a5b64-106">Há vários modos de assinar um assembly com um nome forte:</span><span class="sxs-lookup"><span data-stu-id="a5b64-106">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="a5b64-107">Usando a guia **Assinatura** na caixa de diálogo **Propriedades** de um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5b64-107">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="a5b64-108">Esta é a forma mais fácil e conveniente de assinar um assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="a5b64-108">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="a5b64-109">Usando o [vinculador de assembly (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) para vincular um módulo de código de .NET Framework (um arquivo *. netmodule* ) a um arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="a5b64-109">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="a5b64-110">Usando atributos de assembly para inserir as informações do nome forte no seu código.</span><span class="sxs-lookup"><span data-stu-id="a5b64-110">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="a5b64-111">Você pode usar o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute>, dependendo do local em que o arquivo de chave a ser usado se encontra.</span><span class="sxs-lookup"><span data-stu-id="a5b64-111">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="a5b64-112">Usando opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="a5b64-112">By using compiler options.</span></span>  
  
 <span data-ttu-id="a5b64-113">Você deve ter um par de chaves de criptografia para assinar um assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="a5b64-113">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="a5b64-114">Para obter mais informações sobre como criar um par de chaves, consulte [como criar um par de chaves pública-privada](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="a5b64-114">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="a5b64-115">Criar e assinar um assembly com um nome forte usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a5b64-115">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="a5b64-116">No **Gerenciador de Soluções** , abra o menu de atalho do projeto e, em seguida, escolha **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="a5b64-116">In **Solution Explorer** , open the shortcut menu for the project, and then choose **Properties** .</span></span>  
  
2. <span data-ttu-id="a5b64-117">Escolha a guia **Assinatura** .</span><span class="sxs-lookup"><span data-stu-id="a5b64-117">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="a5b64-118">Marque a caixa **Assinar o assembly** .</span><span class="sxs-lookup"><span data-stu-id="a5b64-118">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="a5b64-119">Na caixa **escolher um arquivo de chave de nome forte** , escolha **procurar** e, em seguida, navegue até o arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="a5b64-119">In the **Choose a strong name key file** box, choose **Browse** , and then navigate to the key file.</span></span> <span data-ttu-id="a5b64-120">Para criar um novo arquivo de chave, escolha **novo** e digite seu nome na caixa de diálogo **criar chave de nome forte** .</span><span class="sxs-lookup"><span data-stu-id="a5b64-120">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5b64-121">Para [assinar um assembly com atraso](delay-sign.md), escolha um arquivo de chave pública.</span><span class="sxs-lookup"><span data-stu-id="a5b64-121">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="a5b64-122">Criar e assinar um assembly com um nome forte usando o vinculador de assembly</span><span class="sxs-lookup"><span data-stu-id="a5b64-122">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="a5b64-123">No [prompt de comando do desenvolvedor para o Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a5b64-123">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="a5b64-124">**Al** **/out:** \<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="a5b64-124">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="a5b64-125">Em que:</span><span class="sxs-lookup"><span data-stu-id="a5b64-125">Where:</span></span>  

- <span data-ttu-id="a5b64-126">*AssemblyName* é o nome do assembly com assinatura forte (um arquivo *. dll* ou *. exe* ) que o vinculador de assembly emitirá.</span><span class="sxs-lookup"><span data-stu-id="a5b64-126">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="a5b64-127">*ModuleName* é o nome de um módulo de código .NET Framework (um arquivo *. netmodule* ) que inclui um ou mais tipos.</span><span class="sxs-lookup"><span data-stu-id="a5b64-127">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="a5b64-128">Você pode criar um arquivo *. netmodule* compilando seu código com a `/target:module` opção em C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a5b64-128">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="a5b64-129">*fileFileName* é o nome do contêiner ou arquivo que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="a5b64-129">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="a5b64-130">O vinculador de assembly interpreta um caminho relativo em relação ao diretório atual.</span><span class="sxs-lookup"><span data-stu-id="a5b64-130">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="a5b64-131">O exemplo a seguir assina o assembly *MyAssembly.dll* com um nome forte usando o arquivo de chave *sgKey. SNK* .</span><span class="sxs-lookup"><span data-stu-id="a5b64-131">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk* .</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="a5b64-132">Para saber mais sobre essa ferramenta, veja [Vinculador de Assembly](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="a5b64-132">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="a5b64-133">Assinar um assembly com um nome forte usando atributos</span><span class="sxs-lookup"><span data-stu-id="a5b64-133">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="a5b64-134">Adicione o atributo <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> ao seu arquivo de código-fonte e especifique o nome do arquivo ou contêiner que contém o par de chaves a ser usado ao assinar o assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="a5b64-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="a5b64-135">Compile o arquivo de código-fonte normalmente.</span><span class="sxs-lookup"><span data-stu-id="a5b64-135">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="a5b64-136">Os compiladores de C# e Visual Basic emitem avisos do compilador (CS1699 e BC41008, respectivamente) quando encontram o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a5b64-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="a5b64-137">Você pode ignorar os avisos.</span><span class="sxs-lookup"><span data-stu-id="a5b64-137">You can ignore the warnings.</span></span>  

<span data-ttu-id="a5b64-138">O exemplo a seguir usa o <xref:System.Reflection.AssemblyKeyFileAttribute> atributo com um arquivo de chave chamado *keyfile. SNK* , que está localizado no diretório em que o assembly é compilado.</span><span class="sxs-lookup"><span data-stu-id="a5b64-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk* , which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="a5b64-139">Você também pode atrasar a assinatura de um assembly ao compilar seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a5b64-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="a5b64-140">Para obter mais informações, veja [assinar um assembly com atraso](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="a5b64-140">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="a5b64-141">Assinar um assembly com um nome forte usando o compilador</span><span class="sxs-lookup"><span data-stu-id="a5b64-141">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="a5b64-142">Compile seu arquivo ou arquivos de código-fonte com a opção de compilador `/keyfile` ou `/delaysign` no C# e em Visual Basic, ou a opção de vinculador `/KEYFILE` ou `/DELAYSIGN` em C++.</span><span class="sxs-lookup"><span data-stu-id="a5b64-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="a5b64-143">Depois do nome da opção, adicione um dois-pontos e o nome do arquivo da chave.</span><span class="sxs-lookup"><span data-stu-id="a5b64-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="a5b64-144">Ao usar compiladores de linha de comando, você pode copiar o arquivo de chave para o diretório que contém seus arquivos de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a5b64-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="a5b64-145">Para obter informações sobre assinatura de atraso, consulte [assinar um assembly com atraso](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="a5b64-145">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="a5b64-146">O exemplo a seguir usa o compilador C# e assina o assembly *UtilityLibrary.dll* com um nome forte usando o arquivo de chave *sgKey. SNK* .</span><span class="sxs-lookup"><span data-stu-id="a5b64-146">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk* .</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="a5b64-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="a5b64-147">See also</span></span>

- [<span data-ttu-id="a5b64-148">Criar e usar assemblies com nome forte</span><span class="sxs-lookup"><span data-stu-id="a5b64-148">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="a5b64-149">Como criar um par de chaves pública-privada</span><span class="sxs-lookup"><span data-stu-id="a5b64-149">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="a5b64-150">Al.exe (vinculador de assembly)</span><span class="sxs-lookup"><span data-stu-id="a5b64-150">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="a5b64-151">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="a5b64-151">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="a5b64-152">Gerenciar assinatura de assembly e de manifesto</span><span class="sxs-lookup"><span data-stu-id="a5b64-152">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="a5b64-153">Página de assinatura, designer de projeto</span><span class="sxs-lookup"><span data-stu-id="a5b64-153">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
