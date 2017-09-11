---
title: "-linkresource (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /linkresource
dev_langs:
- CSharp
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 022d6c1a53eab98fc033c902f903e7bc66e6da3f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="linkresource-c-compiler-options"></a><span data-ttu-id="22cca-102">/linkresource (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="22cca-102">/linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="22cca-103">Cria um link para um recurso do .NET Framework no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="22cca-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="22cca-104">O arquivo de recurso não é adicionado ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="22cca-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="22cca-105">Isso é diferente da opção [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) que insere um arquivo de recurso no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="22cca-105">This differs from the [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22cca-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22cca-106">Syntax</span></span>  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="22cca-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="22cca-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="22cca-108">O arquivo de recurso do .NET Framework ao qual você deseja vincular do assembly.</span><span class="sxs-lookup"><span data-stu-id="22cca-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="22cca-109">`identifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="22cca-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="22cca-110">O nome lógico do recurso; o nome usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="22cca-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="22cca-111">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="22cca-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="22cca-112">`accessibility-modifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="22cca-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="22cca-113">A acessibilidade do recurso: público ou privado.</span><span class="sxs-lookup"><span data-stu-id="22cca-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="22cca-114">O padrão é público.</span><span class="sxs-lookup"><span data-stu-id="22cca-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22cca-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="22cca-115">Remarks</span></span>  
 <span data-ttu-id="22cca-116">Por padrão, os recursos vinculados são públicos no assembly quando são criados usando o compilador C#.</span><span class="sxs-lookup"><span data-stu-id="22cca-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="22cca-117">Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="22cca-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="22cca-118">Não é permitido nenhum outro modificador diferente de `public` ou de `private`.</span><span class="sxs-lookup"><span data-stu-id="22cca-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="22cca-119">**/linkresource** requer uma das opções [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) diferentes de **/target:module**.</span><span class="sxs-lookup"><span data-stu-id="22cca-119">**/linkresource** requires one of the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **/target:module**.</span></span>  
  
 <span data-ttu-id="22cca-120">Se `filename` for um arquivo de recurso do .NET Framework criado, por exemplo, por [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="22cca-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="22cca-121">Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="22cca-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=fullName>.</span></span> <span data-ttu-id="22cca-122">Para todos os outros recursos, use os métodos `GetManifestResource`* na classe <xref:System.Reflection.Assembly> para acessar o recurso no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="22cca-122">For all other resources, use the `GetManifestResource`* methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="22cca-123">O arquivo especificado em `filename` pode ter qualquer formato.</span><span class="sxs-lookup"><span data-stu-id="22cca-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="22cca-124">Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.</span><span class="sxs-lookup"><span data-stu-id="22cca-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="22cca-125">O segundo dos exemplos a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="22cca-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="22cca-126">É possível fazer a mesma coisa no Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="22cca-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="22cca-127">O terceiro dos exemplos a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="22cca-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="22cca-128">Para obter mais informações, consulte [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) e [Trabalhando com assemblies e o cache de assembly global](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="22cca-128">For more information, see [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="22cca-129">**/linkres** é a forma abreviada de **/linkresource**.</span><span class="sxs-lookup"><span data-stu-id="22cca-129">**/linkres** is the short form of **/linkresource**.</span></span>  
  
 <span data-ttu-id="22cca-130">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="22cca-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22cca-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22cca-131">Example</span></span>  
 <span data-ttu-id="22cca-132">Compile `in.cs` e vincule ao arquivo de recurso `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="22cca-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="22cca-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22cca-133">Example</span></span>  
 <span data-ttu-id="22cca-134">Compile `A.cs` em uma DLL, vincule a um DLL N.dll nativo e coloque a saída no GAC (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="22cca-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="22cca-135">Nesse exemplo, tanto A.dll quanto N.dll residirão no GAC.</span><span class="sxs-lookup"><span data-stu-id="22cca-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="22cca-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22cca-136">Example</span></span>  
 <span data-ttu-id="22cca-137">Este exemplo faz a mesma coisa que o anterior, mas usando as opções do Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="22cca-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="22cca-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22cca-138">See Also</span></span>  
 <span data-ttu-id="22cca-139">[Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="22cca-139">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="22cca-140">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="22cca-140">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
 <span data-ttu-id="22cca-141">[Como trabalhar com assemblies e o cache de assembly global](../../../framework/app-domains/working-with-assemblies-and-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="22cca-141">[Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md) </span></span>  
 [<span data-ttu-id="22cca-142">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="22cca-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

