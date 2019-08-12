---
title: Assemblies amigáveis (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68671191"
---
# <a name="friend-assemblies"></a>Assemblies amigáveis

Um *assembly amigável* é um assembly que pode acessar os membros e tipos [internos](../../csharp/language-reference/keywords/internal.md) de outro assembly (no C# ou [Amigável](../../visual-basic/language-reference/modifiers/friend.md) no Visual Basic). Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies. Isso é especialmente conveniente nos seguintes cenários:

- Durante os testes de unidade, quando o código de teste é executado em um assembly separado, mas exige acesso aos membros do assembly sendo testado que são marcados como `internal` no C# ou `Friend` no Visual Basic.

- Quando você está desenvolvendo uma biblioteca de classes e as adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `internal` no C# ou `Friend` no Visual Basic.

## <a name="remarks"></a>Comentários

Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly. O exemplo a seguir usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> no assembly A e especifica o assembly `AssemblyB` como um assembly amigável. Isso fornece ao assembly `AssemblyB` acesso a todos os tipos e membros do assembly A que são marcados como `internal` no C# ou `Friend` no Visual Basic.

> [!NOTE]
> Quando você compila um assembly (assembly `AssemblyB`) que acessará tipos internos ou membros internos de outro assembly (assembly *A*), deve especificar explicitamente o nome do arquivo de saída (.exe ou .dll) usando a opção do compilador **/out**. Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas. Para obter mais informações, confira [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

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

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

```vb
Imports System.Runtime.CompilerServices
Imports System
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

---

Apenas os assemblies que você especificar explicitamente como amigáveis podem acessar os membros e os tipos `internal` (no C# ou `Friend` no Visual Basic). Por exemplo, se o assembly B for amigável para o assembly A e o assembly C fizer referência ao assembly B, C não terá acesso aos tipos `internal` (no C# ou `Friend` no Visual Basic) de A.

O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Se o assembly *A* declara o *B* como um assembly amigável, as regras de validação são as seguintes:

- Se o assembly *A* for fortemente nomeado, o assembly *B* também deverá ser fortemente nomeado. O nome do assembly amigável passado para o atributo deve consistir no nome do assembly e a chave pública da chave de nome forte usada para assinar o assembly *B*.

     O nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> não pode ser o nome forte do assembly *B*: não inclua a versão, cultura, arquitetura ou token de chave pública do assembly.

- Se o assembly *A* não tiver um nome forte, o nome do assembly amigável deverá consistir apenas no nome do assembly. Para obter mais informações, confira [Como: Como criar assemblies amigáveis sem sinal (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) ou [Como: Criar assemblies amigáveis sem sinal (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).

- Se o assembly *B* tiver um nome forte, você deverá especificara a chave de nome forte do assembly *B* usando a configuração do projeto ou a opção do compilador `/keyfile` de linha de comando. Para obter mais informações, confira [Como: Criar assemblies amigáveis com sinal (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) ou [Como: Criar assemblies amigáveis com sinal (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).

 A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:

- <xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.

- Se há centenas de tipos no assembly *A* que você deseja compartilhar como o assembly *B*, é necessário adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles. Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.

- Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos. Se você usar um assembly amigável, os tipos compartilhados serão declarados como `internal` (no C# ou `Friend` no Visual Basic).

Para obter informações sobre como acessar os métodos e os tipos `internal` (no C# ou `Friend` no Visual Basic) de um assembly em um arquivo de módulo (um arquivo com a extensão .netmodule), confira [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Como: Criar assemblies amigáveis sem sinal (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Como: Criar assemblies amigáveis sem sinal (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Como: Criar assemblies amigáveis com sinal (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Como: Criar assemblies amigáveis com sinal (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Assemblies no .NET](index.md)
- [Guia de Programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de Programação](../../visual-basic/programming-guide/concepts/index.md)
