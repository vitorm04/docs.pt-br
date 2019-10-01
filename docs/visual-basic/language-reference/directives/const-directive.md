---
title: '#Diretiva Const (Visual Basic)'
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
ms.openlocfilehash: 9b8d2da2158a8244b4533eb6ef49049949417216
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696849"
---
# <a name="const-directive"></a>Diretiva #Const
Define constantes de compilador condicional para Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Partes  
 `constname`  
 Necessário. Nome da constante que está sendo definida.  
  
 `expression`  
 Necessário. Literal, outra constante de compilador condicional ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos, exceto `Is`.  
  
## <a name="remarks"></a>Comentários  
 Constantes de compilador condicional são sempre particulares para o arquivo no qual aparecem. Você não pode criar constantes de compilador público usando a diretiva `#Const`; Você pode criá-los somente na interface do usuário ou com a opção de compilador `/define`.  
  
 Você pode usar apenas constantes de compilador condicionais e literais no `expression`. O uso de uma constante padrão definida com `Const` causa um erro. Por outro lado, você pode usar constantes definidas com a palavra-chave `#Const` somente para compilação condicional. As constantes também podem ser indefinidas; nesse caso, elas têm um valor de `Nothing`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a diretiva `#Const`.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
