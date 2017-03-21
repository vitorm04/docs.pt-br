---
title: "Diferenças entre argumentos modificável e não modificável (Visual Basic) | Documentos do Microsoft"
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
- procedures, arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
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
ms.openlocfilehash: 810a5539a8ffccbc3205b8a3387761496b07dddc
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Diferenças entre argumentos modificáveis e não modificáveis (Visual Basic)
Quando você chama um procedimento, você normalmente passa um ou mais argumentos para ele. Cada argumento corresponde a um elemento de programação subjacente. Os elementos subjacentes e os próprios argumentos podem ser modificáveis ou não modificáveis.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Elementos modificáveis e não modificáveis  
 Um elemento de programação pode ser um *elemento modificável*, que pode ter seu valor alterado, ou um *elemento não modificável*, que tem um valor fixo após ele ter sido criado.  
  
 A tabela a seguir lista os elementos de programação modificáveis e não modificáveis.  
  
|Elementos modificáveis|Elementos não modificáveis|  
|-------------------------|----------------------------|  
|Variáveis locais (declaradas dentro de procedimentos), incluindo variáveis de objeto, exceto para somente leitura|Variáveis somente leitura, campos e propriedades|  
|Campos (membro variáveis de módulos, classes e estruturas), exceto para somente leitura|Literais e constantes|  
|Propriedades, exceto para somente leitura|Membros de enumeração|  
|Elementos de matriz|Expressões (mesmo se seus elementos são modificáveis)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Argumentos modificável e não modificável  
 A *argumento modificável* é uma com um elemento subjacente modificável. O código de chamada pode armazenar um novo valor a qualquer momento, e se você passar o argumento [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), o código no procedimento também pode modificar o elemento subjacente no código de chamada.  
  
 A *argumento não modificável* tem um elemento subjacente não modificável ou é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). O procedimento não pode modificar o elemento subjacente no código de chamada, mesmo se ele for um elemento modificável. Se for um elemento não modificável, o código de chamada não pode modificá-lo.  
  
 O procedimento chamado pode modificar sua cópia local de um argumento não modificável, mas essa modificação não afeta o elemento subjacente no código de chamada.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)   
 [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md)   
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
