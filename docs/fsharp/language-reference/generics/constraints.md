---
title: Restrições (F#)
description: 'Saiba mais sobre restrições de F # que se aplicam a parâmetros de tipo genérico para especificar os requisitos para um argumento de tipo em um tipo genérico ou uma função.'
ms.date: 05/16/2016
ms.openlocfilehash: 7af064159d2722256f0db8286a99fc02435a99cd
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936859"
---
# <a name="constraints"></a>Restrições

Este tópico descreve as restrições que você pode aplicar a genérica parâmetros para especificar os requisitos para um argumento de tipo em um tipo genérico ou uma função de tipo.


## <a name="syntax"></a>Sintaxe

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Comentários
Há várias restrições diferentes que você pode aplicar para limitar os tipos que podem ser usados em um tipo genérico. A tabela a seguir lista e descreve essas restrições.

|Restrição|Sintaxe|Descrição|
|----------|------|-----------|
|Restrição de tipo|*parâmetro de tipo* :&gt; *tipo*|O tipo fornecido deve ser igual ou derivada do tipo especificado ou, se o tipo é uma interface, o tipo fornecido deve implementar a interface.|
|Restrição de nulos|*parâmetro de tipo* : nulo|O tipo fornecido deve suportar o literal nulo. Isso inclui todos os tipos de objeto do .NET, mas não F # lista, tupla, função, classe, registro ou tipos de união.|
|Restrição de membro explícito|[()]*parâmetro de tipo* [ou... ou *parâmetro de tipo*)]: (*assinatura do membro*)|Pelo menos um dos argumentos de tipo fornecidos deve ter um membro que tem a assinatura especificada; não se destina para uso comum. Membros devem ser seja explicitamente definidos no tipo ou parte de uma extensão de tipo implícito alvos válidos de uma restrição explícita do membro.|
|Restrição de construtor|*parâmetro de tipo* : (novo: unidade -&gt; ' um)|O tipo fornecido deve ter um construtor padrão.|
|Restrição de tipo de valor|: struct|O tipo fornecido deve ser um tipo de valor do .NET.|
|Restrição de tipo de referência|: não struct|O tipo fornecido deve ser um tipo de referência do .NET.|
|Restrição de tipo de enumeração|: enum&lt;*tipo subjacente*&gt;|O tipo fornecido deve ser um tipo enumerado que tem o tipo subjacente especificado. não se destina para uso comum.|
|Restrição de delegado|: Delegar&lt;*tipo de parâmetro de tupla*, *tipo de retorno*&gt;|O tipo fornecido deve ser um tipo de delegado que tem os argumentos especificados e retornar o valor; não se destina para uso comum.|
|Restrição de comparação|: comparação|O tipo fornecido deve oferecer suporte à comparação.|
|Restrição de igualdade|: igualdade|O tipo fornecido deve dar suporte à igualdade.|
|Restrição não gerenciada|: não gerenciado|O tipo fornecido deve ser um tipo não gerenciado. Tipos não gerenciados são determinados tipos de primitivos (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, ou `decimal`), tipos de enumeração, `nativeptr&lt;_&gt;`, ou uma estrutura de não-genérica cujos campos são todos os tipos não gerenciados.|
Você precisa adicionar uma restrição quando seu código precisa usar um recurso que está disponível no tipo de restrição mas não em tipos em geral. Por exemplo, se você usar a restrição de tipo para especificar um tipo de classe, você pode usar qualquer um dos métodos da classe na função genérica ou tipo.

Especifica as restrições às vezes, é necessário ao escrever os parâmetros de tipo explicitamente, porque sem uma restrição, o compilador tem uma forma de verificar que os recursos que você está usando serão disponibilizado em qualquer tipo que pode ser fornecido em tempo de execução para o tipo de parâmetro.

As restrições mais comuns que você usa no código F # são restrições de tipo que especificam a interfaces ou classes base. As outras restrições são usadas pela biblioteca de F # para implementar algumas funcionalidades, como a restrição de membro explícito, que é usada para implementar o sobrecarregamento de operadores aritméticos ou é fornecida principalmente como F # oferece suporte completo conjunto de restrições que é compatível com o common language runtime.

Durante o processo de inferência de tipo, algumas restrições são inferidas automaticamente pelo compilador. Por exemplo, se você usar o `+` operador em uma função, o compilador infere uma restrição de membro explícito em tipos de variáveis que são usadas na expressão.

O código a seguir ilustra algumas declarações de restrição.

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>Consulte também
[Genéricos](index.md)

[Restrições](constraints.md)
