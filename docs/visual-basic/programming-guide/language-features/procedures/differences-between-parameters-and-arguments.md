---
title: "Diferenças entre parâmetros e argumentos (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Diferenças entre parâmetros e argumentos (Visual Basic)
Na maioria dos casos, um procedimento deve ter algumas informações sobre as circunstâncias em que ele foi chamado. Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada. Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando chamá-lo.  
  
 Para comunicar essa informação para o procedimento, o procedimento define um *parâmetro*, e o código de chamada passa um *argumento* para esse parâmetro. Você pode considerar o parâmetro como um espaço de estacionamento e o argumento como um automóvel. Assim como automóveis diferentes podem estacionar em um espaço de estacionamento em momentos diferentes, o código de chamada pode passar um argumento diferente para o mesmo parâmetro toda vez que ele chama o procedimento.  
  
## <a name="parameters"></a>Parâmetros  
 Um *parâmetro* representa um valor que o procedimento espera passar quando você chamá-lo. Declaração do procedimento define seus parâmetros.  
  
 Quando você define uma `Function` ou `Sub` procedimento, você especificar um *lista de parâmetros* entre parênteses imediatamente após o nome do procedimento. Para cada parâmetro, você especificar um nome, um tipo de dados e um mecanismo de passagem ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Você também pode indicar que um parâmetro é opcional. Isso significa que o código de chamada não precisa passar um valor para ele.  
  
 O nome de cada parâmetro serve como um *variável local* no procedimento. Você usar o nome do parâmetro da mesma maneira que você usar qualquer outra variável.  
  
## <a name="arguments"></a>Arguments  
 Um *argumento* representa o valor que você passa para um parâmetro de procedimento quando você chamar o procedimento. O código de chamada fornece os argumentos quando ele chama o procedimento.  
  
 Quando você chama um `Function` ou `Sub` procedimento, você incluir um *lista de argumentos* entre parênteses imediatamente após o nome do procedimento. Cada argumento corresponde ao parâmetro na mesma posição na lista.  
  
 Em contraste com a definição de parâmetro, os argumentos não têm nomes. Cada argumento é uma expressão, que pode conter zero ou mais variáveis, constantes e literais. O tipo de dados da expressão avaliada normalmente deve corresponder ao tipo de dados definido para o parâmetro correspondente e, em qualquer caso deve ser conversível para o tipo de parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Como definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Procedimentos Recursivos](./recursive-procedures.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)
