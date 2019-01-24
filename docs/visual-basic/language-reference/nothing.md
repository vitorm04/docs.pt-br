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
ms.openlocfilehash: b4a9acb5a43898ef616bbc6bb97f2f4f96d206b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496943"
---
# <a name="nothing-visual-basic"></a>Nada (Visual Basic)
Representa o valor padrão de qualquer tipo de dados. Para tipos de referência, o valor padrão é o `null` referência. Para tipos de valor, o valor padrão depende se o tipo de valor é anulável.  
  
> [!NOTE]
>  Para tipos de valor não anulável `Nothing` no Visual Basic difere `null` em C#. No Visual Basic, se você definir uma variável de um tipo de valor não anulável para `Nothing`, a variável é definida como o valor padrão para seu tipo declarado. No C#, se você atribuir uma variável de um tipo de valor não anulável para `null`, ocorre um erro de tempo de compilação.  
  
## <a name="remarks"></a>Comentários  
 `Nothing` representa o valor padrão de um tipo de dados. O valor padrão depende se a variável é de um tipo de valor ou de um tipo de referência.  
  
 Uma variável de um *tipo de valor* contém diretamente de seu valor. Tipos de valor incluem todos os tipos de dados numéricos `Boolean`, `Char`, `Date`, todas as estruturas e todas as enumerações. Uma variável de um *tipo de referência* armazena uma referência a uma instância do objeto na memória. Tipos de referência incluem classes, matrizes, delegados e cadeias de caracteres. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Se uma variável é de um valor de tipo, o comportamento de `Nothing` depende se a variável é um tipo de dados que permite valor nulo. Para representar um tipo de valor anulável, adicione um `?` modificador para o nome do tipo. Atribuindo `Nothing` a uma variável que permite valor nula, define o valor como `null`. Para obter mais informações e exemplos, consulte [tipos de valor anuláveis](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Se for uma variável de um tipo de valor que não permite valor nulo, atribuindo `Nothing` para ele define como o valor padrão para seu tipo declarado. Se o tipo contém membros variáveis, eles estão todos definidos para seus valores padrão. O exemplo a seguir ilustra isso para tipos escalares.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Se for uma variável do tipo de referência, atribuindo `Nothing` à variável define-a como um `null` referência do tipo da variável. Uma variável que é definida como um `null` referência não está associada a qualquer objeto. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Ao verificar se uma referência (ou o tipo de valor anulável) variável é `null`, não use `= Nothing` ou `<> Nothing`. Sempre use `Is Nothing` ou `IsNot Nothing`.  
  
 Para cadeias de caracteres no Visual Basic, a cadeia de caracteres vazia é igual a `Nothing`. Portanto, `"" = Nothing` é verdadeiro.  
  
 O exemplo a seguir mostra as comparações que usam o `Is` e `IsNot` operadores.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Se você declarar uma variável sem usar um `As` cláusula e defina-a como `Nothing`, a variável tem um tipo de `Object`. Um exemplo disso é `Dim something = Nothing`. Um erro de tempo de compilação ocorre nesse caso, quando `Option Strict` está em e `Option Infer` está desativado.  
  
 Quando você atribui `Nothing` a uma variável de objeto, ele não se refere a qualquer instância do objeto. Se a variável anteriormente se referiu a uma instância, configurando-a como `Nothing` não encerra a instância em si. A instância será encerrada e os recursos de memória e do sistema associados a ela são liberados somente depois que o coletor de lixo (GC) detecta que há referências ativas restantes.  
  
 `Nothing` difere de <xref:System.DBNull> objeto que representa um variant não inicializado ou uma coluna de banco de dados inexistente.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)
- [Tempo de vida do objeto: Como os objetos são criados e destruídos](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Tempo de vida no Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Operador Is](../../visual-basic/language-reference/operators/is-operator.md)
- [Operador IsNot](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Tipos de Valor Anulável](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
