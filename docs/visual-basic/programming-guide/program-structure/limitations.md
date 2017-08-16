---
title: "Limitações do Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
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
ms.openlocfilehash: d556b045b4ebae6ba24c0571a6cb7e5337c6a8f2
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-limitations"></a>Limitações do Visual Basic
Versões anteriores do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] imposta limites no código, como o comprimento de nomes de variável, o número de variáveis é permitida em módulos e o tamanho do módulo. Em [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], essas restrições foi abrandadas, oferecendo maior liberdade escrever e organizar seu código.  
  
 Limites físicos são dependentes mais memória de tempo de execução que nas considerações de tempo de compilação. Se você usa prudentes práticas de programação e divide aplicativos grandes em várias classes e módulos, há pouca probabilidade de encontrar interno [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitação.  
  
 A seguir estão algumas limitações que podem ser encontrados em casos extremos:  
  
-   **Comprimento do nome.** Há um número máximo de caracteres para o nome de cada elemento de programação declarado. Esse máximo aplica-se a uma cadeia de caracteres de qualificação inteira se o nome do elemento é qualificado. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Comprimento da linha.** Há no máximo 65535 caracteres em uma linha física do código-fonte. A linha de código fonte lógica pode ser maior se você usar caracteres de continuação de linha. Consulte [como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Dimensões de matriz.** Há um número máximo de dimensões, que você pode declarar uma matriz. Isso limita quantos índices, você pode usar para especificar um elemento de matriz. Consulte [matriz dimensões no Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Comprimento da cadeia de caracteres.** Há um número máximo de caracteres Unicode que você pode armazenar em uma única cadeia de caracteres. Consulte [tipo de dados de cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Comprimento da cadeia de caracteres de ambiente.** Há um máximo de 32768 caracteres para qualquer ambiente de cadeia de caracteres usada como um argumento de linha de comando. Esta é uma limitação em todas as plataformas.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
