---
title: Diferenças entre argumentos modificáveis e não modificáveis (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826659"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Diferenças entre argumentos modificáveis e não modificáveis (Visual Basic)
Quando você chama um procedimento, você normalmente passa um ou mais argumentos para ele. Cada argumento corresponde a um elemento de programação subjacente. Os elementos subjacentes e os próprios argumentos podem ser modificável ou não modificável.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Elementos modificável e  
 Um elemento de programação pode ser um *elemento modificável*, que pode ter seu valor alterado, ou um *elemento não modificável*, que tem um valor fixo quando ele tiver sido criado.  
  
 A tabela a seguir lista os elementos de programação modificáveis e não modificáveis.  
  
|Elementos modificáveis|Elementos não modificáveis|  
|-------------------------|----------------------------|  
|Variáveis locais (declaradas dentro de procedimentos), incluindo variáveis de objeto, exceto para somente leitura|Propriedades, campos e variáveis somente leitura|  
|Campos (variáveis de membro de módulos, classes e estruturas), exceto para somente leitura|Literais e constantes|  
|Propriedades, exceto para somente leitura|Membros de enumeração|  
|Elementos de matriz|Expressões (mesmo se seus elementos são modificáveis)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Argumentos modificáveis e  
 Um *argumento modificável* é aquele com um elemento subjacente modificável. O código de chamada pode armazenar um novo valor a qualquer momento, e se você passar o argumento [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), o código no procedimento também pode modificar o elemento subjacente no código de chamada.  
  
 Um *argumento não modificável* tem um elemento subjacente não modificável ou é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). O procedimento não pode modificar o elemento subjacente no código de chamada, mesmo se for um elemento modificável. Se for um elemento não modificável, o código de chamada em si não é possível modificá-lo.  
  
 O procedimento chamado pode modificar sua cópia local de um argumento não modificável, mas essa modificação não afeta o elemento subjacente no código de chamada.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Como: Passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Como: Altere o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)
- [Como: Proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Como: Forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
