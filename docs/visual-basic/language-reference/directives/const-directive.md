---
title: '#Diretiva const | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
dev_langs:
- VB
helpviewer_keywords:
- '#Const directive'
- conditional compilation, directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants, Const directive
- constants, declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants, #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 7c363d4972b8b59af5ec7db94bfdd747b6102e20
ms.lasthandoff: 03/13/2017

---
# <a name="const-directive"></a>#Diretiva const
Define constantes condicionais de compilador do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Partes  
 `constname`  
 Necessário. Nome da constante sendo definida.  
  
 `expression`  
 Necessário. Literal, outra constante condicional de compilador ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos exceto `Is`.  
  
## <a name="remarks"></a>Comentários  
 Essas constantes são sempre particulares para o arquivo em que aparecem. Você não pode criar constantes de compilador públicas usando o `#Const` diretriz; você pode criá-los apenas na interface do usuário ou com o `/define` opção de compilador.  
  
 Você pode usar apenas constantes de compilador condicionais e literais em `expression`. Usar uma condição padrão definida com `Const` causa um erro. Por outro lado, você pode usar constantes definidas com o `#Const` palavra-chave para compilação condicional. Constantes também podem ser indefinidas, caso no qual elas possuem um valor de `Nothing`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a `#Const` diretiva.  
  
 [!code-vb[VbVbalrConditionalComp n º&3;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
