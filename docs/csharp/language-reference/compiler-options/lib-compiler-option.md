---
title: -lib (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: c140a49de0503da1e59396f14ac1aee4c1d7d1a6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511199"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="4796c-102">-lib (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="4796c-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="4796c-103">A opção **-lib** especifica o local dos assemblies referenciados por meio da opção [-reference (Opções do Compilador do C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4796c-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4796c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4796c-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4796c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4796c-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="4796c-106">Um diretório para o compilador examinar se um assembly referenciado não foi encontrado no diretório de trabalho atual (o diretório do qual você está invocando o compilador) ou no diretório de sistema do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="4796c-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="4796c-107">Um ou mais diretórios adicionais a serem pesquisados para referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="4796c-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="4796c-108">Separe os nomes de diretório adicionais com uma vírgula e não inclua espaços em branco entre eles.</span><span class="sxs-lookup"><span data-stu-id="4796c-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4796c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4796c-109">Remarks</span></span>  
 <span data-ttu-id="4796c-110">O compilador pesquisa referências de assembly que não são totalmente qualificadas na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="4796c-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="4796c-111">Diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="4796c-111">Current working directory.</span></span> <span data-ttu-id="4796c-112">Esse é o diretório do qual o compilador é invocado.</span><span class="sxs-lookup"><span data-stu-id="4796c-112">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="4796c-113">O diretório de sistema do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="4796c-113">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="4796c-114">Diretórios especificados por **-lib**.</span><span class="sxs-lookup"><span data-stu-id="4796c-114">Directories specified by **-lib**.</span></span>  
  
4.  <span data-ttu-id="4796c-115">Diretórios especificados pela variável de ambiente LIB.</span><span class="sxs-lookup"><span data-stu-id="4796c-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="4796c-116">Use **-reference** para especificar uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="4796c-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="4796c-117">**-lib** é aditivo; especificá-lo mais de uma vez acrescenta a valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="4796c-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="4796c-118">Uma alternativa ao uso de **-lib** é copiar todos assemblies necessários para o diretório de trabalho; isso permitirá que você simplesmente passe o nome do assembly para **-reference**.</span><span class="sxs-lookup"><span data-stu-id="4796c-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="4796c-119">Em seguida, é possível excluir os assemblies do diretório de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4796c-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="4796c-120">Como o caminho para o assembly dependente não foi especificado no manifesto do assembly, o aplicativo pode ser iniciado no computador de destino e localizará e usará o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="4796c-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="4796c-121">O fato de o compilador poder referenciar o assembly não implica que o Common Language Runtime será capaz de localizar e carregar o assembly em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4796c-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="4796c-122">Consulte [Como o tempo de execução localiza assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) para obter detalhes sobre como o runtime pesquisa assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="4796c-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4796c-123">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4796c-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4796c-124">Abra a caixa de diálogo **Páginas de Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="4796c-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2.  <span data-ttu-id="4796c-125">Clique na página de propriedades **Caminho de Referências**.</span><span class="sxs-lookup"><span data-stu-id="4796c-125">Click the **References Path** property page.</span></span>  
  
3.  <span data-ttu-id="4796c-126">Modifique o conteúdo da caixa de listagem.</span><span class="sxs-lookup"><span data-stu-id="4796c-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="4796c-127">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="4796c-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4796c-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4796c-128">Example</span></span>  
 <span data-ttu-id="4796c-129">Compile t2.cs para criar um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="4796c-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="4796c-130">O compilador examinará referências de assembly no diretório de trabalho e no diretório raiz da unidade C.</span><span class="sxs-lookup"><span data-stu-id="4796c-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4796c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4796c-131">See Also</span></span>

- [<span data-ttu-id="4796c-132">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="4796c-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="4796c-133">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="4796c-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
