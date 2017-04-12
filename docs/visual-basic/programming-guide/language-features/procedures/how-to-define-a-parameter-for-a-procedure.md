---
title: "Como: definir um parâmetro para um procedimento (Visual Basic) | Documentos do Microsoft"
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
- procedure parameters, defining data types for
- procedures, parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters, defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
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
ms.openlocfilehash: 9fb9ad244499039c1768ff97f071168e0a0842e4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Como definir um parâmetro para um procedimento (Visual Basic)
A *parâmetro* permite que o código passe um valor ao procedimento quando ele chama. Você declara cada parâmetro para um procedimento da mesma maneira que você declarar uma variável, especificando seu nome e tipo de dados. Você também especificar o mecanismo de passagem, e se o parâmetro é opcional.  
  
 Para obter mais informações, consulte [argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Para definir um parâmetro de procedimento  
  
1.  Na declaração do procedimento, adicione o nome do parâmetro à lista de parâmetros do procedimento, separando-o de outros parâmetros por vírgulas.  
  
2.  Decida o tipo de dados do parâmetro.  
  
3.  Siga o nome do parâmetro com um `As` cláusula para especificar o tipo de dados.  
  
4.  Decida o mecanismo de passagem que você deseja para o parâmetro. Normalmente você passa um parâmetro por valor, a menos que o procedimento seja capaz de alterar seu valor no código de chamada.  
  
5.  Preceda o nome do parâmetro com [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para especificar o mecanismo de passagem. Para obter mais informações, consulte [as diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Se o parâmetro é opcional, preceda o mecanismo de passagem com [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) e siga o tipo de dados de parâmetro com um sinal de igual (`=`) e um valor padrão.  
  
     O exemplo a seguir define o contorno de uma `Sub` procedimento com três parâmetros. As duas primeiras são necessárias e o terceiro é opcional. As declarações de parâmetro são separadas na lista de parâmetros por vírgulas.  
  
     [!code-vb[33 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     O primeiro parâmetro aceita um `customer` objeto, e `updateCustomer` pode atualizar diretamente a variável passada para `c` porque o argumento é passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). O procedimento não pode alterar os valores dos dois últimos argumentos porque eles são passados [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Se o código de chamada não fornecer um valor para o `level` parâmetro [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] define como o valor padrão de 0.  
  
     Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off`, o `As` cláusula é opcional quando você define um parâmetro. No entanto, se qualquer outro parâmetro usa um `As` cláusula, todos eles devem usá-lo. Se a opção de verificação de tipo é `On`, o `As` cláusula é necessária para cada definição de parâmetro.  
  
     Especificar tipos de dados para todos os elementos de programação é conhecido como *tipagem forte*. Quando você define `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] impõe a tipagem forte. Isso é fortemente recomendado, pelas seguintes razões:  
  
    -   Ela permite suporte IntelliSense para suas variáveis e parâmetros. Isso permite que você veja suas propriedades e outros membros conforme você digita no seu código.  
  
    -   Ele permite que o compilador execute a verificação de tipo. Isso ajuda a obter declarações que podem falhar em tempo de execução devido a erros como overflow. Ele também captura chamadas para métodos em objetos que não oferecem suporte a eles.  
  
    -   Isso resulta em execução mais rápida do seu código. Uma razão para isso é que, se você não especificar um tipo de dados para um elemento de programação, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador atribui o `Object` tipo. Seu código compilado pode ter que converter entre `Object` e outros tipos de dados, o que reduz o desempenho.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de função](./function-procedures.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos recursivos](./recursive-procedures.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programação Orientada a Objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
