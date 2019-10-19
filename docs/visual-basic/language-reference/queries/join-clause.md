---
title: Cláusula Join (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: b5211d0ed3f618013dc9fe764a6d7b2db8177c26
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582288"
---
# <a name="join-clause-visual-basic"></a>Cláusula Join (Visual Basic)

Combina duas coleções em uma única coleção. A operação de junção é baseada em chaves correspondentes e usa o operador de `Equals`.

## <a name="syntax"></a>Sintaxe

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Partes

`element` Necessário. A variável de controle para a coleção que está sendo unida.

`collection`  
Necessário. A coleção a ser combinada com a coleção identificada no lado esquerdo do operador de `Join`. Uma cláusula `Join` pode ser aninhada em outra cláusula `Join` ou em uma cláusula `Group Join`.

`joinClause`  
Opcional. Uma ou mais cláusulas de `Join` adicionais para refinar ainda mais a consulta.

`groupJoinClause`  
Opcional. Uma ou mais cláusulas de `Group Join` adicionais para refinar ainda mais a consulta.

`key1` `Equals` `key2`  
Necessário. Identifica as chaves para as coleções que estão sendo Unidas. Você deve usar o operador de `Equals` para comparar as chaves das coleções que estão sendo Unidas. Você pode combinar condições de junção usando o operador de `And` para identificar várias chaves. `key1` deve ser da coleção no lado esquerdo do operador de `Join`. `key2` deve ser da coleção no lado direito do operador de `Join`.

As chaves usadas na condição de junção podem ser expressões que incluem mais de um item da coleção. No entanto, cada expressão de chave pode conter apenas itens de sua respectiva coleção.

## <a name="remarks"></a>Comentários

A cláusula `Join` combina duas coleções com base nos valores de chave correspondentes das coleções que estão sendo Unidas. A coleção resultante pode conter qualquer combinação de valores da coleção identificada no lado esquerdo do operador de `Join` e da coleção identificada na cláusula `Join`. A consulta retornará apenas resultados para os quais a condição especificada pelo operador de `Equals` é atendida. Isso é equivalente a um `INNER JOIN` no SQL.

Você pode usar várias cláusulas `Join` em uma consulta para unir duas ou mais coleções em uma única coleção.

Você pode executar uma junção implícita para combinar coleções sem a cláusula `Join`. Para fazer isso, inclua várias cláusulas `In` na cláusula `From` e especifique uma cláusula `Where` que identifique as chaves que você deseja usar para a junção.

Você pode usar a cláusula `Group Join` para combinar coleções em uma única coleção hierárquica. Isso é como uma `LEFT OUTER JOIN` no SQL.

## <a name="example"></a>Exemplo

O exemplo de código a seguir executa uma junção implícita para combinar uma lista de clientes com seus pedidos.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Exemplo

O exemplo de código a seguir une duas coleções usando a cláusula `Join`.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Este exemplo produzirá uma saída semelhante à seguinte:

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Exemplo

O exemplo de código a seguir une duas coleções usando a cláusula `Join` com duas colunas de chave.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

O exemplo produzirá uma saída semelhante à seguinte:

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
