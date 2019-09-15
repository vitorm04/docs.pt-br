---
title: 'Como: Localizar o nome totalmente qualificado de um assembly'
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 4fc670adc80a6f4ce7b36074185dcd3bb85fbc67
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991307"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Como: Localizar o nome totalmente qualificado de um assembly

Para descobrir o nome totalmente qualificado de um .NET Framework assembly no cache de assembly global, use a ferramenta global assembly cache ([Gacutil. exe](../../framework/tools/gacutil-exe-gac-tool.md)). Confira [Como Exiba o conteúdo do cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)de assembly global.

Para assemblies do .NET Core e para .NET Framework assemblies que não estão no cache de assembly global, você pode obter o nome totalmente qualificado do assembly de várias maneiras:

- Você pode usar o código para gerar as informações para o console ou para uma variável, ou pode usar o [ILDASM. exe (desmontador Il)](../../framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contém o nome totalmente qualificado.

- Se o assembly já estiver carregado pelo aplicativo, você poderá recuperar o valor da propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado. Você pode usar a <xref:System.Type.Assembly> propriedade de um <xref:System.Type> definido nesse assembly para <xref:System.Reflection.Assembly> recuperar uma referência ao objeto. O exemplo fornece uma ilustração.

- Se você souber o caminho do sistema de arquivos do assembly, você pode `static` chamarC#o método `Shared` () ou <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> (Visual Basic) para obter o nome totalmente qualificado do assembly. Este é um exemplo simples.

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

- Você pode usar o [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contêm o nome totalmente qualificado.

Para obter mais informações sobre como definir atributos de assembly, como versão, cultura e nome do assembly, consulte [set Assembly Attributes](set-attributes.md). Para obter mais informações sobre como dar um nome forte a um assembly, consulte [criar e usar assemblies de nome forte](create-use-strong-named.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como exibir o nome totalmente qualificado de um assembly que contém uma classe especificada para o console. Ele usa a <xref:System.Type.Assembly?displayProperty=nameWithType> propriedade para recuperar uma referência a um assembly de um tipo que é definido nesse assembly.

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
Imports System
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

## <a name="see-also"></a>Consulte também

- [Nomes de assembly](names.md)
- [Criar assemblies](create.md)
- [Criar e usar assemblies de nome forte](create-use-strong-named.md)
- [Cache de assembly global](../../framework/app-domains/gac.md)
- [Como o tempo de execução localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programa com assemblies](program.md)
