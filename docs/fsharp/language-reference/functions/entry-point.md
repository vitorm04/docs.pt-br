---
title: Ponto de entrada
description: Saiba como definir o ponto de entrada para um F# programa que é compilado como um arquivo executável, onde a execução é iniciada formalmente.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630525"
---
# <a name="entry-point"></a>Ponto de entrada

Este tópico descreve o método que você usa para definir o ponto de entrada para F# um programa.

## <a name="syntax"></a>Sintaxe

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *Let-function-Binding* é a definição de uma função em uma `let` associação.

O ponto de entrada para um programa compilado como um arquivo executável é onde a execução é iniciada formalmente. Você especifica o ponto de entrada para F# um aplicativo aplicando `EntryPoint` o atributo à função do `main` programa. Essa função (criada usando uma `let` associação) deve ser a última função no último arquivo compilado. O último arquivo compilado é o último arquivo no projeto ou o último arquivo que é passado para a linha de comando.

A função de ponto de entrada `string array -> int`tem o tipo. Os argumentos fornecidos na linha de comando são passados para a `main` função na matriz de cadeias de caracteres. O primeiro elemento da matriz é o primeiro argumento; o nome do arquivo executável não está incluído na matriz, pois está em algumas outras linguagens. O valor de retorno é usado como o código de saída para o processo. Zero geralmente indica êxito; valores diferentes de zero indicam um erro. Não há nenhuma convenção para o significado específico de códigos de retorno diferentes de zero; os significados dos códigos de retorno são específicos do aplicativo.

O exemplo a seguir ilustra uma `main` função simples.

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

Quando esse código é executado com a linha `EntryPoint.exe 1 2 3`de comando, a saída é a seguinte:

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Ponto de entrada implícito

Quando um programa não tem um atributo **EntryPoint** que indica explicitamente o ponto de entrada, as associações de nível superior no último arquivo a ser compilado são usadas como o ponto de entrada.

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
- [Associações let](let-bindings.md)
