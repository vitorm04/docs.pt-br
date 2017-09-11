---
title: "Como: determinar se um arquivo é um Assembly (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4bd3404cbdc3b79ff92290a53574080bf197fe9d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="c68ab-102">Como: determinar se um arquivo é um Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68ab-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="c68ab-103">Um arquivo é um assembly somente se ele é gerenciado e contém uma entrada de assembly em seus metadados.</span><span class="sxs-lookup"><span data-stu-id="c68ab-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="c68ab-104">Para obter mais informações sobre metadados e assemblies, consulte o tópico [manifesto do Assembly](https://msdn.microsoft.com/library/1w45z383).</span><span class="sxs-lookup"><span data-stu-id="c68ab-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="c68ab-105">Como determinar manualmente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="c68ab-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="c68ab-106">Iniciar o [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="c68ab-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="c68ab-107">Carregar o arquivo que você deseja testar.</span><span class="sxs-lookup"><span data-stu-id="c68ab-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="c68ab-108">Se **ILDASM** relatórios que o arquivo não é um arquivo executável portátil (PE), não é um assembly.</span><span class="sxs-lookup"><span data-stu-id="c68ab-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="c68ab-109">Para obter mais informações, consulte o tópico [como: exibir o conteúdo do Assembly](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).</span><span class="sxs-lookup"><span data-stu-id="c68ab-109">For more information, see the topic [How to: View Assembly Contents](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="c68ab-110">Como determinar programaticamente se um arquivo é um assembly</span><span class="sxs-lookup"><span data-stu-id="c68ab-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="c68ab-111">Chamar o <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>método, passando o caminho completo e o nome do arquivo que você está testando.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A></span><span class="sxs-lookup"><span data-stu-id="c68ab-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="c68ab-112">Se um <xref:System.BadImageFormatException>exceção é lançada, o arquivo não é um assembly.</xref:System.BadImageFormatException></span><span class="sxs-lookup"><span data-stu-id="c68ab-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c68ab-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c68ab-113">Example</span></span>  
 <span data-ttu-id="c68ab-114">Este exemplo testa uma DLL para verificar se ele é um assembly.</span><span class="sxs-lookup"><span data-stu-id="c68ab-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="c68ab-115">O <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>método carrega o arquivo de teste e libera quando a informação é lida.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A></span><span class="sxs-lookup"><span data-stu-id="c68ab-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68ab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c68ab-116">See Also</span></span>  
 <span data-ttu-id="c68ab-117"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="c68ab-117"><xref:System.Reflection.AssemblyName></span></span>   
<span data-ttu-id="c68ab-118"> [Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="c68ab-118"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="c68ab-119"> [Assemblies e o Cache de Assembly Global (Visual Basic)](index.md)</span><span class="sxs-lookup"><span data-stu-id="c68ab-119"> [Assemblies and the Global Assembly Cache (Visual Basic)](index.md)</span></span>
