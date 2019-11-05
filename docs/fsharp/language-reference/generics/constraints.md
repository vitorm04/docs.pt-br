---
title: Restrições
description: Saiba mais F# sobre restrições que se aplicam a parâmetros de tipo genérico para especificar os requisitos para um argumento de tipo em um tipo ou função genérica.
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425012"
---
# <a name="constraints"></a>Restrições

Este tópico descreve as restrições que você pode aplicar a parâmetros de tipo genérico para especificar os requisitos para um argumento de tipo em um tipo ou função genérica.

## <a name="syntax"></a>Sintaxe

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Comentários

Há várias restrições diferentes que você pode aplicar para limitar os tipos que podem ser usados em um tipo genérico. A tabela a seguir lista e descreve essas restrições.

|Restrição|Sintaxe|Descrição|
|----------|------|-----------|
|Restrição de tipo|*tipo-parâmetro* : *tipo* de&gt;|O tipo fornecido deve ser igual ou derivado do tipo especificado, ou, se o tipo for uma interface, o tipo fornecido deverá implementar a interface.|
|Restrição NULL|*parâmetro de tipo* : nulo|O tipo fornecido deve dar suporte ao literal nulo. Isso inclui todos os tipos de objeto do F# .net, mas não os tipos lista, tupla, função, classe, registro ou União.|
|Restrição de membro explícita|[(]*tipo-parâmetro* [ou... ou *tipo-parâmetro*)]: (*assinatura de membro*)|Pelo menos um dos argumentos de tipo fornecidos deve ter um membro que tenha a assinatura especificada; Não se destina ao uso comum. Os membros devem ser explicitamente definidos no tipo ou parte de uma extensão de tipo implícita para serem destinos válidos para uma restrição de membro explícita.|
|Restrição de Construtor|*tipo-parâmetro* : (novo: unidade-&gt; ' a)|O tipo fornecido deve ter um construtor sem parâmetros.|
|Restrição de tipo de valor|: struct|O tipo fornecido deve ser um tipo de valor .NET.|
|Restrição de tipo de referência|: não struct|O tipo fornecido deve ser um tipo de referência do .NET.|
|Restrição de tipo de enumeração|: enum&lt;*tipo subjacente*&gt;|O tipo fornecido deve ser um tipo enumerado que tenha o tipo subjacente especificado; Não se destina ao uso comum.|
|Delegar restrição|: delegar&lt;*tupla-tipo de parâmetro*, tipo de *retorno*&gt;|O tipo fornecido deve ser um tipo delegado que tenha os argumentos especificados e o valor de retorno; Não se destina ao uso comum.|
|Restrição de comparação|: comparação|O tipo fornecido deve dar suporte à comparação.|
|Restrição de igualdade|: igualdade|O tipo fornecido deve dar suporte à igualdade.|
|Restrição não gerenciada|: não gerenciado|O tipo fornecido deve ser um tipo não gerenciado. Tipos não gerenciados são determinados tipos primitivos (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, ou `decimal`), tipos de enumeração, `nativeptr<_>`ou uma estrutura não genérica cujos campos são todos os tipos não gerenciados.|

Você precisa adicionar uma restrição quando seu código precisa usar um recurso que está disponível no tipo de restrição, mas não em tipos em geral. Por exemplo, se você usar a restrição de tipo para especificar um tipo de classe, poderá usar qualquer um dos métodos dessa classe na função ou no tipo genérico.

Às vezes, especificar restrições é necessário ao escrever parâmetros de tipo explicitamente, porque sem uma restrição, o compilador não tem como verificar se os recursos que você está usando estará disponível em qualquer tipo que possa ser fornecido no tempo de execução para o tipo meter.

As restrições mais comuns que você usa F# no código são restrições de tipo que especificam classes ou interfaces base. As outras restrições são usadas pela F# biblioteca para implementar determinadas funcionalidades, como a restrição de membro explícita, que é usada para implementar a sobrecarga de operador para operadores aritméticos ou são fornecidas principalmente porque F# dá suporte ao conjunto completo de restrições com suporte pelo Common Language Runtime.

Durante o processo de inferência de tipos, algumas restrições são inferidas automaticamente pelo compilador. Por exemplo, se você usar o operador de `+` em uma função, o compilador infere uma restrição de membro explícita em tipos de variáveis que são usados na expressão.

O código a seguir ilustra algumas declarações de restrição:

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

- [Genéricos](index.md)
- [Restrições](constraints.md)
