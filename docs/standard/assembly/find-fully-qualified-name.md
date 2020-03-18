---
title: 'Como: Encontrar o nome totalmente qualificado de uma assembléia'
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
ms.openlocfilehash: 49ebaeabee7a346fb84f09e5a9e34590d1ea9811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348193"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Como: Encontrar o nome totalmente qualificado de uma assembléia

Para descobrir o nome totalmente qualificado de um conjunto .NET Framework no cache de montagem global, use a ferramenta Global Assembly Cache[(Gacutil.exe).](../../framework/tools/gacutil-exe-gac-tool.md) [Veja Como: Veja o conteúdo do cache de montagem global](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

Para as assembléias do .NET Core e para as montagens do .NET Framework que não estão no cache de montagem global, você pode obter o nome de montagem totalmente qualificado de várias maneiras:

- Você pode usar o código para produzir as informações para o console ou para uma variável, ou pode usar o [Ildasm.exe (IL Desassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do conjunto, que contém o nome totalmente qualificado.

- Se o assembly já estiver carregado pelo aplicativo, você poderá recuperar o valor da propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado. Você pode <xref:System.Type.Assembly> usar a <xref:System.Type> propriedade de um conjunto definido <xref:System.Reflection.Assembly> para recuperar uma referência ao objeto. O exemplo fornece uma ilustração.

- Se você conhece o caminho do sistema de `static` arquivos do `Shared` conjunto, você <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> pode chamar o método (C#) ou (Visual Basic) para obter o nome de montagem totalmente qualificado. A seguir há um exemplo simples.

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

Para obter mais informações sobre a definição de atributos de montagem, como versão, cultura e nome de montagem, consulte [Definir atributos de montagem](set-attributes.md). Para obter mais informações sobre como dar um nome forte a um conjunto, consulte [Criar e usar conjuntos com nomes fortes](create-use-strong-named.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como exibir o nome totalmente qualificado de um conjunto contendo uma classe especificada para o console. Ele usa <xref:System.Type.Assembly?displayProperty=nameWithType> a propriedade para recuperar uma referência a um conjunto de um tipo definido nessa montagem.

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

## <a name="see-also"></a>Confira também

- [Nomes de assembly](names.md)
- [Criar assemblies](create.md)
- [Criar e usar assemblies com nome forte](create-use-strong-named.md)
- [Cache de montagem global](../../framework/app-domains/gac.md)
- [Como o tempo de execução localiza conjuntos](../../framework/deployment/how-the-runtime-locates-assemblies.md)
