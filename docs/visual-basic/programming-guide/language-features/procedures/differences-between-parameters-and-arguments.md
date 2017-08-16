---
title: "Diferenças entre parâmetros e argumentos (Visual Basic) | Documentos do Microsoft"
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
- procedures, parameters
- parameters, and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters, definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: 18
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
ms.openlocfilehash: 409fbfffb2fcd616da76544b6a66eda5838d8983
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Diferenças entre parâmetros e argumentos (Visual Basic)
Na maioria dos casos, um procedimento deve ter algumas informações sobre as circunstâncias em que ele foi chamado. Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada. Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando chamá-lo.  
  
 Para se comunicar essas informações para o procedimento, o procedimento define uma *parâmetro*, e o código de chamada passa um *argumento* para esse parâmetro. Você pode considerar o parâmetro como um espaço de estacionamento e o argumento de um automóvel. Assim como automóveis diferentes podem estaciono em um espaço de estacionamento em momentos diferentes, o código de chamada pode passar um argumento diferente para o mesmo parâmetro toda vez que ele chama o procedimento.  
  
## <a name="parameters"></a>Parâmetros  
 A *parâmetro* representa um valor que o procedimento espera que você passe quando você chamá-lo. Declaração do procedimento define seus parâmetros.  
  
 Quando você define uma `Function` ou `Sub` procedimento, você especificar um *lista de parâmetros* entre parênteses imediatamente após o nome do procedimento. Para cada parâmetro, você especificar um nome, um tipo de dados e um mecanismo de passagem ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Você também pode indicar que um parâmetro é opcional. Isso significa que o código de chamada não precisa passar um valor para ela.  
  
 O nome de cada parâmetro serve como um *variável local* no procedimento. Você usar o nome do parâmetro da mesma maneira que você usar qualquer outra variável.  
  
## <a name="arguments"></a>Arguments  
 Um *argumento* representa o valor que você passa para um parâmetro de procedimento quando você chamar o procedimento. O código de chamada fornece os argumentos quando ele chama o procedimento.  
  
 Quando você chama um `Function` ou `Sub` procedimento, você incluir um *lista de argumentos* entre parênteses imediatamente após o nome do procedimento. Cada argumento corresponde ao parâmetro na mesma posição na lista.  
  
 Em contraste com a definição do parâmetro, argumentos não têm nomes. Cada argumento é uma expressão, que pode conter zero ou mais variáveis, constantes e literais. O tipo de dados da expressão avaliada normalmente deve corresponder ao tipo de dados definido para o parâmetro correspondente e, em qualquer caso deve ser conversível para o tipo de parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de função](./function-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Como: definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos recursivos](./recursive-procedures.md)   
 [Sobrecarga de Procedimento](./procedure-overloading.md)
