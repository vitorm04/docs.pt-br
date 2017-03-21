---
title: Tipo de dados UShort (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ushort
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- literal type characters, US
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- integers, types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: 16
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
ms.openlocfilehash: 4f0974bc63ad92799fb1c79c69086cddd52ffb35
ms.lasthandoff: 03/13/2017

---
# <a name="ushort-data-type-visual-basic"></a>Tipo de dados UShort (Visual Basic)
Armazena inteiros sem sinal 16 bits (2 bytes) cujo valor varia de 0 a 65.535.  
  
## <a name="remarks"></a>Comentários  
 Use o `UShort` tipo de dados para armazenar dados binários muito grandes para `Byte`.  
  
 O valor padrão de `UShort` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** Porque `UShort` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `UShort`, Visual Basic converte a expressão para `Integer` primeiro.  
  
-   **Compatibilidade com CLS.** O `UShort` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Ampliação.** The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`. Isso significa que você pode converter `UShort` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `US` a um literal força ao `UShort` tipo de dados. `UShort`não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.UInt16?displayProperty=fullName>estrutura.</xref:System.UInt16?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UInt16></xref:System.UInt16>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
