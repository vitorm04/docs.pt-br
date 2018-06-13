---
title: Limitações do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 57378c3aa18a5cc108c10e8654e55803f3cf9052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649923"
---
# <a name="visual-basic-limitations"></a>Limitações do Visual Basic
Versões anteriores do Visual Basic imposta limites no código, como o comprimento dos nomes de variável, o número de coluna não são permitidos em módulos e o tamanho do módulo. No Visual Basic .NET, essas restrições têm foram reduzidas, fornecendo maior liberdade escrever e organizar seu código.  
  
 Limites físicos são dependentes mais memória de tempo de execução que sobre considerações de tempo de compilação. Se você usa prudentes práticas recomendadas de programação e divide aplicativos grandes em várias classes e módulos, há muito pouca chance de encontrar uma limitação interna do Visual Basic.  
  
 A seguir estão algumas limitações que podem ser encontrados em casos extremos:  
  
-   **Comprimento do nome.** Há um número máximo de caracteres para o nome de cada elemento de programação declarado. Esse máximo aplica-se a uma cadeia de caracteres de qualificação inteira se o nome do elemento é qualificado. Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Comprimento da linha.** Há um máximo de 65.535 caracteres em uma linha física do código-fonte. A linha de código fonte lógica pode ser maior se você usar caracteres de continuação de linha. Consulte [como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Dimensões de matriz.** Há um número máximo de dimensões, que você pode declarar uma matriz. Isso limita quantos índices, você pode usar para especificar um elemento de matriz. Consulte [matriz dimensões no Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Comprimento da cadeia de caracteres.** Há um número máximo de caracteres Unicode que você pode armazenar em uma única cadeia de caracteres. Consulte [tipo de dados de cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Comprimento da cadeia de caracteres de ambiente.** Há um máximo de 32768 caracteres para qualquer cadeia de caracteres de ambiente usado como um argumento de linha de comando. Essa é uma limitação em todas as plataformas.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
