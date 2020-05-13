---
title: Assemblies amigáveis
description: Um assembly Friend é um assembly .NET que pode acessar os tipos e membros internos (C#) ou Friend (Visual Basic) de outro assembly.
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378927"
---
# <a name="friend-assemblies"></a>Assemblies amigáveis

Um *assembly Friend* é um assembly que pode acessar os tipos e membros [internos](../../csharp/language-reference/keywords/internal.md) (C#) ou [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) de outro assembly. Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies. Isso é especialmente conveniente nos seguintes cenários:

- Durante os testes de unidade, quando o código de teste é executado em um assembly separado, mas exige acesso aos membros do assembly sendo testado que são marcados como `internal` no C# ou `Friend` no Visual Basic.

- Quando você está desenvolvendo uma biblioteca de classes e as adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `internal` no C# ou `Friend` no Visual Basic.

## <a name="remarks"></a>Comentários

Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly. O exemplo a seguir usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo no *assembly A* e especifica o assembly *AssemblyB* como um assembly Friend. Isso dá ao assembly *AssemblyB* acesso a todos os tipos e membros no *assembly A* que são marcados como `internal` em C# ou `Friend` em Visual Basic.

> [!NOTE]
> Quando você compila um assembly como *AssemblyB* que acessará tipos internos ou membros internos de outro assembly, como *assembly a*, você deve especificar explicitamente o nome do arquivo de saída (*. exe* ou *. dll*) usando a opção de compilador **-out** . Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas. Para obter mais informações, consulte [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

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

Somente os assemblies que você especifica explicitamente como amigos podem acessar `internal` os tipos e membros do (C#) ou `Friend` (Visual Basic). Por exemplo, se *AssemblyB* for um amigo do *assembly a e o* *assembly c* fizer referência a *AssemblyB*, o *assembly c* não terá acesso aos `internal` tipos (C#) ou `Friend` (Visual Basic) no *assembly a*.

O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Se o *assembly A* declarar *AssemblyB* como um assembly Friend, as regras de validação serão as seguintes:

- Se *o assembly A tiver um* nome forte, *AssemblyB* também deverá ter um nome forte. O nome do assembly Friend que é passado para o atributo deve consistir no nome do assembly e na chave pública da chave de nome forte que é usada para assinar *AssemblyB*.

     O nome do assembly Friend que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo não pode ser o nome forte de *AssemblyB*. Não inclua a versão do assembly, a cultura, a arquitetura ou o token de chave pública.

- Se o *assembly A* não for de nome forte, o nome do assembly Friend deverá consistir apenas no nome do assembly. Para obter mais informações, consulte [como: criar assemblies Friend não assinados](create-unsigned-friend.md).

- Se *AssemblyB* for de nome forte, você deverá especificar a chave de nome forte para *AssemblyB* usando a configuração do projeto ou a opção do compilador de linha de comando `/keyfile` . Para obter mais informações, consulte [como criar assemblies Friend assinados](create-signed-friend.md).

 A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:

- <xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.

- Se houver centenas de tipos no *assembly a* que você deseja compartilhar com *AssemblyB*, você precisará adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles. Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.

- Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos. Se você usar um assembly Friend, os tipos compartilhados serão declarados como `internal` (C#) ou `Friend` (Visual Basic).

Para obter informações sobre como acessar `internal` os tipos e métodos de um assembly (C#) ou `Friend` (Visual Basic) de um arquivo de módulo (um arquivo com a extensão *. netmodule* ), consulte [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Confira também

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Como: criar assemblies Friend não assinados](create-unsigned-friend.md)
- [Como criar assemblies Friend assinados](create-signed-friend.md)
- [Assemblies no .NET](index.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
