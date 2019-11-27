---
title: Instrução Mid
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
ms.openlocfilehash: eeef4c13743b75a3d5e61ac46afb94d9ea105b7a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348034"
---
# <a name="mid-statement"></a>Instrução Mid
Substitui um número especificado de caracteres em uma variável de `String` com caracteres de outra cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Partes  
 `Target`  
 Necessária. Nome da variável de `String` a ser modificada.  
  
 `Start`  
 Necessária. Expressão `Integer`. Posição do caractere no `Target` onde começa a substituição do texto. `Start` usa um índice baseado em um.  
  
 `Length`  
 Opcional. Expressão `Integer`. Número de caracteres a serem substituídos. Se for omitido, todos os `String` serão usados.  
  
 `StringExpression`  
 Necessária. `String` expressão que substitui parte de `Target`.  
  
## <a name="exceptions"></a>Exceções  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` <= 0 ou `Length` < 0.|  
  
## <a name="remarks"></a>Comentários  
 O número de caracteres substituídos é sempre menor ou igual ao número de caracteres em `Target`.  
  
 Visual Basic tem uma função <xref:Microsoft.VisualBasic.Strings.Mid%2A> e uma instrução `Mid`. Esses elementos operam em um número especificado de caracteres em uma cadeia de caracteres, mas a função `Mid` retorna os caracteres enquanto a instrução `Mid` substitui os caracteres. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> A instrução `MidB` de versões anteriores do Visual Basic substitui uma Subcadeia em bytes, em vez de caracteres. Ele é usado principalmente para converter cadeias de caracteres em aplicativos DBCS. Todas as cadeias de caracteres Visual Basic estão em Unicode e não há mais suporte para `MidB`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a instrução `Mid` para substituir um número especificado de caracteres em uma variável String por caracteres de outra cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Módulo:** `Strings`  
  
 **Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Cadeias de Caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Introdução às cadeias de caracteres no Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
