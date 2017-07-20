---
title: "Como determinar se um arquivo é um assembly (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 9565d0af978f1a1bc3744db127ac75911b519ab2
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Como determinar se um arquivo é um assembly (C#)
Um arquivo será um assembly somente se ele for gerenciado e se contiver uma entrada de assembly em seus metadados. Para obter mais informações sobre metadados e assemblies, consulte o tópico [Manifesto do assembly](https://msdn.microsoft.com/library/1w45z383).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Como determinar manualmente se um arquivo é um assembly  
  
1.  Inicie o [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Carregue o arquivo que você deseja testar.  
  
3.  Se o **ILDASM** relatar que o arquivo não é um arquivo PE (executável portátil), então ele não será um assembly. Para obter mais informações, consulte o tópico [Como exibir o conteúdo de um assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Como determinar programaticamente se um arquivo é um assembly  
  
1.  Chame o método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, passando o caminho do arquivo completo e o nome do arquivo que você está testando.  
  
2.  Se uma exceção <xref:System.BadImageFormatException> é gerada, o arquivo não é um assembly.  
  
## <a name="example"></a>Exemplo  
 Este exemplo testa uma DLL para verificar se ela é um assembly.  
  
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
  
 O método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carrega o arquivo de teste e o libera quando a informação é lida.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.AssemblyName>   
 [Guia de programação em C#](../../../../csharp/programming-guide/index.md)   
 [Assemblies e o Cache de Assembly Global (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
