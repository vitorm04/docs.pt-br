---
title: 'Como: assinar um assembly com um nome forte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 963923951b3f3c288506cf339cd8a15f27792af3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599212"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="822a2-102">Como: assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="822a2-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="822a2-103">Há vários modos de assinar um assembly com um nome forte:</span><span class="sxs-lookup"><span data-stu-id="822a2-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="822a2-104">Usando a guia **Assinatura** na caixa de diálogo **Propriedades** de um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="822a2-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="822a2-105">Esta é a forma mais fácil e conveniente de assinar um assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="822a2-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="822a2-106">Usando o [Vinculador de Assembly (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para vincular um módulo de código do .NET Framework (um arquivo .netmodule) com um arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="822a2-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="822a2-107">Usando atributos de assembly para inserir as informações do nome forte no seu código.</span><span class="sxs-lookup"><span data-stu-id="822a2-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="822a2-108">Você pode usar o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute>, dependendo do local em que o arquivo de chave a ser usado se encontra.</span><span class="sxs-lookup"><span data-stu-id="822a2-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="822a2-109">Usando opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="822a2-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="822a2-110">Você deve ter um par de chaves de criptografia para assinar um assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="822a2-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="822a2-111">Para obter mais informações de como criar um par de chaves, confira [Como criar um par de chaves pública/privada](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="822a2-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="822a2-112">Para criar e assinar um assembly com um nome forte usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="822a2-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="822a2-113">No **Gerenciador de Soluções**, abra o menu de atalho do projeto e, em seguida, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="822a2-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="822a2-114">Escolha a guia **Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="822a2-114">Choose the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="822a2-115">Marque a caixa **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="822a2-115">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="822a2-116">Na caixa **Escolher um arquivo de chave com nome forte**, selecione **\<Procurar…>** e, em seguida, navegue até o arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="822a2-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="822a2-117">Para criar um novo arquivo de chave, selecione **\<Novo…>** e digite o nome na caixa de diálogo **Criar Chave de Nome Forte**.</span><span class="sxs-lookup"><span data-stu-id="822a2-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="822a2-118">Para criar e assinar um assembly com um nome forte usando o Vinculador de Assembly.</span><span class="sxs-lookup"><span data-stu-id="822a2-118">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="822a2-119">Com o [Prompt de Comando do Desenvolvedor para Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="822a2-119">At the [Developer Command Prompt for Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="822a2-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="822a2-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="822a2-121">em que:</span><span class="sxs-lookup"><span data-stu-id="822a2-121">where:</span></span>  
  
     <span data-ttu-id="822a2-122">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="822a2-122">*assemblyName*</span></span>  
     <span data-ttu-id="822a2-123">O nome forte do assembly assinado (um arquivo .dll ou .exe) que o Vinculador de Assembly emitirá.</span><span class="sxs-lookup"><span data-stu-id="822a2-123">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="822a2-124">*moduleName*</span><span class="sxs-lookup"><span data-stu-id="822a2-124">*moduleName*</span></span>  
     <span data-ttu-id="822a2-125">O nome de um módulo de código do .NET Framework (um arquivo .netmodule) que inclui um ou mais tipos.</span><span class="sxs-lookup"><span data-stu-id="822a2-125">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="822a2-126">Você pode criar um arquivo .netmodule ao compilar seu código com a opção `/target:module` em C# ou no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="822a2-126">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="822a2-127">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="822a2-127">*keyfileName*</span></span>  
     <span data-ttu-id="822a2-128">O nome do contêiner ou arquivo que contém o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="822a2-128">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="822a2-129">O Vinculador de Assembly interpreta um caminho relativo em relação ao diretório atual.</span><span class="sxs-lookup"><span data-stu-id="822a2-129">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="822a2-130">O exemplo a seguir assina o assembly `MyAssembly.dll` com um nome forte usando o arquivo de chave `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="822a2-130">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="822a2-131">Para saber mais sobre essa ferramenta, veja [Vinculador de Assembly](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="822a2-131">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="822a2-132">Para assinar um assembly com um nome forte usando atributos</span><span class="sxs-lookup"><span data-stu-id="822a2-132">To sign an assembly with a strong name by using attributes</span></span>  
  
1.  <span data-ttu-id="822a2-133">Adicione o atributo <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> ao seu arquivo de código-fonte e especifique o nome do arquivo ou contêiner que contém o par de chaves a ser usado ao assinar o assembly com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="822a2-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2.  <span data-ttu-id="822a2-134">Compile o arquivo de código-fonte normalmente.</span><span class="sxs-lookup"><span data-stu-id="822a2-134">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="822a2-135">Os compiladores de C# e Visual Basic emitem avisos do compilador (CS1699 e BC41008, respectivamente) quando encontram o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="822a2-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="822a2-136">Você pode ignorar os avisos.</span><span class="sxs-lookup"><span data-stu-id="822a2-136">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="822a2-137">O exemplo de código a seguir usa o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> com um arquivo de chave chamado `keyfile.snk`, localizado no diretório onde o assembly é compilado.</span><span class="sxs-lookup"><span data-stu-id="822a2-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="822a2-138">Você também pode atrasar a assinatura de um assembly ao compilar seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="822a2-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="822a2-139">Para obter mais informações, consulte [Assinando um assembly com atraso](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="822a2-139">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="822a2-140">Para assinar um assembly com um nome forte usando o compilador</span><span class="sxs-lookup"><span data-stu-id="822a2-140">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="822a2-141">Compile seu arquivo ou arquivos de código-fonte com a opção de compilador `/keyfile` ou `/delaysign` no C# e em Visual Basic, ou a opção de vinculador `/KEYFILE` ou `/DELAYSIGN` em C++.</span><span class="sxs-lookup"><span data-stu-id="822a2-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="822a2-142">Depois do nome da opção, adicione um dois-pontos e o nome do arquivo da chave.</span><span class="sxs-lookup"><span data-stu-id="822a2-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="822a2-143">Ao usar compiladores de linha de comando, você pode copiar o arquivo de chave para o diretório que contém seus arquivos de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="822a2-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="822a2-144">Para saber mais sobre assinatura com atraso, veja [Assinar um assembly com atraso](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="822a2-144">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="822a2-145">O exemplo a seguir usa o compilador C# e assina o assembly `UtilityLibrary.dll` com um nome forte usando o arquivo de chave `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="822a2-145">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="822a2-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="822a2-146">See also</span></span>
- [<span data-ttu-id="822a2-147">Criar e usar assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="822a2-147">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="822a2-148">Como: criar um par de chaves pública/privada</span><span class="sxs-lookup"><span data-stu-id="822a2-148">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="822a2-149">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="822a2-149">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="822a2-150">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="822a2-150">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="822a2-151">Gerenciando Assinatura de Assembly e Manifesto</span><span class="sxs-lookup"><span data-stu-id="822a2-151">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="822a2-152">Página de Assinatura, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="822a2-152">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
