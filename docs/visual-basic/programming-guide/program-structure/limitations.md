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
ms.openlocfilehash: 10f67c02d25ec275d1c3e98197d51c25aa250c19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955500"
---
# <a name="visual-basic-limitations"></a>Limitações do Visual Basic
Versões anteriores do Visual Basic aplicadas limites no código, como o comprimento de nomes de variável, o número de coluna não são permitidos em módulos e o tamanho do módulo. No Visual Basic .NET, essas restrições têm foi abrandadas, dando a você maior liberdade de escrever e organizar seu código.  
  
 Limites físicos são dependentes mais na memória do tempo de execução que nas considerações de tempo de compilação. Se você usa práticas de programação prudentes e divide aplicativos grandes em várias classes e módulos, há pouca probabilidade de encontrar uma limitação interna do Visual Basic.  
  
 A seguir estão algumas limitações que podem ocorrer em casos extremos:  
  
- **Comprimento do nome.** Há um número máximo de caracteres para o nome de cada elemento de programação declarado. Esse máximo aplica-se para uma cadeia de caracteres de qualificação inteira se o nome do elemento é qualificado. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
- **Comprimento da linha.** Há um máximo de 65535 caracteres em uma linha física do código-fonte. A linha de código da lógica de código-fonte pode ser maior se você usar caracteres de continuação de linha. Confira [Como Quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
- **Dimensões de matriz.** Há um número máximo de dimensões que você pode declarar uma matriz. Isso limita quantos índices, você pode usar para especificar um elemento de matriz. Ver [dimensões no Visual Basic de matriz](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
- **Comprimento da cadeia de caracteres.** Há um número máximo de caracteres Unicode que você pode armazenar em uma única cadeia de caracteres. Ver [tipo de dados de cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
- **Comprimento da cadeia de caracteres de ambiente.** Há um máximo de 32768 caracteres para qualquer cadeia de caracteres de ambiente usado como um argumento de linha de comando. Essa é uma limitação em todas as plataformas.  
  
## <a name="see-also"></a>Consulte também

- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
