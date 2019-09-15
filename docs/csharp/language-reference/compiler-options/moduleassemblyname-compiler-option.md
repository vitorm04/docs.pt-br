---
title: -moduleassemblyname (opção do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 7562c0609d61b2388f5063bc480a4dfc715155db
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970084"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="b3d21-102">-moduleassemblyname (opção do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="b3d21-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="b3d21-103">Especifica um assembly cujos tipos não públicos podem ser acessados por um .netmodule.</span><span class="sxs-lookup"><span data-stu-id="b3d21-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3d21-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3d21-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3d21-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="b3d21-106">O nome do assembly cujos tipos não públicos podem ser acessados por um .netmodule.</span><span class="sxs-lookup"><span data-stu-id="b3d21-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3d21-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3d21-107">Remarks</span></span>  
 <span data-ttu-id="b3d21-108">O **-moduleassemblyname** deverá ser usado ao compilar um .netmodule e quando as condições a seguir forem true:</span><span class="sxs-lookup"><span data-stu-id="b3d21-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="b3d21-109">O .netmodule precisa acessar tipos não públicos em um assembly existente.</span><span class="sxs-lookup"><span data-stu-id="b3d21-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="b3d21-110">Você sabe o nome do assembly no qual o .netmodule será compilado.</span><span class="sxs-lookup"><span data-stu-id="b3d21-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="b3d21-111">O assembly existente concedeu acesso de assembly amigável ao assembly no qual o .netmodule será compilado.</span><span class="sxs-lookup"><span data-stu-id="b3d21-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="b3d21-112">Para obter mais informações sobre a compilação de um .netmodule, consulte [-target:module (Opções do compilador do C#)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b3d21-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="b3d21-113">Para obter mais informações sobre assemblies amigos, consulte [Assemblies Amigáveis](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="b3d21-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="b3d21-114">Essa opção não está disponível de dentro do ambiente de desenvolvimento; ela só está disponível quando se compila na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b3d21-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="b3d21-115">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="b3d21-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3d21-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3d21-116">Example</span></span>  
 <span data-ttu-id="b3d21-117">Este exemplo compila um assembly com um tipo privado que concede acesso de assembly amigável a um assembly denominado csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="b3d21-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="b3d21-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3d21-118">Example</span></span>  
 <span data-ttu-id="b3d21-119">Este exemplo compila um .netmodule que acessa um tipo não público no assembly moduleassemblyname_1.dll.</span><span class="sxs-lookup"><span data-stu-id="b3d21-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="b3d21-120">Sabendo que esse .netmodule será compilado dentro de um assembly chamado csman_an_assembly, é possível especificar **-moduleassemblyname**, permitindo que o .netmodule acesse tipos não públicos em um assembly que tenha concedido acesso de assembly amigável ao csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="b3d21-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="b3d21-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3d21-121">Example</span></span>  
 <span data-ttu-id="b3d21-122">Este exemplo de código compila o assembly csman_an_assembly, referenciando o assembly compilado anteriormente e o .netmodule.</span><span class="sxs-lookup"><span data-stu-id="b3d21-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="b3d21-123">**An_Internal_Class.Test foi chamado**</span><span class="sxs-lookup"><span data-stu-id="b3d21-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="b3d21-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3d21-124">See also</span></span>

- [<span data-ttu-id="b3d21-125">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="b3d21-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b3d21-126">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="b3d21-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
