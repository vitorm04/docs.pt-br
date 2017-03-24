---
title: Tipo de dados byte (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Byte
dev_langs:
- VB
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
caps.latest.revision: 18
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
ms.openlocfilehash: b8d4ff20e9d00d59a2744c626726a78f080599be
ms.lasthandoff: 03/13/2017

---
# <a name="byte-data-type-visual-basic"></a>Tipo de dados Byte (Visual Basic)
Armazena inteiros de (1 byte) de 8 bits sem sinal que variam em valor de 0 a 255.  
  
## <a name="remarks"></a>Comentários  
 Use o `Byte` tipo de dados para armazenar dados binários.  
  
 O valor padrão de `Byte` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** Porque `Byte` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `Byte`, Visual Basic converte a expressão para `Short` primeiro.  
  
-   **Conversões de formato.** Quando o Visual Basic lê ou grava arquivos, ou quando ele chama DLLs, métodos e propriedades, pode converter automaticamente entre os formatos de dados. Dados binários armazenados em `Byte` matrizes e variáveis são preservados durante essas conversões de formato. Você não deve usar um `String` variável para dados binários, porque seu conteúdo pode ser corrompido durante a conversão entre ANSI e Unicode formatos.  
  
-   **Ampliação.** The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`. Isso significa que você pode converter `Byte` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** `Byte`não possui caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Byte?displayProperty=fullName>estrutura.</xref:System.Byte?displayProperty=fullName>  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `b` é um `Byte` variável. As instruções demonstram o intervalo da variável e a aplicação de operadores bit shift para ele.  
  
 [!code-vb[VbVbalrDataTypes n º&16;](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Byte?displayProperty=fullName></xref:System.Byte?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
