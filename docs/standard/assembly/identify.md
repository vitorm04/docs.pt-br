---
title: Como determinar se um arquivo é um assembly
description: Este artigo mostra como determinar se um arquivo é um assembly .NET, manualmente e programaticamente.
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: fb1bcfa50ec380f10ab67cc47331f91dc3e4b32d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380143"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="2b05f-103">Como determinar se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="2b05f-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="2b05f-104">Um arquivo será um assembly somente se ele for gerenciado e se contiver uma entrada de assembly em seus metadados.</span><span class="sxs-lookup"><span data-stu-id="2b05f-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="2b05f-105">Para obter mais informações sobre assemblies e metadados, consulte [manifesto do assembly](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2b05f-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="2b05f-106">Como determinar manualmente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="2b05f-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="2b05f-107">Inicie o [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="2b05f-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="2b05f-108">Carregue o arquivo que você deseja testar.</span><span class="sxs-lookup"><span data-stu-id="2b05f-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="2b05f-109">Se o **ILDASM** relatar que o arquivo não é um arquivo PE (executável portátil), então ele não será um assembly.</span><span class="sxs-lookup"><span data-stu-id="2b05f-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="2b05f-110">Para obter mais informações, consulte o tópico [How to: View assembly Contents](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="2b05f-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="2b05f-111">Como determinar programaticamente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="2b05f-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="2b05f-112">Chame o método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>, passando o caminho do arquivo completo e o nome do arquivo que você está testando.</span><span class="sxs-lookup"><span data-stu-id="2b05f-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="2b05f-113">Se uma exceção <xref:System.BadImageFormatException> é gerada, o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="2b05f-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b05f-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b05f-114">Example</span></span>  
<span data-ttu-id="2b05f-115">Este exemplo testa uma DLL para verificar se ela é um assembly.</span><span class="sxs-lookup"><span data-stu-id="2b05f-115">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

<span data-ttu-id="2b05f-116">O método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carrega o arquivo de teste e o libera quando a informação é lida.</span><span class="sxs-lookup"><span data-stu-id="2b05f-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b05f-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="2b05f-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="2b05f-118">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="2b05f-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2b05f-119">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b05f-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="2b05f-120">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="2b05f-120">Assemblies in .NET</span></span>](index.md)
