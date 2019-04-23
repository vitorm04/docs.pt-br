---
title: 'Como: Exibir o conteúdo do assembly'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33fc98f12c1b49d6fe2b1dc187615e2dc9b1768
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330071"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="d3e42-102">Como: Exibir o conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="d3e42-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="d3e42-103">Você pode usar o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para exibir informações MSIL (Microsoft Intermediate Language) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3e42-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="d3e42-104">Se o arquivo que estiver sendo examinado for um assembly, essas informações poderão incluir os atributos do assembly, bem como as referências a outros módulos e assemblies.</span><span class="sxs-lookup"><span data-stu-id="d3e42-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="d3e42-105">Essas informações podem ser úteis para determinar se um arquivo é um assembly ou parte de um assembly e se o arquivo possui referências a outros módulos ou assemblies.</span><span class="sxs-lookup"><span data-stu-id="d3e42-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="d3e42-106">Para exibir o conteúdo de um assembly usando Ildasm.exe</span><span class="sxs-lookup"><span data-stu-id="d3e42-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1. <span data-ttu-id="d3e42-107">Digite **ildasm** \<*nome do assembly*> no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="d3e42-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="d3e42-108">Por exemplo, o comando a seguir desmonta o assembly `Hello.exe`.</span><span class="sxs-lookup"><span data-stu-id="d3e42-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="d3e42-109">Para exibir informações do manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="d3e42-109">To view assembly manifest information</span></span>  
  
1. <span data-ttu-id="d3e42-110">Clique duas vezes no ícone MANIFESTO da janela Desmontador de MSIL.</span><span class="sxs-lookup"><span data-stu-id="d3e42-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3e42-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3e42-111">Example</span></span>  
 <span data-ttu-id="d3e42-112">O exemplo a seguir inicia com um programa básico "Hello, World".</span><span class="sxs-lookup"><span data-stu-id="d3e42-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="d3e42-113">Após a compilação do programa, use Ildasm.exe para desmontar o assembly Hello.exe e exibir o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d3e42-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="d3e42-114">Executar o comando ildasm.exe no assembly Hello.exe e clicar duas vezes no ícone MANIFESTO da janela IL DASM gera o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="d3e42-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 <span data-ttu-id="d3e42-115">A tabela a seguir descreve cada diretiva no manifesto do assembly de Hello.exe usado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="d3e42-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="d3e42-116">Diretiva</span><span class="sxs-lookup"><span data-stu-id="d3e42-116">Directive</span></span>|<span data-ttu-id="d3e42-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3e42-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3e42-118">**.assembly extern \<** *nome do assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="d3e42-119">Especifica outro assembly que contém itens referenciados pelo módulo atual (neste exemplo, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="d3e42-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="d3e42-120">**.publickeytoken \<** *token* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="d3e42-121">Especifica o token da chave real do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="d3e42-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="d3e42-122">**.ver \<** *número da versão* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="d3e42-123">Especifica o número de versão do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="d3e42-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="d3e42-124">**.assembly \<** *nome do assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="d3e42-125">Especifica o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="d3e42-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="d3e42-126">**.hash algorithm \<** *valor int32* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="d3e42-127">Especifica o algoritmo de hash usado.</span><span class="sxs-lookup"><span data-stu-id="d3e42-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="d3e42-128">**.ver \<** *número da versão* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="d3e42-129">Especifica o número de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="d3e42-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="d3e42-130">**.module \<** *nome de arquivo* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="d3e42-131">Especifica o nome dos módulos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="d3e42-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="d3e42-132">Neste exemplo, o assembly consiste em apenas um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3e42-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="d3e42-133">**.subsystem \<** *valor* **>**</span><span class="sxs-lookup"><span data-stu-id="d3e42-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="d3e42-134">Especifica o ambiente de aplicativo necessário para o programa.</span><span class="sxs-lookup"><span data-stu-id="d3e42-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="d3e42-135">Neste exemplo, o valor 3 indica que este executável é executado em um console.</span><span class="sxs-lookup"><span data-stu-id="d3e42-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|**<span data-ttu-id="d3e42-136">.corflags</span><span class="sxs-lookup"><span data-stu-id="d3e42-136">.corflags</span></span>**|<span data-ttu-id="d3e42-137">Atualmente, um campo reservado nos metadados.</span><span class="sxs-lookup"><span data-stu-id="d3e42-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="d3e42-138">Um manifesto do assembly pode conter várias diretivas diferentes, dependendo do conteúdo do assembly.</span><span class="sxs-lookup"><span data-stu-id="d3e42-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="d3e42-139">Para obter uma lista extensa das diretivas no manifesto do assembly, confira a documentação da ECMA, especialmente "Partição II: Definição de metadados e semântica" e "Partição III: Conjunto de instruções CIL".</span><span class="sxs-lookup"><span data-stu-id="d3e42-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="d3e42-140">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="d3e42-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e42-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3e42-141">See also</span></span>

- [<span data-ttu-id="d3e42-142">Domínios de aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="d3e42-142">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="d3e42-143">Tópicos explicativos sobre domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="d3e42-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="d3e42-144">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="d3e42-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
