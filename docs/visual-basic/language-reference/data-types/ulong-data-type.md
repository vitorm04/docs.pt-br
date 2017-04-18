---
title: Tipo de dados ULong (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ulong
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- integers, types
- data types [Visual Basic], integral
- literal type characters, UL
- ULong data type
- UL literal type characters
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
caps.latest.revision: 21
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
ms.openlocfilehash: 89dbc73cb7295a9694c8fde33c1763ec9309759c
ms.lasthandoff: 03/13/2017

---
# <a name="ulong-data-type-visual-basic"></a>Tipo de dados ULong (Visual Basic)
Contém 64 bits (8 bytes) números inteiros sem sinal que variam em valor entre 0 e 18.446.744.073.709.551.615 (mais do que 1,84 vezes 10 ^ 19).  
  
## <a name="remarks"></a>Comentários  
 Use o `ULong` tipo de dados para armazenar dados binários muito grandes para `UInteger`, ou valores inteiros sem sinal de maior possível.  
  
 O valor padrão de `ULong` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** Porque `ULong` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `ULong`, Visual Basic converte a expressão para `Decimal` primeiro.  
  
-   **Compatibilidade com CLS.** O `ULong` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos como `ulong` pode ter uma largura de dados diferente (32 bits) em outros ambientes. Se você estiver passando um argumento de 32 bits para tal um componente, declare-o como `UInteger` em vez de `ULong` no seu código Visual Basic gerenciado.  
  
     Além disso, automação não dá suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000. Você não pode passar um Visual Basic `ULong` argumento para um componente de automação dessas plataformas.  
  
-   **Ampliação.** O `ULong` tipo de dados amplia a `Decimal`, `Single`, e `Double`. Isso significa que você pode converter `ULong` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `UL` a um literal força ao `ULong` tipo de dados. `ULong`não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.UInt64?displayProperty=fullName>estrutura.</xref:System.UInt64?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UInt64></xref:System.UInt64>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
