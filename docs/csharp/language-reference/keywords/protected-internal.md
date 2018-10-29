---
title: protected internal (referência do C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: e5763830a29d4e627dbb8efa0e86fca536bbb26c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193767"
---
# <a name="protected-internal-c-reference"></a>protected internal (referência do C#)

A combinação de palavras-chave `protected internal` é um modificador de acesso de membro. Um membro protegido interno é acessível no assembly atual ou nos tipos que derivam da classe recipiente. Para obter uma comparação de `protected internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md).

## <a name="example"></a>Exemplo

Um membro protegido interno de uma classe base é acessível em qualquer tipo em seu assembly recipiente. Ele também é acessível em uma classe derivada localizada em outro assembly somente se o acesso ocorre por meio de uma variável do tipo de classe derivada. Por exemplo, considere o seguinte segmento de código:

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```
Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly2.cs`.
O primeiro arquivo contém uma classe base pública, `BaseClass`, e outra classe, `TestAccess`. `BaseClass` tem um membro interno protegido, `myValue`, que é acessado pelo tipo `TestAccess`.
No segundo arquivo, uma tentativa de acessar `myValue` por meio de uma instância de `BaseClass` produzirá um erro, enquanto um acesso a esse membro por meio de uma instância de uma classe derivada, `DerivedClass`, terá êxito.

Membros de struct não podem ser `protected internal` porque o struct não pode ser herdado.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Modificadores de acesso](access-modifiers.md)
- [Níveis de acessibilidade](accessibility-levels.md)
- [Modificadores](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Questões de segurança de palavras-chave virtuais internas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))