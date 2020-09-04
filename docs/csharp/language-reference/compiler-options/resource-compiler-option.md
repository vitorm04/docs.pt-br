---
description: -resource (opções do compilador C#)
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
ms.openlocfilehash: 1e2de095b460b684fb06faf46731283a1304906e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465683"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="286c2-103">-resource (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="286c2-103">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="286c2-104">Insere o recurso especificado no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="286c2-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="286c2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="286c2-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="286c2-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="286c2-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="286c2-107">O arquivo de recurso do .NET que você deseja inserir no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="286c2-107">The .NET resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="286c2-108">`identifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="286c2-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="286c2-109">O nome lógico do recurso; o nome usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="286c2-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="286c2-110">O padrão é o nome do nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="286c2-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="286c2-111">`accessibility-modifier` (opcional)</span><span class="sxs-lookup"><span data-stu-id="286c2-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="286c2-112">A acessibilidade do recurso: público ou privado.</span><span class="sxs-lookup"><span data-stu-id="286c2-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="286c2-113">O padrão é público.</span><span class="sxs-lookup"><span data-stu-id="286c2-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="286c2-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="286c2-114">Remarks</span></span>  
 <span data-ttu-id="286c2-115">Use [-linkresource](./linkresource-compiler-option.md) para vincular um recurso a um assembly e não adicionar o arquivo de recurso ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="286c2-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="286c2-116">Por padrão, recursos são públicos no assembly quando são criados usando o compilador C#.</span><span class="sxs-lookup"><span data-stu-id="286c2-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="286c2-117">Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="286c2-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="286c2-118">Não é permitida nenhuma outra acessibilidade diferente de `public` ou `private`.</span><span class="sxs-lookup"><span data-stu-id="286c2-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="286c2-119">Se `filename` for um arquivo de recurso .NET criado, por exemplo, por [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no <xref:System.Resources> namespace.</span><span class="sxs-lookup"><span data-stu-id="286c2-119">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="286c2-120">Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="286c2-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="286c2-121">Para todos os outros recursos, use os métodos `GetManifestResource` na classe <xref:System.Reflection.Assembly> para acessar o recurso em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="286c2-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="286c2-122">**-res** é a forma abreviada de **-resource**.</span><span class="sxs-lookup"><span data-stu-id="286c2-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="286c2-123">A ordem dos recursos no arquivo de saída é determinada com base na ordem especificada na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="286c2-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="286c2-124">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="286c2-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="286c2-125">Adicionar um arquivo de recurso ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="286c2-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="286c2-126">Selecione o arquivo que você deseja inserir no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="286c2-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="286c2-127">Selecione **Ação de Build** para o arquivo na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="286c2-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="286c2-128">Defina **Ação de Build** como **Recurso inserido**.</span><span class="sxs-lookup"><span data-stu-id="286c2-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="286c2-129">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="286c2-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="286c2-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="286c2-130">Example</span></span>  
 <span data-ttu-id="286c2-131">Compile `in.cs` e anexe ao arquivo de recurso `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="286c2-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="286c2-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="286c2-132">See also</span></span>

- [<span data-ttu-id="286c2-133">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="286c2-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="286c2-134">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="286c2-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
