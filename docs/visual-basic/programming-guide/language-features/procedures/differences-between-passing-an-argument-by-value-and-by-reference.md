---
title: "Diferenças entre passar um argumento por valor e por referência (Visual Basic) | Documentos do Microsoft"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
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
ms.openlocfilehash: 93c515dd8524cde85555a27879baee00185f78e3
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Diferenças entre passar um argumento por valor e por referência (Visual Basic)
Quando você passar um ou mais argumentos para um procedimento, cada argumento corresponde a um elemento de programação subjacente no código de chamada. Você pode passar o valor desse elemento ou uma referência a ele. Isso é conhecido como o *mecanismo de passagem*.  
  
## <a name="passing-by-value"></a>Passagem por valor  
 Passar um argumento *pelo valor* especificando o [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) palavra-chave para o parâmetro correspondente na definição do procedimento. Quando você usa este mecanismo de passagem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copia o valor do elemento de programação subjacente em uma variável local no procedimento. O código do procedimento não tem nenhum acesso ao elemento subjacente no código de chamada.  
  
## <a name="passing-by-reference"></a>Passagem por referência  
 Passar um argumento *por referência* especificando o [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave para o parâmetro correspondente na definição do procedimento. Quando você usa este mecanismo de passagem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece o procedimento uma referência direta ao elemento de programação subjacente no código de chamada.  
  
## <a name="passing-mechanism-and-element-type"></a>Mecanismo de passagem e tipo de elemento  
 A escolha do mecanismo de passagem não é o mesmo que a classificação de tipo do elemento. Passagem por valor ou referência se refere ao que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece ao código do procedimento. Um tipo de valor ou referência se refere a como um elemento de programação é armazenado na memória.  
  
 No entanto, o mecanismo de passagem e o tipo de elemento são inter-relacionados. O valor de um tipo de referência é um ponteiro para os dados em outro lugar na memória. Isso significa que quando você passa um tipo de referência por valor, o código do procedimento tem um ponteiro para os dados do elemento, mesmo que ele não pode acessar o elemento subjacente. Por exemplo, se o elemento é uma variável de matriz, o código do procedimento não tem acesso à variável em si, mas ele pode acessar os membros da matriz.  
  
## <a name="ability-to-modify"></a>Capacidade de modificar  
 Quando você passa um elemento não modificável como um argumento, o procedimento nunca pode modificá-lo no código de chamada, se é passado `ByVal` ou `ByRef`.  
  
 Para um elemento modificável, a tabela a seguir resume a interação entre o tipo de elemento e o mecanismo de passagem.  
  
|Tipo de elemento|Passado`ByVal`|Passado`ByRef`|  
|------------------|--------------------|--------------------|  
|Tipo de valor (contém apenas um valor)|O procedimento não pode alterar a variável ou qualquer um de seus membros.|O procedimento pode mudar a variável e seus membros.|  
|Tipo de referência (contém um ponteiro para uma instância de classe ou estrutura)|O procedimento não é possível alterar a variável mas pode mudar membros da instância para qual ele aponta.|O procedimento pode alterar a variável e membros da instância para qual ele aponta.|  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Diferenças entre argumentos modificável e não modificável](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)   
 [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md)   
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
