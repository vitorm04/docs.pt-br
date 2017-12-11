---
title: "Como determinar se um arquivo é um assembly (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 09e56f3c0310a519594d0a53d8094275e1accec6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="1bc96-102">Como determinar se um arquivo é um assembly (C#)</span><span class="sxs-lookup"><span data-stu-id="1bc96-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="1bc96-103">Um arquivo será um assembly somente se ele for gerenciado e se contiver uma entrada de assembly em seus metadados.</span><span class="sxs-lookup"><span data-stu-id="1bc96-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="1bc96-104">Para obter mais informações sobre metadados e assemblies, consulte o tópico [Manifesto do assembly](../../../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="1bc96-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="1bc96-105">Como determinar manualmente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="1bc96-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="1bc96-106">Inicie o [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="1bc96-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="1bc96-107">Carregue o arquivo que você deseja testar.</span><span class="sxs-lookup"><span data-stu-id="1bc96-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="1bc96-108">Se o **ILDASM** relatar que o arquivo não é um arquivo PE (executável portátil), então ele não será um assembly.</span><span class="sxs-lookup"><span data-stu-id="1bc96-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="1bc96-109">Para obter mais informações, consulte o tópico [Como exibir o conteúdo de um assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="1bc96-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="1bc96-110">Como determinar programaticamente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="1bc96-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="1bc96-111">Chame o método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, passando o caminho do arquivo completo e o nome do arquivo que você está testando.</span><span class="sxs-lookup"><span data-stu-id="1bc96-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="1bc96-112">Se uma exceção <xref:System.BadImageFormatException> é gerada, o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="1bc96-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc96-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bc96-113">Example</span></span>  
 <span data-ttu-id="1bc96-114">Este exemplo testa uma DLL para verificar se ela é um assembly.</span><span class="sxs-lookup"><span data-stu-id="1bc96-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```  
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
  
 <span data-ttu-id="1bc96-115">O método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carrega o arquivo de teste e o libera quando a informação é lida.</span><span class="sxs-lookup"><span data-stu-id="1bc96-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc96-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bc96-116">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="1bc96-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1bc96-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1bc96-118">Assemblies e o Cache de Assembly Global (C#)</span><span class="sxs-lookup"><span data-stu-id="1bc96-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
