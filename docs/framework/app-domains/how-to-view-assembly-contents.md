---
title: "Como exibir o conteúdo de um assembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8903f7da1c945ff927ad6dfe0a92650849a36439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="7e168-102">Como exibir o conteúdo de um assembly</span><span class="sxs-lookup"><span data-stu-id="7e168-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="7e168-103">Você pode usar o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para exibir informações MSIL (Microsoft Intermediate Language) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="7e168-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="7e168-104">Se o arquivo que estiver sendo examinado for um assembly, essas informações poderão incluir os atributos do assembly, bem como as referências a outros módulos e assemblies.</span><span class="sxs-lookup"><span data-stu-id="7e168-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="7e168-105">Essas informações podem ser úteis para determinar se um arquivo é um assembly ou parte de um assembly e se o arquivo possui referências a outros módulos ou assemblies.</span><span class="sxs-lookup"><span data-stu-id="7e168-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="7e168-106">Para exibir o conteúdo de um assembly usando Ildasm.exe</span><span class="sxs-lookup"><span data-stu-id="7e168-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="7e168-107">Digite **ildasm** \<*nome do assembly*> no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="7e168-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="7e168-108">Por exemplo, o comando a seguir desmonta o assembly `Hello.exe`.</span><span class="sxs-lookup"><span data-stu-id="7e168-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="7e168-109">Para exibir informações do manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="7e168-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="7e168-110">Clique duas vezes no ícone MANIFESTO da janela Desmontador de MSIL.</span><span class="sxs-lookup"><span data-stu-id="7e168-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e168-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e168-111">Example</span></span>  
 <span data-ttu-id="7e168-112">O exemplo a seguir inicia com um programa básico "Hello, World".</span><span class="sxs-lookup"><span data-stu-id="7e168-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="7e168-113">Após a compilação do programa, use Ildasm.exe para desmontar o assembly Hello.exe e exibir o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="7e168-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="7e168-114">Executar o comando ildasm.exe no assembly Hello.exe e clicar duas vezes no ícone MANIFESTO da janela IL DASM gera o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="7e168-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="7e168-115">A tabela a seguir descreve cada diretiva no manifesto do assembly de Hello.exe usado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="7e168-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="7e168-116">Diretiva</span><span class="sxs-lookup"><span data-stu-id="7e168-116">Directive</span></span>|<span data-ttu-id="7e168-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e168-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e168-118">**.assembly extern \<** *nome do assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="7e168-119">Especifica outro assembly que contém itens referenciados pelo módulo atual (neste exemplo, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="7e168-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="7e168-120">**.publickeytoken \<** *token* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="7e168-121">Especifica o token da chave real do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="7e168-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="7e168-122">**.ver \<** *número da versão* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="7e168-123">Especifica o número de versão do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="7e168-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="7e168-124">**.assembly \<** *nome do assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="7e168-125">Especifica o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="7e168-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="7e168-126">**.hash algorithm \<** *valor int32* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="7e168-127">Especifica o algoritmo de hash usado.</span><span class="sxs-lookup"><span data-stu-id="7e168-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="7e168-128">**.ver \<** *número da versão* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="7e168-129">Especifica o número de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="7e168-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="7e168-130">**.module \<** *nome de arquivo* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="7e168-131">Especifica o nome dos módulos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="7e168-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="7e168-132">Neste exemplo, o assembly consiste em apenas um arquivo.</span><span class="sxs-lookup"><span data-stu-id="7e168-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="7e168-133">**.subsystem \<** *valor* **>**</span><span class="sxs-lookup"><span data-stu-id="7e168-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="7e168-134">Especifica o ambiente de aplicativo necessário para o programa.</span><span class="sxs-lookup"><span data-stu-id="7e168-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="7e168-135">Neste exemplo, o valor 3 indica que este executável é executado em um console.</span><span class="sxs-lookup"><span data-stu-id="7e168-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="7e168-136">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="7e168-136">**.corflags**</span></span>|<span data-ttu-id="7e168-137">Atualmente, um campo reservado nos metadados.</span><span class="sxs-lookup"><span data-stu-id="7e168-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="7e168-138">Um manifesto do assembly pode conter várias diretivas diferentes, dependendo do conteúdo do assembly.</span><span class="sxs-lookup"><span data-stu-id="7e168-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="7e168-139">Para obter uma lista extensa das diretivas no manifesto do assembly, confira a documentação da ECMA, especialmente "Partition II: Metadata Definition and Semantics" e "Partition III: CIL Instruction Set".</span><span class="sxs-lookup"><span data-stu-id="7e168-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="7e168-140">A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.</span><span class="sxs-lookup"><span data-stu-id="7e168-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e168-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e168-141">See Also</span></span>  
 [<span data-ttu-id="7e168-142">Domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="7e168-142">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [<span data-ttu-id="7e168-143">Tópicos explicativos sobre domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="7e168-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [<span data-ttu-id="7e168-144">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="7e168-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
