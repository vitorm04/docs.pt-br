---
title: Diferenças entre passar um argumento por valor e por referência
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 84ec3bac2532b2cef72ddda347251bc987801c3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341228"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Diferenças entre passar um argumento por valor e por referência (Visual Basic)
Quando você passa um ou mais argumentos para um procedimento, cada argumento corresponde a um elemento de programação subjacente no código de chamada. Você pode passar o valor desse elemento subjacente ou uma referência a ele. Isso é conhecido como o *mecanismo de passagem*.  
  
## <a name="passing-by-value"></a>passagem por valor  
 Você passa um argumento *por valor* especificando a palavra-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente na definição do procedimento. Quando você usa esse mecanismo de passagem, o Visual Basic copia o valor do elemento de programação subjacente em uma variável local no procedimento. O código do procedimento não tem nenhum acesso ao elemento subjacente no código de chamada.  
  
## <a name="passing-by-reference"></a>Passando por referência  
 Você passa um argumento *por referência* especificando a palavra-chave [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente na definição do procedimento. Quando você usa esse mecanismo de passagem, Visual Basic dá ao procedimento uma referência direta para o elemento de programação subjacente no código de chamada.  
  
## <a name="passing-mechanism-and-element-type"></a>Tipo de mecanismo e elemento de passagem  
 A escolha do mecanismo de passagem não é a mesma que a classificação do tipo de elemento subjacente. A passagem por valor ou por referência refere-se ao que Visual Basic fornece ao código do procedimento. Um tipo de valor ou tipo de referência refere-se a como um elemento de programação é armazenado na memória.  
  
 No entanto, o mecanismo de passagem e o tipo de elemento são inter-relacionados. O valor de um tipo de referência é um ponteiro para os dados em outro lugar na memória. Isso significa que quando você passa um tipo de referência por valor, o código do procedimento tem um ponteiro para os dados do elemento subjacente, mesmo que ele não possa acessar o próprio elemento subjacente. Por exemplo, se o elemento for uma variável de matriz, o código do procedimento não terá acesso à variável em si, mas poderá acessar os membros da matriz.  
  
## <a name="ability-to-modify"></a>Capacidade de modificar  
 Quando você passa um elemento não modificável como um argumento, o procedimento nunca pode modificá-lo no código de chamada, quer seja passado `ByVal` ou `ByRef`.  
  
 Para um elemento modificável, a tabela a seguir resume a interação entre o tipo de elemento e o mecanismo de passagem.  
  
|Tipo de elemento|Passou `ByVal`|Passou `ByRef`|  
|------------------|--------------------|--------------------|  
|Tipo de valor (contém apenas um valor)|O procedimento não pode alterar a variável ou nenhum de seus membros.|O procedimento pode alterar a variável e seus membros.|  
|Tipo de referência (contém um ponteiro para uma classe ou instância de estrutura)|O procedimento não pode alterar a variável, mas pode alterar os membros da instância para a qual ela aponta.|O procedimento pode alterar a variável e os membros da instância para a qual ele aponta.|  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Diferenças entre argumentos modificáveis e não modificáveis](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Como alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)
- [Como proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Como forçar um argumento a ser passado por Valor](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
