---
title: Como localizar o nome totalmente qualificado de um assembly
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 49d6d6cf5c138df671d061beb23cb57bcb0667b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140295"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Como localizar o nome totalmente qualificado de um assembly

Para descobrir o nome totalmente qualificado de um .NET Framework assembly no cache de assembly global, use a ferramenta global assembly cache ([Gacutil. exe](../../framework/tools/gacutil-exe-gac-tool.md)). Consulte [como: exibir o conteúdo do cache de assembly global](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

Para assemblies do .NET Core e para .NET Framework assemblies que não estão no cache de assembly global, você pode obter o nome totalmente qualificado do assembly de várias maneiras:

- Você pode usar o código para gerar as informações para o console ou para uma variável, ou pode usar o [ILDASM. exe (desmontador Il)](../../framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contém o nome totalmente qualificado.

- Se o assembly já estiver carregado pelo aplicativo, você poderá recuperar o valor da propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado. Você pode usar a propriedade <xref:System.Type.Assembly> de uma <xref:System.Type> definida nesse assembly para recuperar uma referência ao objeto <xref:System.Reflection.Assembly>. O exemplo fornece uma ilustração.

- Se você souber o caminho do sistema de arquivos do assembly, poderá chamar o métodoC#`static` () ou `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado do assembly. Este é um exemplo simples.

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

O exemplo a seguir mostra como exibir o nome totalmente qualificado de um assembly que contém uma classe especificada para o console. Ele usa a propriedade <xref:System.Type.Assembly?displayProperty=nameWithType> para recuperar uma referência a um assembly de um tipo que é definido nesse assembly.

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
