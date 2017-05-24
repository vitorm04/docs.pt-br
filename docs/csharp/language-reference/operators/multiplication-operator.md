---
title: "* Operator (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7b25091b422de68391b925b492ca1e4cef720467
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="-operator-c-reference"></a>Operador * (Referência de C#)
O operador de multiplicação (`*`), que calcula o produto dos operandos.  Além disso, o operador de desreferenciamento, que permite a leitura e gravação em um ponteiro.  
  
## <a name="remarks"></a>Comentários  
 Todos os tipos numéricos têm operadores de multiplicação predefinidos.  
  
 O operador `*` também é usado para declarar tipos de ponteiro e para desreferenciar ponteiros. Esse operador pode ser usado somente em contextos não seguros, indicado pelo uso da palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) e exigindo a opção do compilador [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  O operador de desreferenciamento é também conhecido como operador de indireção.  
  
 Tipos definidos pelo usuário podem sobrecarregar o operador binário `*` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Código Não Seguro e Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
