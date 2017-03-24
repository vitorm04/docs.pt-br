---
title: Tipo de dados UInteger | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.uinteger
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- UInteger data type
- literal type characters, UI
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- integers, types
- UI literal type characters
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: 19
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
ms.openlocfilehash: efbcbe1926c2229f6115dc4f355722cdca447b3e
ms.lasthandoff: 03/13/2017

---
# <a name="uinteger-data-type"></a>Tipo de dados UInteger
Armazena inteiros sem sinal 32 bits (4 bytes) variando de 0 a 4.294.967.295.  
  
## <a name="remarks"></a>Comentários  
 O `UInteger` tipo de dados fornece o maior valor sem sinal à largura de dados mais eficiente.  
  
 O valor padrão de `UInteger` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
 O `UInteger` e `Integer` tipos de dados fornecem um desempenho ideal em um processador de 32 bits, porque os tipos de inteiro menores (`UShort`, `Short`, `Byte`, e `SByte`), mesmo que eles usam menos bits, levará mais tempo para carregar, armazenar e buscar.  
  
-   **Números negativos.** Porque `UInteger` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `UInteger`, Visual Basic converte a expressão para `Long` primeiro.  
  
-   **Compatibilidade com CLS.** O `UInteger` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos como `uint` pode ter uma largura de dados diferente (16 bits) em outros ambientes. Se você estiver passando um argumento de 16 bits para tal um componente, declare-o como `UShort` em vez de `UInteger` no seu código Visual Basic gerenciado.  
  
-   **Ampliação.** The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`. Isso significa que você pode converter `UInteger` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `UI` a um literal força ao `UInteger` tipo de dados. `UInteger`não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.UInt32?displayProperty=fullName>estrutura.</xref:System.UInt32?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UInt32></xref:System.UInt32>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
