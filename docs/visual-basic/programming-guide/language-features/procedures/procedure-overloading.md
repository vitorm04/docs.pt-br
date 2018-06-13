---
title: Sobrecarga de procedimento (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 0d1f2c4d8c88922659b3d91ed41d5e760e6e5233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653908"
---
# <a name="procedure-overloading-visual-basic"></a>Sobrecarga de procedimento (Visual Basic)
*Sobrecarga* significa que um procedimento defini-lo em várias versões, usando o mesmo nome, mas listas de parâmetros diferentes. O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem diferenciá-los por nome. Você pode fazer isso variando a lista de parâmetros.  
  
## <a name="overloading-rules"></a>Sobrecarga de regras  
 Quando você sobrecarregar um procedimento, as seguintes regras se aplicam:  
  
-   **Mesmo nome**. Cada versão sobrecarregada deve usar o mesmo nome do procedimento.  
  
-   **Assinatura diferente**. Cada versão sobrecarregada deve diferir de todas as outras versões sobrecarregadas em pelo menos um dos seguintes aspectos:  
  
    -   Número de parâmetros  
  
    -   Ordem dos parâmetros  
  
    -   Tipos de dados dos parâmetros  
  
    -   Número de parâmetros de tipo (para um procedimento genérico)  
  
    -   Tipo de retorno (somente para um operador de conversão)  
  
     Junto com o nome do procedimento, os itens anteriores são coletivamente chamados de *assinatura* do procedimento. Quando você chamar um procedimento sobrecarregado, o compilador usa a assinatura para verificar se a chamada corretamente corresponde a definição.  
  
-   **Itens não faz parte da assinatura**. Você não pode sobrecarregar um procedimento sem variando a assinatura. Em particular, você não pode sobrecarregar um procedimento, variando apenas um ou mais dos seguintes itens:  
  
    -   Palavras-chave com o modificador de procedimento, como `Public`, `Shared`, e `Static`  
  
    -   Nomes de parâmetro de parâmetro ou tipo  
  
    -   Restrições de parâmetro de tipo (para um procedimento genérico)  
  
    -   Palavras-chave com o modificador de parâmetro, como `ByRef` e `Optional`  
  
    -   Se ele retorna um valor  
  
    -   O tipo de dados do valor de retorno (exceto para um operador de conversão)  
  
     Os itens na lista anterior não fazem parte da assinatura. Embora você não pode usá-los para diferenciar entre versões sobrecarregadas, você pode variá-los entre versões sobrecarregadas corretamente são diferenciadas por suas assinaturas.  
  
-   **Associação tardia argumentos**. Se você pretende passar uma variável de objeto associado a mais de uma versão sobrecarregada, você deve declarar o parâmetro apropriado como <xref:System.Object>.  
  
## <a name="multiple-versions-of-a-procedure"></a>Várias versões de um procedimento  
 Suponha que você está escrevendo uma `Sub` procedimento para lançar uma transação contra um saldo do cliente e você deseja ser capaz de fazer referência ao cliente pelo nome ou pelo número de conta. Para acomodar isso, você pode definir duas diferentes `Sub` procedimentos, como no exemplo a seguir:  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a>Versões sobrecarregadas  
 Uma alternativa é a sobrecarga de um único nome de procedimento. Você pode usar o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave para definir uma versão do procedimento para cada lista de parâmetros, da seguinte maneira:  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a>Sobrecargas adicionais  
 Se você quiser aceitar o valor de uma transação no `Decimal` ou `Single`, você pode sobrecarregar mais `post` para permitir essa variação. Se você já fez isso para cada uma das sobrecargas no exemplo anterior, você teria que quatro `Sub` procedimentos, tudo com o mesmo nome mas com quatro assinaturas diferentes.  
  
## <a name="advantages-of-overloading"></a>Vantagens da sobrecarga  
 A vantagem de sobrecarregar um procedimento é a flexibilidade da chamada. Para usar o `post` procedimento declarado no exemplo anterior, o código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, chame o procedimento mesmo em ambos os casos. O exemplo a seguir ilustra isto:  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Como definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Como chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)  
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)  
 [Resolução de Sobrecarga](./overload-resolution.md)  
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
