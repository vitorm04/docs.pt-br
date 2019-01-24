---
title: '#Diretiva const (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 7e855f76a0fa8e6c06fd557a944c518641415f09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710593"
---
# <a name="const-directive"></a>Diretiva #Const
Define constantes condicionais de compilador do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Partes  
 `constname`  
 Necessário. Nome da constante que está sendo definido.  
  
 `expression`  
 Necessário. Literal, outra constante condicional de compilador ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos exceto `Is`.  
  
## <a name="remarks"></a>Comentários  
 Constantes condicionais de compilador são sempre privadas ao arquivo em que aparecem. Não é possível criar constantes de compilador públicas usando o `#Const` diretiva; você pode criá-los apenas na interface do usuário ou com o `/define` opção de compilador.  
  
 Você pode usar apenas constantes condicionais de compilador e literais em `expression`. Usar uma condição padrão definida com `Const` causa um erro. Por outro lado, você pode usar constantes definidas com o `#Const` palavra-chave para compilação condicional. Constantes também podem ser indefinidas, caso em que eles têm um valor de `Nothing`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `#Const` diretiva.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
