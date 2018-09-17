---
title: -resource (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: e02eda66ab9fadbc7b5b042c8940096c70ef6a03
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45593147"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="550d6-102">-resource (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="550d6-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="550d6-103">Insere o recurso especificado no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="550d6-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="550d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="550d6-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="550d6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="550d6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="550d6-106">O arquivo de recurso do .NET Framework que você deseja inserir no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="550d6-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="550d6-107">`identifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="550d6-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="550d6-108">O nome lógico do recurso; o nome usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="550d6-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="550d6-109">O padrão é o nome do nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="550d6-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="550d6-110">`accessibility-modifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="550d6-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="550d6-111">A acessibilidade do recurso: público ou privado.</span><span class="sxs-lookup"><span data-stu-id="550d6-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="550d6-112">O padrão é público.</span><span class="sxs-lookup"><span data-stu-id="550d6-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="550d6-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="550d6-113">Remarks</span></span>  
 <span data-ttu-id="550d6-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) para vincular um recurso a um assembly e não adicionar o arquivo de recurso ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="550d6-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="550d6-115">Por padrão, recursos são públicos no assembly quando são criados usando o compilador C#.</span><span class="sxs-lookup"><span data-stu-id="550d6-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="550d6-116">Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="550d6-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="550d6-117">Não é permitida nenhuma outra acessibilidade diferente de `public` ou `private`.</span><span class="sxs-lookup"><span data-stu-id="550d6-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="550d6-118">Se `filename` for um arquivo de recurso do .NET Framework criado, por exemplo, por [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="550d6-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="550d6-119">Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="550d6-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="550d6-120">Para todos os outros recursos, use os métodos `GetManifestResource` na classe <xref:System.Reflection.Assembly> para acessar o recurso em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="550d6-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="550d6-121">**-res** é a forma abreviada de **-resource**.</span><span class="sxs-lookup"><span data-stu-id="550d6-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="550d6-122">A ordem dos recursos no arquivo de saída é determinada com base na ordem especificada na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="550d6-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="550d6-123">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="550d6-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="550d6-124">Adicionar um arquivo de recurso ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="550d6-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="550d6-125">Selecione o arquivo que você deseja inserir no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="550d6-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="550d6-126">Selecione **Ação de Build** para o arquivo na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="550d6-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="550d6-127">Defina **Ação de Build** como **Recurso inserido**.</span><span class="sxs-lookup"><span data-stu-id="550d6-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="550d6-128">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="550d6-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="550d6-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="550d6-129">Example</span></span>  
 <span data-ttu-id="550d6-130">Compile `in.cs` e anexe ao arquivo de recurso `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="550d6-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="550d6-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="550d6-131">See Also</span></span>  

- [<span data-ttu-id="550d6-132">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="550d6-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="550d6-133">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="550d6-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
