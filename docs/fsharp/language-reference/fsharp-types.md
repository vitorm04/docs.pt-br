---
title: Tipos F#
description: Saiba mais sobre os tipos que são usados em F# e como F# tipos são chamados e descritos.
ms.date: 05/16/2016
ms.openlocfilehash: b48376c80b48df210bf7bc699a769d40fec60864
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934635"
---
# <a name="f-types"></a>Tipos F#

Este tópico descreve os tipos que são usados em F# e como F# tipos são chamados e descritos.

## <a name="summary-of-f-types"></a>Resumo de F# tipos
Alguns tipos são considerados *tipos primitivos*, como o tipo Boolean `bool` e tipos de ponto flutuante e integral dos vários tamanhos, que incluem tipos de bytes e caracteres. Esses tipos são descritos em [tipos primitivos](primitive-types.md).

Outros tipos que são integrados à linguagem incluem tuplas, listas, matrizes, sequências, registros e uniões discriminadas. Se você tiver experiência com outras linguagens .NET e são learning F#, você deve ler os tópicos para cada um desses tipos. Links para obter mais informações sobre esses tipos são incluídos na [tópicos relacionados](https://msdn.microsoft.com/library/#rel) seção deste tópico. Esses F#-tipos específicos oferecem suporte a estilos de programação que são comuns a linguagens de programação funcionais. Muitos desses tipos associou módulos no F# que dão suporte a operações comuns nesses tipos de biblioteca.

O tipo de uma função inclui informações sobre os tipos de parâmetro e tipo de retorno.

O .NET Framework é a fonte dos tipos de objeto, tipos de interface, tipos de delegado e outras pessoas. Você pode definir seus próprios tipos de objeto, assim como em qualquer outra linguagem .NET.

Além disso, F# código pode definir aliases, que são nomeados *abreviações de tipo*, que são nomes alternativos para tipos. Você pode usar as abreviações de tipo quando o tipo pode mudar no futuro e você quiser evitar alterar o código que depende do tipo. Ou, você pode usar uma abreviação de tipo como um nome amigável para um tipo que pode tornar o código mais fácil de ler e entender.

F#fornece tipos de coleção úteis que são projetados com programação funcional em mente. Usando esses tipos de coleção ajuda você a escrever código que está mais funcionando no estilo. Para obter mais informações, consulte [ F# tipos de coleção](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Sintaxe para tipos
No F# código, você geralmente precisa gravar os nomes de tipos. Cada tipo tem uma forma sintática, e você usar esses formulários sintáticos em anotações de tipo, declarações de método abstrato, declarações de delegado, assinaturas e outras construções. Sempre que você declare uma nova construção de programa no interpretador, o interpretador imprime o nome da construção e a sintaxe para seu tipo. Essa sintaxe pode ser apenas um identificador para um tipo definido pelo usuário ou um identificador interno tal como para `int` ou `string`, mas para tipos mais complexos, a sintaxe é mais complexa.

A tabela a seguir mostra os aspectos da sintaxe de tipo F# tipos.

|Tipo|Sintaxe de tipo|Exemplos|
|----|-----------|--------|
|tipo primitivo|*type-name*|`int`<br /><br />`float`<br /><br />`string`|
|tipo de agregação (classe, estrutura, união, registro, enum e assim por diante)|*type-name*|`System.DateTime`<br /><br />`Color`|
|abreviação de tipo|*type-abbreviation-name*|`bigint`|
|tipo totalmente qualificado|*namespaces.type-name*<br /><br />ou<br /><br />*modules.type-name*<br /><br />ou<br /><br />*namespaces.modules.type-name*|`System.IO.StreamWriter`|
|array|*nome do tipo*[] ou<br /><br />*type-name* array|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|matriz bidimensional|*type-name*[,]|`int[,]`<br /><br />`float[,]`|
|matriz tridimensional|*type-name*[,,]|`float[,,]`|
|tupla|*tipo Nome1* &#42; *name2 do tipo* ...|Por exemplo, `(1,'b',3)` tem tipo `int * char * int`|
|tipo genérico|*type-parameter* *generic-type-name*<br /><br />ou<br /><br />*generic-type-name*&lt;*type-parameter-list*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|(um tipo genérico que tem um argumento de tipo específico fornecido) do tipo construído|*type-argument* *generic-type-name*<br /><br />ou<br /><br />*generic-type-name*&lt;*type-argument-list*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|tipo de função que tem um único parâmetro|*parameter-type1* -&gt; *return-type*|Uma função que usa um `int` e retorna um `string` tem tipo `int -> string`|
|tipo de função que tem vários parâmetros|*parâmetro type1*  - &gt; *parâmetro type2*  - &gt; ... -&gt; *tipo de retorno*|Uma função que usa um `int` e uma `float` e retorna um `string` tem tipo `int -> float -> string`|
|função de ordem superior como um parâmetro|(*function-type*)|`List.map` tem o tipo `('a -> 'b) -> 'a list -> 'b list`|
|delegado|Delegar de *tipo de função*|`delegate of unit -> int`|
|tipo flexível|#*type-name*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Tópicos relacionados

|Tópico|Descrição|
|-----|-----------|
|[Tipos Primitivos](primitive-types.md)|Descreve os tipos simples internos como tipos integrais, o tipo booleano e tipos de caracteres.|
|[Tipo Unit](unit-type.md)|Descreve o `unit` tipo, um tipo que tem um valor e que é indicado por (); equivalente à `void` em C# e `Nothing` no Visual Basic.|
|[Tuplas](tuples.md)|Descreve o tipo de tupla, um tipo que consiste em valores associados de qualquer tipo agrupados em pares, triplos, quadruples e assim por diante.|
|[Opções](options.md)|Descreve o tipo de opção, um tipo que pode ter um valor ou estar vazio.|
|[Listas](lists.md)|Descreve as listas, que são série imutável, ordenada, de elementos todos do mesmo tipo.|
|[Matrizes](arrays.md)|Descreve matrizes, que são conjuntos ordenados de mutáveis elementos do mesmo tipo que ocupam um bloco contíguo de memória e são de tamanho fixo.|
|[Sequências](sequences.md)|Descreve o tipo de sequência, que representa uma série de lógica de valores; os valores individuais são computados somente quando necessário.|
|[Registros](records.md)|Descreve o tipo de registro, uma pequena agregação de valores nomeados.|
|[Uniões Discriminadas](discriminated-unions.md)|Descreve o tipo de união discriminado, um tipo cujos valores podem ser qualquer um de um conjunto de tipos possíveis.|
|[Funções](functions/index.md)|Descreve os valores de função.|
|[Classes](classes.md)|Descreve o tipo de classe, um tipo de objeto que corresponde a um tipo de referência do .NET. Tipos de classe podem conter membros, propriedades, interfaces implementadas e um tipo base.|
|[Estruturas](structures.md)|Descreve o `struct` tipo, um tipo de objeto que corresponde a um tipo de valor do .NET. O `struct` tipo normalmente representa uma agregação pequena de dados.|
|[Interfaces](interfaces.md)|Descreve os tipos de interface, que são tipos que representam um conjunto de membros que fornecer determinadas funcionalidades, mas que não contêm dados. Um tipo de interface deve ser implementado por um tipo de objeto para ser útil.|
|[Delegados](delegates.md)|Descreve o tipo de delegado, que representa uma função como um objeto.|
|[Enumerações](enumerations.md)|Descreve os tipos de enumeração cujos valores pertencem a um conjunto de valores nomeados.|
|[Atributos](attributes.md)|Descreve os atributos que são usados para especificar os metadados de outro tipo.|
|[Tipos de Exceção](exception-handling/exception-types.md)|Descreve exceções, que especificam as informações de erro.|
