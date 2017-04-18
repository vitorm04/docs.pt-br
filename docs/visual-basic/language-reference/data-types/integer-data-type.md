---
title: Tipo de dados inteiro (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- enumerated values
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- literal type characters, I
- integers, types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters, %
- I literal type character
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
caps.latest.revision: 22
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
ms.openlocfilehash: b8df2264a335d6a37042b90a421c5d15f6b5b404
ms.lasthandoff: 03/13/2017

---
# <a name="integer-data-type-visual-basic"></a>Tipo de dados inteiro (Visual Basic)
Armazena inteiros de 32 bits (4 bytes) com sinal que variam em valor de -2.147.483.648 a 2.147.483.647.  
  
## <a name="remarks"></a>Comentários  
 O tipo de dados `Integer` proporciona um desempenho ideal em um processador de 32 bits. Os outros tipos integrais são mais lentos para carregar e armazenar na memória.  
  
 O valor padrão de `Integer` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre-se de que `Integer` possui uma largura de dados diferente (16 bits) em outros ambientes. Se você estiver passando um argumento de 16 bits para esse componente, declare-o como `Short` em vez de `Integer` no seu novo código do Visual Basic.  
  
-   **Ampliação.** O tipo de dados `Integer` é ampliado para `Long`, `Decimal`, `Single` ou `Double`. Isso significa que você pode converter `Integer` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `I` a um literal o força ao tipo de dados `Integer`. Acrescentar o caractere de tipo identificador `%` a qualquer identificador o força ao tipo `Integer`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Int32?displayProperty=fullName>estrutura.</xref:System.Int32?displayProperty=fullName>  
  
## <a name="range"></a>Intervalo  
 Se você tentar definir uma variável de um tipo integral para um número fora do intervalo para esse tipo, ocorrerá um erro. Se você tentar defini-lo como uma fração, o número será arredondado para cima ou para baixo para o valor inteiro mais próximo. Se o número for igualmente próximo de dois valores inteiros, o valor será arredondado para o inteiro par mais próximo. Esse comportamento minimiza erros de arredondamento gerados ao arredondar consistentemente um valor de ponto médio em uma única direção. O código a seguir mostra exemplos de arredondamento.  
  
```  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int32?displayProperty=fullName></xref:System.Int32?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Tipo de dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
