---
title: Instrução mid (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 47034b3699f4dfee67d36e72d4b22898d469c900
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700283"
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
 Necessário. Expressão `Integer`. Posição de caractere `Target` onde a substituição de texto começa. `Start` usa um índice baseado em um.  
  
 `Length`  
 Opcional. Expressão `Integer`. Número de caracteres a substituir. Se omitido, todos os `String` é usado.  
  
 `StringExpression`  
 Necessário. `String` expressão que substitui parte de `Target`.  
  
## <a name="exceptions"></a>Exceções  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` <= 0 ou `Length` < 0.|  
  
## <a name="remarks"></a>Comentários  
 O número de caracteres serão substituídos sempre é menor ou igual ao número de caracteres em `Target`.  
  
 O Visual Basic possui um <xref:Microsoft.VisualBasic.Strings.Mid%2A> função e um `Mid` instrução. Os dois elementos operam em um número especificado de caracteres em uma cadeia de caracteres, mas o `Mid` função retorna os caracteres enquanto o `Mid` instrução substitui os caracteres. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
>  O `MidB` declaração de versões anteriores do Visual Basic substitui uma subcadeia de caracteres em bytes, em vez de caracteres. Ele é usado principalmente para converter cadeias de caracteres em caracteres de byte duplo (DBCS) conjunto de aplicativos. Todas as cadeias de caracteres do Visual Basic estão em Unicode, e `MidB` não é mais suportada.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Mid` instrução para substituir um número especificado de caracteres em uma variável de cadeia de caracteres com caracteres de outra cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Módulo:** `Strings`  
  
 **Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Cadeias de Caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Introdução às cadeias de caracteres no Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
