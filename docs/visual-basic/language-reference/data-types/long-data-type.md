---
title: Tipo de dados Long (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Long
dev_langs:
- VB
helpviewer_keywords:
- identifier type characters, &
- numbers, whole
- whole numbers
- integral data types
- '& identifier type character'
- integer numbers
- literal type characters, L
- numbers, integer
- integers, data types
- L literal type character
- integers, types
- Long keyword
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
caps.latest.revision: 20
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
ms.openlocfilehash: 6419b6df60d3a8145ed7b96f6ca787a62b057ac2
ms.lasthandoff: 03/13/2017

---
# <a name="long-data-type-visual-basic"></a>Tipo de dados Long (Visual Basic)
Armazena inteiros de 64 bits (8 bytes) cujo valor varia de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 (9.2... E + 18).  
  
## <a name="remarks"></a>Comentários  
 Use o `Long` tipo de dados para conter números inteiros que são muito grandes para caber no `Integer` tipo de dados.  
  
 O valor padrão de `Long` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, lembre-se de que `Long` tem uma largura de dados diferente (32 bits) em outros ambientes. Se você estiver passando um argumento de 32 bits para tal um componente, declare-o como `Integer` em vez de `Long` em seu novo código Visual Basic.  
  
     Além disso, automação não dá suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000. Você não pode passar um Visual Basic `Long` argumento para um componente de automação nesses sistemas operacionais.  
  
-   **Ampliação.** O `Long` tipo de dados amplia a `Decimal`, `Single`, ou `Double`. Isso significa que você pode converter `Long` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `L` a um literal o força ao tipo de dados `Long`. Acrescentar o caractere de tipo identificador `&` a qualquer identificador o força ao tipo `Long`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Int64?displayProperty=fullName>estrutura.</xref:System.Int64?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int64></xref:System.Int64>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
