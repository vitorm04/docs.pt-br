---
title: "#else (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#else'
dev_langs:
- CSharp
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f531ba57e45466699910d15bd6dff8de6ee7bf2e
ms.lasthandoff: 03/13/2017

---
# <a name="else-c-reference"></a>#else (Referência de C#)
`#else` permite que você crie uma diretiva condicional composta, para que, se não houver nenhuma das expressões na [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) anterior ou nas diretivas [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) (opcionais) para `true`, o compilador avalie todo o código entre `#else` e o `#endif` subsequente.  
  
## <a name="remarks"></a>Comentários  
 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) deve ser a próxima diretiva de pré-processador após `#else`. Consulte [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) para obter um exemplo de como usar `#else`.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
