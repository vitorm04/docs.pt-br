---
description: -linkresource (opções do compilador C#)
title: -linkresource (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 4efa0cbf286b40ad971bad66a7acce15e553eb39
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194096"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="00731-103">-linkresource (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="00731-103">-linkresource (C# Compiler Options)</span></span>

<span data-ttu-id="00731-104">Cria um link para um recurso do .NET no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="00731-104">Creates a link to a .NET resource in the output file.</span></span> <span data-ttu-id="00731-105">O arquivo de recurso não é adicionado ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="00731-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="00731-106">Isso é diferente da opção [-resource](./resource-compiler-option.md) que insere um arquivo de recurso no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="00731-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00731-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00731-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="00731-108">Argumentos</span><span class="sxs-lookup"><span data-stu-id="00731-108">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="00731-109">O arquivo de recurso do .NET para o qual você deseja vincular do assembly.</span><span class="sxs-lookup"><span data-stu-id="00731-109">The .NET resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="00731-110">`identifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="00731-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="00731-111">O nome lógico do recurso; o nome usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="00731-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="00731-112">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="00731-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="00731-113">`accessibility-modifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="00731-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="00731-114">A acessibilidade do recurso: público ou privado.</span><span class="sxs-lookup"><span data-stu-id="00731-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="00731-115">O padrão é público.</span><span class="sxs-lookup"><span data-stu-id="00731-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00731-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="00731-116">Remarks</span></span>  

 <span data-ttu-id="00731-117">Por padrão, os recursos vinculados são públicos no assembly quando são criados usando o compilador C#.</span><span class="sxs-lookup"><span data-stu-id="00731-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="00731-118">Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="00731-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="00731-119">Não é permitido nenhum outro modificador diferente de `public` ou de `private`.</span><span class="sxs-lookup"><span data-stu-id="00731-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="00731-120">**-linkresource** requer uma das opções [-target](./target-compiler-option.md) diferentes de **-target:module**.</span><span class="sxs-lookup"><span data-stu-id="00731-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="00731-121">Se `filename` for um arquivo de recurso .NET criado, por exemplo, por [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no <xref:System.Resources> namespace.</span><span class="sxs-lookup"><span data-stu-id="00731-121">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="00731-122">Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="00731-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="00731-123">Para todos os outros recursos, use os métodos `GetManifestResource` na classe <xref:System.Reflection.Assembly> para acessar o recurso em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00731-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="00731-124">O arquivo especificado em `filename` pode ter qualquer formato.</span><span class="sxs-lookup"><span data-stu-id="00731-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="00731-125">Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.</span><span class="sxs-lookup"><span data-stu-id="00731-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="00731-126">O segundo dos exemplos a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="00731-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="00731-127">É possível fazer a mesma coisa no Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="00731-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="00731-128">O terceiro dos exemplos a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="00731-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="00731-129">Para obter mais informações, consulte [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) e [Trabalhando com assemblies e o cache de assembly global](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="00731-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="00731-130">**-linkres** é a forma abreviada de **-linkresource**.</span><span class="sxs-lookup"><span data-stu-id="00731-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="00731-131">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="00731-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00731-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00731-132">Example</span></span>  

 <span data-ttu-id="00731-133">Compile `in.cs` e vincule ao arquivo de recurso `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="00731-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="00731-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00731-134">Example</span></span>  

 <span data-ttu-id="00731-135">Compile `A.cs` em uma DLL, vincule a um DLL N.dll nativo e coloque a saída no GAC (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="00731-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="00731-136">Nesse exemplo, tanto A.dll quanto N.dll residirão no GAC.</span><span class="sxs-lookup"><span data-stu-id="00731-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="00731-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00731-137">Example</span></span>  

 <span data-ttu-id="00731-138">Este exemplo faz a mesma coisa que o anterior, mas usando as opções do Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="00731-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="00731-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="00731-139">See also</span></span>

- [<span data-ttu-id="00731-140">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="00731-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="00731-141">Al.exe (vinculador de assembly)</span><span class="sxs-lookup"><span data-stu-id="00731-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="00731-142">Trabalhando com assemblies e o cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="00731-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="00731-143">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="00731-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
