---
title: Opcional (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
dev_langs:
- VB
helpviewer_keywords:
- Optional keyword, contexts
- Optional keyword
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: 14
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
ms.openlocfilehash: c00f3f386159fa60da9c60cf7857fd62fa3e9b45
ms.lasthandoff: 03/13/2017

---
# <a name="optional-visual-basic"></a>Opcional (Visual Basic)
Especifica que um argumento de procedimento pode ser omitido quando o procedimento é chamado.  
  
## <a name="remarks"></a>Comentários  
 Para cada parâmetro opcional, você deve especificar uma expressão constante como o valor padrão desse parâmetro. Se a expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), o valor padrão do tipo de dados valor é usado como o valor padrão do parâmetro.  
  
 Se a lista de parâmetros contém um parâmetro opcional, cada parâmetro seguinte também deve ser opcional.  
  
 O `Optional` modificador pode ser usado nesses contextos:  
  
-   [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  Ao chamar um procedimento com ou sem parâmetros opcionais, você pode passar argumentos por posição ou por nome. Para obter mais informações, consulte [passando argumentos por posição e nome](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Você também pode definir um procedimento com parâmetros opcionais usando a sobrecarga. Se você tiver um parâmetro opcional, você pode definir duas versões sobrecarregadas do procedimento, uma que aceita o parâmetro e um que não. Para obter mais informações, consulte [sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um procedimento com um parâmetro opcional.  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como chamar um procedimento com os argumentos passados por posição e argumentos passados pelo nome. O procedimento tem dois parâmetros opcionais.  
  
 [!code-vb[VbVbalrKeywords&#21;](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
