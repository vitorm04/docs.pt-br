---
title: Constantes definidas pelo usuário (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: f0196457235ad77df545a367573f62b43209269d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906978"
---
# <a name="user-defined-constants-visual-basic"></a>Constantes definidas pelo usuário (Visual Basic)
Uma constante é um nome significativo que toma o lugar de um número ou cadeia de caracteres que não são alterados. Constantes armazenam valores que, como o nome implica, permanecem constantes durante a execução de um aplicativo. Você pode usar constantes que são definidas por controles ou componentes que funcionam com, ou você pode criar seus próprios. Constantes que você mesmo cria são descritas como *definidos pelo usuário*.  
  
 Declarar uma constante com o `Const` instrução, usando as mesmas diretrizes que você faria para a criação de um nome de variável. Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.  
  
## <a name="const-statement-usage"></a>Uso da instrução Const  
 Um `Const` declaração pode representar uma matemática ou quantidade de data/hora:  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 Ele também pode definir `String` constantes:  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 A expressão no lado direito do sinal de igual ( `=` ) costuma ser um número ou cadeia de caracteres literal, mas também pode ser uma expressão que resulta em um número ou cadeia de caracteres (embora essa expressão não pode conter chamadas a funções). Você pode até mesmo definir constantes em termos de constantes definidas anteriormente:  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>Escopo das constantes definidas pelo usuário  
 Um `Const` escopo da instrução é a mesma de uma variável declarada no mesmo local. Você pode especificar o escopo em qualquer uma das seguintes maneiras:  
  
-   Para criar uma constante que existe somente dentro de um procedimento, declare-o dentro desse procedimento.  
  
-   Para criar uma constante disponível para todos os procedimentos dentro de uma classe, mas não para qualquer código fora desse módulo, declare-o na seção de declarações da classe.  
  
-   Para criar uma constante que está disponível para todos os membros de um assembly, mas não para clientes fora do assembly, declare-o usando o `Friend` palavra-chave na seção de declarações da classe.  
  
-   Para criar uma constante disponível em todo o aplicativo, declare-o usando o `Public` seção de palavra-chave nas declarações de classe.  
  
 Para obter mais informações, confira [Como: Declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Evitar referências circulares  
 Como constantes podem ser definidas em termos de outras constantes, é possível criar inadvertidamente um *ciclo*, ou uma referência circular, entre duas ou mais constantes. Um ciclo ocorre quando você tem duas ou mais constantes públicas, cada um deles é definida em termos de outro, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 Se ocorrer um ciclo, o Visual Basic gera um erro do compilador.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Constantes e Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Visão geral de Enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Visão Geral de Constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Como: Declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
