---
title: Assemblies amigáveis
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348172"
---
# <a name="friend-assemblies"></a>Assemblies amigáveis

A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members. Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies. Isso é especialmente conveniente nos seguintes cenários:

- Durante os testes de unidade, quando o código de teste é executado em um assembly separado, mas exige acesso aos membros do assembly sendo testado que são marcados como `internal` no C# ou `Friend` no Visual Basic.

- Quando você está desenvolvendo uma biblioteca de classes e as adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `internal` no C# ou `Friend` no Visual Basic.

## <a name="remarks"></a>Comentários

Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly. The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly. This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.

> [!NOTE]
> When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file ( *.exe* or *.dll*) by using the **-out** compiler option. Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas. For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members. For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.

O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:

- If *Assembly A* is strong named, *AssemblyB* must also be strong named. The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.

     The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*. Don't include the assembly version, culture, architecture, or public key token.

- If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name. For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).

- If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option. For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).

 A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:

- <xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.

- If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them. Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.

- Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos. If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).

For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [How to: Create unsigned friend assemblies](create-unsigned-friend.md)
- [How to: Create signed friend assemblies](create-signed-friend.md)
- [Assemblies no .NET](index.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Programming concepts (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
