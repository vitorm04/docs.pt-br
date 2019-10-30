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
# <a name="-operator-c-reference"></a><span data-ttu-id="8557a-102">Operador :: (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="8557a-102">:: operator (C# reference)</span></span>

<span data-ttu-id="8557a-103">Use o qualificador de alias de namespace `::` para acessar um membro de um namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="8557a-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="8557a-104">Você pode usar o qualificador `::` somente entre dois identificadores.</span><span class="sxs-lookup"><span data-stu-id="8557a-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="8557a-105">O identificador à esquerda pode ser qualquer um dos seguintes aliases:</span><span class="sxs-lookup"><span data-stu-id="8557a-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="8557a-106">Um alias de namespace criado com uma [diretiva de alias using](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="8557a-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="8557a-107">Um [alias extern](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="8557a-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="8557a-108">O alias `global`, que é o alias do namespace global.</span><span class="sxs-lookup"><span data-stu-id="8557a-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="8557a-109">O namespace global é o namespace que contém namespaces e tipos que não são declarados dentro de um namespace com nome.</span><span class="sxs-lookup"><span data-stu-id="8557a-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="8557a-110">Quando usado com o qualificador `::`, o alias `global` sempre faz referência ao namespace global, mesmo se houver o alias de namespace `global` definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="8557a-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="8557a-111">O exemplo a seguir usa o alias `global` para acessar o namespace .NET <xref:System>, que é um membro do namespace global.</span><span class="sxs-lookup"><span data-stu-id="8557a-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="8557a-112">Sem o alias `global`, o namespace `System` definido pelo usuário, que é um membro do namespace `MyCompany.MyProduct`, seria acessado:</span><span class="sxs-lookup"><span data-stu-id="8557a-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="8557a-113">A palavra-chave `global` é o alias do namespace global apenas quando é o identificador à esquerda do qualificador `::`.</span><span class="sxs-lookup"><span data-stu-id="8557a-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="8557a-114">Você também pode usar o [operador de `.` de acesso de membro](member-access-operators.md#member-access-operator-) para acessar um membro de um namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="8557a-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="8557a-115">No entanto, o operador de `.` também é usado para acessar um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="8557a-115">However, the `.` operator is also used to access a type member.</span></span> <span data-ttu-id="8557a-116">O qualificador `::` garante que o identificador à esquerda dele sempre faça referência a um alias de namespace, mesmo que exista um tipo ou namespace com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="8557a-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8557a-117">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8557a-117">C# language specification</span></span>

<span data-ttu-id="8557a-118">Saiba mais na seção [Qualificadores de alias de namespace](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8557a-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8557a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8557a-119">See also</span></span>

- [<span data-ttu-id="8557a-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8557a-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8557a-121">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="8557a-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="8557a-122">Usar namespaces</span><span class="sxs-lookup"><span data-stu-id="8557a-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
