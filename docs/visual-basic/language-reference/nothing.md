---
title: Nada (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 12c88db49dc7723fc269195e7d174bfa822c64d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963756"
---
# <a name="nothing-visual-basic"></a>Nada (Visual Basic)
Representa o valor padrão de qualquer tipo de dados. Para tipos de referência, o valor padrão é `null` a referência. Para tipos de valor, o valor padrão depende se o tipo de valor é anulável.  
  
> [!NOTE]
> Para tipos de valores não anuláveis `Nothing` , em Visual Basic difere `null` de C#em. Em Visual Basic, se você definir uma variável de um tipo de valor não anulável como `Nothing`, a variável será definida como o valor padrão para seu tipo declarado. No C#, se você atribuir uma variável de um tipo de valor não anulável a `null`, ocorrerá um erro em tempo de compilação.  
  
## <a name="remarks"></a>Comentários  
 `Nothing`representa o valor padrão de um tipo de dados. O valor padrão depende se a variável é de um tipo de valor ou de um tipo de referência.  
  
 Uma variável de um *tipo Value* contém diretamente seu valor. Os tipos de valor incluem todos os tipos `Boolean`de `Char`dados `Date`numéricos,,,, todas as estruturas e todas as enumerações. Uma variável de um *tipo de referência* armazena uma referência a uma instância do objeto na memória. Os tipos de referência incluem classes, matrizes, delegados e cadeias de caracteres. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Se uma variável for de um tipo Value, o comportamento de `Nothing` dependerá se a variável é de um tipo de dados anulável. Para representar um tipo de valor anulável, adicione `?` um modificador ao nome do tipo. A atribuição `Nothing` a uma variável anulável define o valor como `null`. Para obter mais informações e exemplos, consulte [tipos de valor anulável](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Se uma variável for de um tipo de valor que não permite valor nulo, `Nothing` a atribuição a ela a definirá como o valor padrão para seu tipo declarado. Se esse tipo contiver Membros variáveis, todos eles serão definidos como seus valores padrão. O exemplo a seguir ilustra isso para tipos escalares.  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 Se uma variável for de um tipo de referência, a atribuição `Nothing` à variável a definirá como uma `null` referência do tipo da variável. Uma variável que é definida como uma `null` referência não está associada a nenhum objeto. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 Ao verificar se uma variável de referência (ou tipo de valor Anulável `null`) é, não `= Nothing` use `<> Nothing`ou. Sempre use `Is Nothing` ou `IsNot Nothing`.  
  
 Para cadeias de caracteres em Visual Basic, a `Nothing`cadeia vazia é igual a. Portanto, `"" = Nothing` é verdadeiro.  
  
 O exemplo a seguir mostra as comparações `Is` que `IsNot` usam os operadores e.  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 Se você declarar uma variável sem usar uma `As` cláusula e defini-la `Nothing`como, a variável terá um tipo `Object`de. Um exemplo disso é `Dim something = Nothing`. Um erro de tempo de compilação ocorre nesse caso quando `Option Strict` o está ativado `Option Infer` e é desativado.  
  
 Quando você atribui `Nothing` a uma variável de objeto, ele não faz mais referência a nenhuma instância de objeto. Se a variável tiver referido anteriormente uma instância, defini-la como `Nothing` não terminará a instância em si. A instância é encerrada e os recursos de memória e sistema associados a ela são liberados, somente após o GC (coletor de lixo) detectar que não há nenhuma referência ativa restante.  
  
 `Nothing`difere do <xref:System.DBNull> objeto, que representa uma variante não inicializada ou uma coluna de banco de dados inexistente.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)
- [Tempo de vida do objeto: Como os objetos são criados e destruídos](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Tempo de vida em Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Operador Is](../../visual-basic/language-reference/operators/is-operator.md)
- [Operador IsNot](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Tipos de Valor Anulável](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
