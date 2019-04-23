---
title: 'Como: Determinar se um arquivo é um assembly (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: e8026ab5fa44b7601e54b5e76ebf9eb434596a07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340133"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="ba8dd-102">Como: Determinar se um arquivo é um assembly (C#)</span><span class="sxs-lookup"><span data-stu-id="ba8dd-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="ba8dd-103">Um arquivo será um assembly somente se ele for gerenciado e se contiver uma entrada de assembly em seus metadados.</span><span class="sxs-lookup"><span data-stu-id="ba8dd-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="ba8dd-104">Para obter mais informações sobre metadados e assemblies, consulte o tópico [Manifesto do assembly](../../../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="ba8dd-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="ba8dd-105">Como determinar manualmente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="ba8dd-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="ba8dd-106">Inicie o [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="ba8dd-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="ba8dd-107">Carregue o arquivo que você deseja testar.</span><span class="sxs-lookup"><span data-stu-id="ba8dd-107">Load the file you wish to test.</span></span>  
  
3. <span data-ttu-id="ba8dd-108">Se o **ILDASM** relatar que o arquivo não é um arquivo PE (executável portátil), então ele não será um assembly.</span><span class="sxs-lookup"><span data-stu-id="ba8dd-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="ba8dd-109">Para obter mais informações, confira o tópico [Como: exibir o conteúdo do assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="ba8dd-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="ba8dd-110">Como determinar programaticamente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="ba8dd-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="ba8dd-111">Chame o método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, passando o caminho do arquivo completo e o nome do arquivo que você está testando.</span><span class="sxs-lookup"><span data-stu-id="ba8dd-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="ba8dd-112">Se uma exceção <xref:System.BadImageFormatException> é gerada, o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="ba8dd-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba8dd-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba8dd-113">Example</span></span>  
 <span data-ttu-id="ba8dd-114">Este exemplo testa uma DLL para verificar se ela é um assembly.</span><span class="sxs-lookup"><span data-stu-id="ba8dd-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="ba8dd-115">O método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carrega o arquivo de teste e o libera quando a informação é lida.</span><span class="sxs-lookup"><span data-stu-id="ba8dd-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba8dd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba8dd-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="ba8dd-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ba8dd-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ba8dd-118">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="ba8dd-118">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
