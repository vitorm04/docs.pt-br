---
title: Restrições ao uso de níveis de acessibilidade – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: ef1c0a93da2a53f1e199627fb7f83894d01e714a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239323"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Restrições ao uso de níveis de acessibilidade (Referência em C#)

Quando você especifica um tipo em uma declaração, verifique se o nível de acessibilidade do tipo é dependente do nível de acessibilidade de um membro ou de outro tipo. Por exemplo, a classe base direta deve ser, pelo menos, tão acessível quanto a classe derivada. As seguintes declarações causam um erro do compilador porque a classe base `BaseClass` é menos acessível que a `MyClass`:

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

A tabela a seguir resume as restrições nos níveis de acessibilidade declarada.

|Contexto|Comentários|
|-------------|-------------|
|[Classes](../../programming-guide/classes-and-structs/classes.md)|A classe base direta de um tipo de classe deve ser, pelo menos, tão acessível quanto o próprio tipo de classe.|
|[Interfaces](../../programming-guide/interfaces/index.md)|As interfaces base explícitas de um tipo de interface devem ser, pelo menos, tão acessíveis quanto o próprio tipo de interface.|
|[Delegados](../../programming-guide/delegates/index.md)|O tipo de retorno e os tipos de parâmetro de um tipo delegado devem ser, pelo menos, tão acessíveis quanto o próprio tipo delegado.|
|[Constantes](../../programming-guide/classes-and-structs/constants.md)|O tipo de uma constante deve ser, pelo menos, tão acessível quanto a própria constante.|
|[Campos](../../programming-guide/classes-and-structs/fields.md)|O tipo de um campo deve ser, pelo menos, tão acessível quanto o próprio campo.|
|[Métodos](../../programming-guide/classes-and-structs/methods.md)|O tipo de retorno e os tipos de parâmetro de um método devem ser, pelo menos, tão acessíveis quanto o próprio método.|
|[Propriedades](../../programming-guide/classes-and-structs/properties.md)|O tipo de uma propriedade deve ser, pelo menos, tão acessível quanto a propriedade em si.|
|[Eventos](../../programming-guide/events/index.md)|O tipo de um evento deve ser, pelo menos, tão acessível quanto o próprio evento.|
|[Indexadores](../../programming-guide/indexers/index.md)|O tipo e os tipos de parâmetro de um indexador devem ser, pelo menos, tão acessíveis quanto o próprio indexador.|
|[Operadores](../../programming-guide/statements-expressions-operators/operators.md)|O tipo de retorno e os tipos de parâmetro de um operador devem ser, pelo menos, tão acessíveis quanto o próprio operador.|
|[Construtores](../../programming-guide/classes-and-structs/constructors.md)|Os tipos de parâmetro de um construtor devem ser, pelo menos, tão acessíveis quanto o próprio construtor.|

## <a name="example"></a>Exemplo

O exemplo a seguir contém declarações incorretas de tipos diferentes. O comentário que segue cada declaração indica o erro do compilador esperado.

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible 
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error: 
    // "The parameter B.MyPrivateMethod is not accessible due to 
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../language-reference/index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](../../language-reference/keywords/index.md)
- [Modificadores de acesso](../../language-reference/keywords/access-modifiers.md)
- [Domínio de acessibilidade](../../language-reference/keywords/accessibility-domain.md)
- [Níveis de acessibilidade](../../language-reference/keywords/accessibility-levels.md)
- [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../language-reference/keywords/public.md)
- [private](../../language-reference/keywords/private.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)