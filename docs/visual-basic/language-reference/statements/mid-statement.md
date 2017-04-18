---
title: "Mid instrução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e385d6838daa16d45903c6b270fc47ad88797845
ms.lasthandoff: 03/13/2017

---
# <a name="mid-statement"></a>Instrução Mid
Substitui um número especificado de caracteres em um `String` variável com caracteres de outra cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Partes  
 `Target`  
 Necessário. Nome da `String` variável para modificar.  
  
 `Start`  
 Necessário. Expressão `Integer`. Posição de caractere `Target` onde a substituição do texto começa. `Start`usa um índice baseado em um.  
  
 `Length`  
 Opcional. Expressão `Integer`. Número de caracteres a substituir. Se omitido, todos `String` é usado.  
  
 `StringExpression`  
 Necessário. `String`expressão que substitui parte de `Target`.  
  
## <a name="exceptions"></a>Exceções  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException></xref:System.ArgumentException>|`Start` <= 0 ou `Length` < 0.|  
  
## <a name="remarks"></a>Comentários  
 O número de caracteres substituído é sempre menor ou igual ao número de caracteres em `Target`.  
  
 O Visual Basic possui uma <xref:Microsoft.VisualBasic.Strings.Mid%2A>função e um `Mid` instrução.</xref:Microsoft.VisualBasic.Strings.Mid%2A> Os dois elementos operam em um número especificado de caracteres em uma cadeia de caracteres, mas o `Mid` função retorna os caracteres enquanto o `Mid` instrução substitui os caracteres. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</xref:Microsoft.VisualBasic.Strings.Mid%2A>  
  
> [!NOTE]
>  O `MidB` instrução de versões anteriores do Visual Basic substitui uma substring em bytes, em vez de caracteres. Ele é usado principalmente para converter cadeias de caracteres de dois bytes (DBCS) conjunto de aplicativos. Todas as cadeias de caracteres do Visual Basic estão em Unicode, e `MidB` não é mais suportado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Mid` instrução para substituir um número especificado de caracteres em uma variável de cadeia de caracteres com caracteres de outra cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings n º&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Módulo:**`Strings`  
  
 **Assembly:**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 [Cadeias de caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Introdução a cadeias de caracteres no Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
