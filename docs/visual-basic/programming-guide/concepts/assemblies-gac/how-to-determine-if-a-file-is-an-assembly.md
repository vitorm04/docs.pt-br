---
title: 'Como: Determinar se um arquivo é um Assembly (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: 47ac7f29509af86819006a4394ca661140b95ab0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022162"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Como: Determinar se um arquivo é um Assembly (Visual Basic)
Um arquivo será um assembly somente se ele for gerenciado e se contiver uma entrada de assembly em seus metadados. Para obter mais informações sobre metadados e assemblies, consulte o tópico [Manifesto do assembly](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Como determinar manualmente se um arquivo é um assembly  
  
1. Inicie o [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Carregue o arquivo que você deseja testar.  
  
3. Se o **ILDASM** relatar que o arquivo não é um arquivo PE (executável portátil), então ele não será um assembly. Para obter mais informações, confira o tópico [Como: exibir o conteúdo do assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Como determinar programaticamente se um arquivo é um assembly  
  
1. Chame o método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, passando o caminho do arquivo completo e o nome do arquivo que você está testando.  
  
2. Se uma exceção <xref:System.BadImageFormatException> é gerada, o arquivo não é um assembly.  
  
## <a name="example"></a>Exemplo  
 Este exemplo testa uma DLL para verificar se ela é um assembly.  
  
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
  
 O método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carrega o arquivo de teste e o libera quando a informação é lida.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.AssemblyName>
- [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)
- [Assemblies e o cache de assembly global (Visual Basic)](index.md)
