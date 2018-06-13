---
title: Ponto de entrada (F#)
description: 'Saiba como configurar o ponto de entrada para um programa em F # que é compilado como um arquivo executável, onde formalmente início da execução.'
ms.date: 05/16/2016
ms.openlocfilehash: 3d6cab755dd89f2d3d669a8763aa08660432a0ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563614"
---
# <a name="entry-point"></a>Ponto de entrada

Este tópico descreve o método que você usar para definir o ponto de entrada para um programa em F #.


## <a name="syntax"></a>Sintaxe

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Comentários
Na sintaxe anterior, *permitem a associação de função* é a definição de uma função em um `let` associação.

O ponto de entrada para um programa que é compilado como um arquivo executável é onde formalmente início da execução. Especifique o ponto de entrada para um aplicativo do F #, aplicando o `EntryPoint` de atributo para o programa `main` função. Essa função (criada usando um `let` associação) deve ser a última função no último arquivo compilado. O último arquivo compilado é o último arquivo do projeto ou o último arquivo que é passado para a linha de comando.

A função de ponto de entrada tem tipo `string array -> int`. Os argumentos fornecidos na linha de comando são passados para o `main` função na matriz de cadeias de caracteres. O primeiro elemento da matriz é o primeiro argumento; o nome do arquivo executável não está incluído na matriz, pois ele está em algumas outras linguagens. O valor de retorno é usado como o código de saída para o processo. Zero geralmente indica sucesso. valores diferentes de zero indicam um erro. Não há nenhum convenção do significado específico de códigos de retorno diferente de zero; os significados dos códigos de retorno são específicas do aplicativo.

O exemplo a seguir ilustra um simples `main` função.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

Quando esse código é executado com a linha de comando `EntryPoint.exe 1 2 3`, a saída é da seguinte maneira.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Ponto de entrada implícito
Quando um programa não tem **EntryPoint** atributo que explicitamente indica o ponto de entrada, as associações de nível superior no último arquivo a ser compilado são usados como o ponto de entrada.


## <a name="see-also"></a>Consulte também
[Funções](index.md)

[Associações let](let-bindings.md)
