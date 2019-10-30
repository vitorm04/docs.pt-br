---
title: 'Operador :: – referência do C#'
ms.custom: seodec18
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 97ed24b050f79cf44ffd1c03c213ffcf91758260
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038988"
---
# <a name="-operator-c-reference"></a>Operador :: (referência do C#)

Use o qualificador de alias de namespace `::` para acessar um membro de um namespace com alias. Você pode usar o qualificador `::` somente entre dois identificadores. O identificador à esquerda pode ser qualquer um dos seguintes aliases:

- Um alias de namespace criado com uma [diretiva de alias using](../keywords/using-directive.md):

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- Um [alias extern](../keywords/extern-alias.md).
- O alias `global`, que é o alias do namespace global. O namespace global é o namespace que contém namespaces e tipos que não são declarados dentro de um namespace com nome. Quando usado com o qualificador `::`, o alias `global` sempre faz referência ao namespace global, mesmo se houver o alias de namespace `global` definido pelo usuário.

  O exemplo a seguir usa o alias `global` para acessar o namespace .NET <xref:System>, que é um membro do namespace global. Sem o alias `global`, o namespace `System` definido pelo usuário, que é um membro do namespace `MyCompany.MyProduct`, seria acessado:

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > A palavra-chave `global` é o alias do namespace global apenas quando é o identificador à esquerda do qualificador `::`.

Você também pode usar o [operador de `.` de acesso de membro](member-access-operators.md#member-access-operator-) para acessar um membro de um namespace com alias. No entanto, o operador de `.` também é usado para acessar um membro de tipo. O qualificador `::` garante que o identificador à esquerda dele sempre faça referência a um alias de namespace, mesmo que exista um tipo ou namespace com o mesmo nome.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Saiba mais na seção [Qualificadores de alias de namespace](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Usar namespaces](../../programming-guide/namespaces/using-namespaces.md)
