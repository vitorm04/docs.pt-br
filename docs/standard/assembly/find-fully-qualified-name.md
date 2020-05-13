---
title: Como localizar o nome totalmente qualificado de um assembly
description: Este artigo mostra como obter o nome totalmente qualificado de um assembly .NET Framework ou assembly do .NET Core.
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 346d50dc7f279ce46c9803ad60479d3111739c25
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378945"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="dab7e-103">Como localizar o nome totalmente qualificado de um assembly</span><span class="sxs-lookup"><span data-stu-id="dab7e-103">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="dab7e-104">Para descobrir o nome totalmente qualificado de um .NET Framework assembly no cache de assembly global, use a ferramenta global assembly cache ([Gacutil. exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="dab7e-104">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="dab7e-105">Consulte [como: exibir o conteúdo do cache de assembly global](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="dab7e-105">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="dab7e-106">Para assemblies do .NET Core e para .NET Framework assemblies que não estão no cache de assembly global, você pode obter o nome totalmente qualificado do assembly de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="dab7e-106">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="dab7e-107">Você pode usar o código para gerar as informações para o console ou para uma variável, ou pode usar o [ILDASM. exe (desmontador Il)](../../framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contém o nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="dab7e-107">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="dab7e-108">Se o assembly já estiver carregado pelo aplicativo, você poderá recuperar o valor da propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="dab7e-108">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="dab7e-109">Você pode usar a <xref:System.Type.Assembly> propriedade de um <xref:System.Type> definido nesse assembly para recuperar uma referência ao <xref:System.Reflection.Assembly> objeto.</span><span class="sxs-lookup"><span data-stu-id="dab7e-109">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="dab7e-110">O exemplo fornece uma ilustração.</span><span class="sxs-lookup"><span data-stu-id="dab7e-110">The example provides an illustration.</span></span>

- <span data-ttu-id="dab7e-111">Se você souber o caminho do sistema de arquivos do assembly, poderá chamar o `static` método (C#) ou `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="dab7e-111">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="dab7e-112">A seguir há um exemplo simples.</span><span class="sxs-lookup"><span data-stu-id="dab7e-112">The following is a simple example.</span></span>

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- <span data-ttu-id="dab7e-113">Você pode usar o [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contêm o nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="dab7e-113">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="dab7e-114">Para obter mais informações sobre como definir atributos de assembly, como versão, cultura e nome do assembly, consulte [set Assembly Attributes](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="dab7e-114">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="dab7e-115">Para obter mais informações sobre como dar um nome forte a um assembly, consulte [criar e usar assemblies de nome forte](create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="dab7e-115">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="dab7e-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dab7e-116">Example</span></span>

<span data-ttu-id="dab7e-117">O exemplo a seguir mostra como exibir o nome totalmente qualificado de um assembly que contém uma classe especificada para o console.</span><span class="sxs-lookup"><span data-stu-id="dab7e-117">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="dab7e-118">Ele usa a <xref:System.Type.Assembly?displayProperty=nameWithType> propriedade para recuperar uma referência a um assembly de um tipo que é definido nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="dab7e-118">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="dab7e-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="dab7e-119">See also</span></span>

- [<span data-ttu-id="dab7e-120">Nomes de assembly</span><span class="sxs-lookup"><span data-stu-id="dab7e-120">Assembly names</span></span>](names.md)
- [<span data-ttu-id="dab7e-121">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="dab7e-121">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="dab7e-122">Criar e usar assemblies com nome forte</span><span class="sxs-lookup"><span data-stu-id="dab7e-122">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="dab7e-123">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="dab7e-123">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="dab7e-124">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="dab7e-124">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
