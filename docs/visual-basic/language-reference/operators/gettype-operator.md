---
title: Operador GetType (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetType
dev_langs:
- VB
helpviewer_keywords:
- GetType operator
- GetType keyword
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 17
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
ms.openlocfilehash: 8e7599ee5c80f1bf68c61affc7a7ddc9b8498bb7
ms.lasthandoff: 03/13/2017

---
# <a name="gettype-operator-visual-basic"></a>Operador GetType (Visual Basic)
Retorna um <xref:System.Type>objeto para o tipo especificado.</xref:System.Type> O <xref:System.Type>objeto fornece informações sobre o tipo como suas propriedades, métodos e eventos.</xref:System.Type>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---|---|  
|`typename`|O nome do tipo para o qual você deseja informações.|  
  
## <a name="remarks"></a>Comentários  
 O `GetType` operador retorna o <xref:System.Type>objeto especificado `typename`.</xref:System.Type> Você pode passar o nome de qualquer tipo definido em `typename`. Isso inclui o seguinte:  
  
-   Digite quaisquer dados do Visual Basic, como `Boolean` ou `Date`.  
  
-   Qualquer classe do .NET Framework, estrutura, módulo ou interface, como <xref:System.ArgumentException?displayProperty=fullName>ou <xref:System.Double?displayProperty=fullName>.</xref:System.Double?displayProperty=fullName> </xref:System.ArgumentException?displayProperty=fullName>  
  
-   Qualquer classe, estrutura, módulo ou interface definida por seu aplicativo.  
  
-   Qualquer matriz definida por seu aplicativo.  
  
-   Qualquer delegado definido por seu aplicativo.  
  
-   Qualquer enumeração definida pelo seu aplicativo, o .NET Framework ou Visual Basic.  
  
 Se você deseja obter o objeto do tipo de uma variável de objeto, use o <xref:System.Type.GetType%2A?displayProperty=fullName>método.</xref:System.Type.GetType%2A?displayProperty=fullName>  
  
 O `GetType` operador pode ser útil nas seguintes circunstâncias:  
  
-   Você deve acessar os metadados para um tipo em tempo de execução. O <xref:System.Type>objeto fornece metadados como membros do tipo e informações de implantação.</xref:System.Type> Você precisa disto, por exemplo, para refletir sobre um assembly. Para obter mais informações, consulte <xref:System.Reflection?displayProperty=fullName>.</xref:System.Reflection?displayProperty=fullName>  
  
-   Você deseja comparar duas referências de objeto para ver se elas se referem a instâncias do mesmo tipo. Se Sim, `GetType` retorna referências para o mesmo <xref:System.Type>objeto.</xref:System.Type>  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram o `GetType` operador em uso.  
  
 [!code-vb[VbVbalrOperators&#26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
