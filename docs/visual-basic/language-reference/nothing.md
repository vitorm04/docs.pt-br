---
title: Nada (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Nothing
- vb.Nothing
dev_langs:
- VB
helpviewer_keywords:
- Nothing keyword
- Nothing keyword, syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: 31
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4c88f7e87a39158399510af382817c58cffa97aa
ms.lasthandoff: 03/13/2017

---
# <a name="nothing-visual-basic"></a>Nada (Visual Basic)
Representa o valor padrão de qualquer tipo de dados. Para tipos de referência, o valor padrão é o `null` referência. Para tipos de valor, o valor padrão depende se o tipo de valor é anulável.  
  
> [!NOTE]
>  Para tipos de valor não nulo, `Nothing` no Visual Basic difere `null` em c#. No Visual Basic, se você definir uma variável de um tipo de valor não nulo para `Nothing`, a variável é definida como o valor padrão para seu tipo declarado. No c#, se você atribuir uma variável de um tipo de valor não nulo para `null`, ocorrerá um erro em tempo de compilação.  
  
## <a name="remarks"></a>Comentários  
 `Nothing`representa o valor padrão de um tipo de dados. O valor padrão depende se a variável é de um tipo de valor ou de um tipo de referência.  
  
 Uma variável de um *tipo de valor* contém diretamente seu valor. Tipos de valor incluem todos os tipos de dados numéricos, `Boolean`, `Char`, `Date`, todas as estruturas e todas as enumerações. Uma variável de um *tipo de referência* armazena uma referência a uma instância do objeto na memória. Tipos de referência incluem classes, matrizes, delegados e cadeias de caracteres. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Se uma variável é de um valor de tipo, o comportamento de `Nothing` depende se a variável for de um tipo de dados anulável. Para representar um tipo de valor anulável, adicione um `?` modificador para o nome do tipo. Atribuindo `Nothing` a uma variável anulável define o valor como `null`. Para obter mais informações e exemplos, consulte [tipos de valor anulável](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Se for uma variável de um tipo de valor não é anulável, atribuindo `Nothing` para ele define como o valor padrão para seu tipo declarado. Se o tipo contém membros variáveis, eles são definidos para seus valores padrão. O exemplo a seguir ilustra isso para tipos escalares.  
  
 [!code-vb[VbVbalrKeywords&#7;](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Se for uma variável do tipo de referência, atribuindo `Nothing` à variável define como um `null` referência do tipo da variável. Uma variável que é definida como um `null` referência não está associada a qualquer objeto. O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbalrKeywords n º&8;](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Ao verificar se uma referência (ou o tipo de valor anulável) é variável `null`, não use `= Nothing` ou `<> Nothing`. Sempre use `Is Nothing` ou `IsNot Nothing`.  
  
 Cadeias de caracteres no Visual Basic, a cadeia de caracteres vazia é igual a `Nothing`. Portanto, `"" = Nothing` é verdadeiro.  
  
 O exemplo a seguir mostra as comparações que usam o `Is` e `IsNot` operadores.  
  
 [!code-vb[VbVbalrKeywords n º&9;](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Se você declarar uma variável sem usar um `As` cláusula e defina-o como `Nothing`, a variável tem um tipo de `Object`. Um exemplo disso é `Dim something = Nothing`. Um erro de tempo de compilação nesse caso ocorre quando `Option Strict` está em e `Option Infer` está desativado.  
  
 Quando você atribui `Nothing` a uma variável de objeto, ele não se refere a qualquer instância do objeto. Se a variável tivesse anteriormente referenciado uma instância, defini-la como `Nothing` finaliza a instância em si. A instância é finalizada, e os recursos de memória e do sistema associados a ele são liberados, somente após o coletor de lixo (GC) detectar que não há referências ativas restantes.  
  
 `Nothing`difere de <xref:System.DBNull>objeto que representa um variant não inicializado ou uma coluna de banco de dados que não existe.</xref:System.DBNull>  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)   
 [Vida útil do objeto: Como os objetos são criados e destruídos](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Tempo de vida no Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Operador is](../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Tipos de Valor Anulável](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
