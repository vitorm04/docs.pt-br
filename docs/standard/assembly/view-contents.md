---
title: Como exibir o conteúdo do assembly
description: Você pode usar o desmontador IL para exibir os atributos e as referências de um assembly para outros módulos e assemblies.
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: be2311c601effbebd519e33b7a5e13d49f44bd05
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687492"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="61d31-103">Como exibir o conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="61d31-103">How to: View assembly contents</span></span>

<span data-ttu-id="61d31-104">Você pode usar o [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) para exibir informações MSIL (Microsoft Intermediate Language) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="61d31-104">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="61d31-105">Se o arquivo que está sendo examinado for um assembly, essas informações poderão incluir os atributos e as referências do assembly a outros módulos e assemblies.</span><span class="sxs-lookup"><span data-stu-id="61d31-105">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="61d31-106">Essas informações podem ser úteis para determinar se um arquivo é um assembly ou parte de um assembly e se o arquivo tem referências a outros módulos ou assemblies.</span><span class="sxs-lookup"><span data-stu-id="61d31-106">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="61d31-107">Para exibir o conteúdo de um assembly usando *Ildasm.exe* , insira **ILDASM \<assembly name>** em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="61d31-107">To display the contents of an assembly using *Ildasm.exe* , enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="61d31-108">Por exemplo, o comando a seguir desmonta o assembly *Hello.exe* .</span><span class="sxs-lookup"><span data-stu-id="61d31-108">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="61d31-109">Para exibir informações de manifesto do assembly, clique duas vezes no ícone de **manifesto** na janela do desmontador MSIL.</span><span class="sxs-lookup"><span data-stu-id="61d31-109">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="61d31-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61d31-110">Example</span></span>

<span data-ttu-id="61d31-111">O exemplo a seguir começa com um programa "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="61d31-111">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="61d31-112">Depois de compilar o programa, use *Ildasm.exe* para desmontar o assembly *Hello.exe* e exibir o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="61d31-112">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="61d31-113">Executar o comando *ildasm.exe* no assembly de *Hello.exe* e clicar duas vezes no ícone de **manifesto** na janela do desmontador MSIL produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="61d31-113">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

```output
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

<span data-ttu-id="61d31-114">A tabela a seguir descreve cada diretiva no manifesto do assembly do assembly *Hello.exe* usado no exemplo:</span><span class="sxs-lookup"><span data-stu-id="61d31-114">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="61d31-115">Diretiva</span><span class="sxs-lookup"><span data-stu-id="61d31-115">Directive</span></span>|<span data-ttu-id="61d31-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="61d31-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="61d31-117">**. assembly externo \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="61d31-117">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="61d31-118">Especifica outro assembly que contém itens referenciados pelo módulo atual (neste exemplo, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="61d31-118">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="61d31-119">**. PublicKeyToken \<token>**</span><span class="sxs-lookup"><span data-stu-id="61d31-119">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="61d31-120">Especifica o token da chave real do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="61d31-120">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="61d31-121">**. ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="61d31-121">**.ver \<version number>**</span></span>|<span data-ttu-id="61d31-122">Especifica o número de versão do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="61d31-122">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="61d31-123">**. assembly \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="61d31-123">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="61d31-124">Especifica o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="61d31-124">Specifies the assembly name.</span></span>|
|<span data-ttu-id="61d31-125">**. algoritmo de hash \<int32 value>**</span><span class="sxs-lookup"><span data-stu-id="61d31-125">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="61d31-126">Especifica o algoritmo de hash usado.</span><span class="sxs-lookup"><span data-stu-id="61d31-126">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="61d31-127">**. ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="61d31-127">**.ver \<version number>**</span></span>|<span data-ttu-id="61d31-128">Especifica o número de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="61d31-128">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="61d31-129">**. módulo \<file name>**</span><span class="sxs-lookup"><span data-stu-id="61d31-129">**.module \<file name>**</span></span>|<span data-ttu-id="61d31-130">Especifica o nome dos módulos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="61d31-130">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="61d31-131">Neste exemplo, o assembly consiste em apenas um arquivo.</span><span class="sxs-lookup"><span data-stu-id="61d31-131">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="61d31-132">**. subsistema \<value>**</span><span class="sxs-lookup"><span data-stu-id="61d31-132">**.subsystem \<value>**</span></span>|<span data-ttu-id="61d31-133">Especifica o ambiente de aplicativo necessário para o programa.</span><span class="sxs-lookup"><span data-stu-id="61d31-133">Specifies the application environment required for the program.</span></span> <span data-ttu-id="61d31-134">Neste exemplo, o valor 3 indica que este executável é executado em um console.</span><span class="sxs-lookup"><span data-stu-id="61d31-134">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="61d31-135">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="61d31-135">**.corflags**</span></span>|<span data-ttu-id="61d31-136">Atualmente, um campo reservado nos metadados.</span><span class="sxs-lookup"><span data-stu-id="61d31-136">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="61d31-137">Um manifesto do assembly pode conter várias diretivas diferentes, dependendo do conteúdo do assembly.</span><span class="sxs-lookup"><span data-stu-id="61d31-137">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="61d31-138">Para obter uma lista extensa das diretivas no manifesto do assembly, consulte a documentação do ECMA, especialmente a "partição II: definição de metadados e semântica" e "partição III: conjunto de instruções CIL":</span><span class="sxs-lookup"><span data-stu-id="61d31-138">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="61d31-139">Padrões ECMA C# e Common Language Infrastructure</span><span class="sxs-lookup"><span data-stu-id="61d31-139">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="61d31-140">ECMA-335-Common Language Infrastructure (CLI) padrão</span><span class="sxs-lookup"><span data-stu-id="61d31-140">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="61d31-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="61d31-141">See also</span></span>

- [<span data-ttu-id="61d31-142">Domínios de aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="61d31-142">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="61d31-143">Tópicos de instruções sobre domínios de aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="61d31-143">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="61d31-144">Ildasm.exe (desmontador de IL)</span><span class="sxs-lookup"><span data-stu-id="61d31-144">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
