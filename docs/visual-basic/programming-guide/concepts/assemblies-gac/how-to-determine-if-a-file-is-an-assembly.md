---
title: 'Como: Determinar se um arquivo é um Assembly (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: b8627c64398afdef00fde71121f870b337ac072f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520081"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="b0312-102">Como: Determinar se um arquivo é um Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0312-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="b0312-103">Um arquivo será um assembly somente se ele for gerenciado e se contiver uma entrada de assembly em seus metadados.</span><span class="sxs-lookup"><span data-stu-id="b0312-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="b0312-104">Para obter mais informações sobre metadados e assemblies, consulte o tópico [Manifesto do assembly](../../../../framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b0312-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="b0312-105">Como determinar manualmente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="b0312-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="b0312-106">Inicie o [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="b0312-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="b0312-107">Carregue o arquivo que você deseja testar.</span><span class="sxs-lookup"><span data-stu-id="b0312-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="b0312-108">Se o **ILDASM** relatar que o arquivo não é um arquivo PE (executável portátil), então ele não será um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0312-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="b0312-109">Para obter mais informações, consulte o tópico [como: exibir o conteúdo do assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="b0312-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="b0312-110">Como determinar programaticamente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="b0312-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="b0312-111">Chame o método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, passando o caminho do arquivo completo e o nome do arquivo que você está testando.</span><span class="sxs-lookup"><span data-stu-id="b0312-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="b0312-112">Se uma exceção <xref:System.BadImageFormatException> é gerada, o arquivo não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0312-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0312-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0312-113">Example</span></span>  
 <span data-ttu-id="b0312-114">Este exemplo testa uma DLL para verificar se ela é um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0312-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="b0312-115">O método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carrega o arquivo de teste e o libera quando a informação é lida.</span><span class="sxs-lookup"><span data-stu-id="b0312-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0312-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0312-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="b0312-117">Conceitos de Programação</span><span class="sxs-lookup"><span data-stu-id="b0312-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="b0312-118">Assemblies e o cache de assembly global (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0312-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
