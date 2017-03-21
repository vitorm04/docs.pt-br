---
title: "Constantes (Visual Basic) definidos pelo usuário | Documentos do Microsoft"
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
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
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
ms.openlocfilehash: e5942d8663a8866b2f9794a86756f2bf25660ba5
ms.lasthandoff: 03/13/2017

---
# <a name="user-defined-constants-visual-basic"></a>Constantes definidas pelo usuário (Visual Basic)
Uma constante é um nome significativo que toma o lugar de um número ou cadeia de caracteres que não são alterados. Constantes armazenam valores que, como o nome implica, permanecem constantes durante a execução de um aplicativo. Você pode usar constantes definidas por controles ou componentes que funcionam com ou você pode criar seus próprios. Constantes que você mesmo cria são descritas como *definidos pelo usuário*.  
  
 Declarar uma constante com o `Const` instrução, usando as mesmas diretrizes que você faria para criar um nome de variável. Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.  
  
## <a name="const-statement-usage"></a>Uso da instrução Const  
 Um `Const` declaração pode representar uma matemática ou quantidade de data/hora:  
  
 [!code-vb[VbEnumsTask n º&10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Ele também pode definir `String` constantes:  
  
 [!code-vb[VbEnumsTask&13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 A expressão à direita do sinal de igual ( `=` ) é geralmente um número ou cadeia de caracteres literal, mas também pode ser uma expressão que resulta em um número ou cadeia de caracteres (embora essa expressão não pode conter chamadas a funções). Você pode até mesmo definir constantes em termos de constantes definidas anteriormente:  
  
 [!code-vb[VbEnumsTask&#15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>Escopo de constantes definidas pelo usuário  
 Um `Const` escopo da instrução é o mesmo que uma variável declarada no mesmo local. Você pode especificar o escopo em qualquer uma das seguintes maneiras:  
  
-   Para criar uma constante que existe somente dentro de um procedimento, declare-a dentro desse procedimento.  
  
-   Para criar uma constante disponível para todos os procedimentos dentro de uma classe, mas não para qualquer código fora desse módulo, declare-o na seção de declarações da classe.  
  
-   Para criar uma constante que está disponível para todos os membros de um assembly, mas não para clientes fora do assembly, declare-a usando o `Friend` palavra-chave na seção de declarações da classe.  
  
-   Para criar uma constante disponível em todo o aplicativo, declare-a usando o `Public` seção de palavra-chave nas declarações de classe.  
  
 Para obter mais informações, consulte [como: declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Evitando referências circulares  
 Como constantes podem ser definidas em termos de outras constantes, é possível criar inadvertidamente um *ciclo*, ou referência circular, entre duas ou mais constantes. Um ciclo ocorre quando você tiver duas ou mais constantes públicas, cada um deles é definida em termos da outra, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask n º&16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[17 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Se ocorrer um ciclo, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gera um erro do compilador.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Tipos de dados constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constantes e enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
