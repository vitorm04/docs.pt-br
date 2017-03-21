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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2e58363369ae4420879310bf09ed89cdd4f5b5cc
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Como: determinar se um arquivo é um Assembly (Visual Basic)
Um arquivo é um assembly somente se ele é gerenciado e contém uma entrada de assembly em seus metadados. Para obter mais informações sobre metadados e assemblies, consulte o tópico [manifesto do Assembly](https://msdn.microsoft.com/library/1w45z383).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Como determinar manualmente se um arquivo é um assembly  
  
1.  Iniciar o [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Carregar o arquivo que você deseja testar.  
  
3.  Se **ILDASM** relatórios que o arquivo não é um arquivo executável portátil (PE), não é um assembly. Para obter mais informações, consulte o tópico [como: exibir o conteúdo do Assembly](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Como determinar programaticamente se um arquivo é um assembly  
  
1.  Chamar o <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>método, passando o caminho completo e o nome do arquivo que você está testando.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>  
  
2.  Se um <xref:System.BadImageFormatException>exceção é lançada, o arquivo não é um assembly.</xref:System.BadImageFormatException>  
  
## <a name="example"></a>Exemplo  
 Este exemplo testa uma DLL para verificar se ele é um assembly.  
  
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
  
 O <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>método carrega o arquivo de teste e libera quando a informação é lida.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>   
 [Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Assemblies e o Cache de Assembly Global (Visual Basic)](index.md)
