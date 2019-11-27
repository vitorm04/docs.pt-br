---
title: Limitações
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: f7e19977a011565bb4b1536af5cab195f8a01017
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347361"
---
# <a name="visual-basic-limitations"></a>Limitações do Visual Basic
Versões anteriores do Visual Basic limites impostos no código, como o comprimento de nomes de variáveis, o número de variáveis permitidas em módulos e o tamanho do módulo. No Visual Basic .NET, essas restrições foram reduzidas, dando a você maior liberdade de escrever e organizar seu código.  
  
 Os limites físicos são dependentes mais da memória em tempo de execução do que nas considerações de tempo de compilação. Se você usar práticas de programação prudentes e dividir aplicativos grandes em várias classes e módulos, haverá uma pequena chance de encontrar uma limitação de Visual Basic interno.  
  
 A seguir estão algumas limitações que você pode encontrar em casos extremos:  
  
- **Comprimento do nome.** Há um número máximo de caracteres para o nome de cada elemento de programação declarado. Esse máximo se aplica a uma cadeia de caracteres de qualificação inteira se o nome do elemento for qualificado. Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
- **Comprimento da linha.** Há um máximo de 65535 caracteres em uma linha física de código-fonte. A linha de código-fonte lógica pode ser maior se você usar caracteres de continuação de linha. Consulte [como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
- **Dimensões de matriz.** Há um número máximo de dimensões que você pode declarar para uma matriz. Isso limita quantos índices você pode usar para especificar um elemento de matriz. Consulte [dimensões de matriz em Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
- **Comprimento da cadeia de caracteres.** Há um número máximo de caracteres Unicode que você pode armazenar em uma única cadeia de caractere. Consulte [tipo de dados de cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
- **Comprimento da cadeia de caracteres do ambiente.** Há um máximo de 32768 caracteres para qualquer cadeia de caracteres de ambiente usada como um argumento de linha de comando. Essa é uma limitação em todas as plataformas.  
  
## <a name="see-also"></a>Consulte também

- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic convenções de nomenclatura](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
