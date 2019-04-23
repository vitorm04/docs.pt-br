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
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Como: Determinar se um arquivo é um assembly (C#)
Um arquivo será um assembly somente se ele for gerenciado e se contiver uma entrada de assembly em seus metadados. Para obter mais informações sobre metadados e assemblies, consulte o tópico [Manifesto do assembly](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Como determinar manualmente se um arquivo é um assembly  
  
1. Inicie o [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Carregue o arquivo que você deseja testar.  
  
3. Se o **ILDASM** relatar que o arquivo não é um arquivo PE (executável portátil), então ele não será um assembly. Para obter mais informações, confira o tópico [Como: exibir o conteúdo do assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Como determinar programaticamente se um arquivo é um assembly  
  
1. Chame o método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, passando o caminho do arquivo completo e o nome do arquivo que você está testando.  
  
2. Se uma exceção <xref:System.BadImageFormatException> é gerada, o arquivo não é um assembly.  
  
## <a name="example"></a>Exemplo  
 Este exemplo testa uma DLL para verificar se ela é um assembly.  
  
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
  
 O método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carrega o arquivo de teste e o libera quando a informação é lida.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.AssemblyName>
- [Guia de Programação em C#](../../../../csharp/programming-guide/index.md)
- [Assemblies no .NET](../../../../standard/assembly/index.md)
