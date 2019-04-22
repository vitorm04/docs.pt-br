---
title: Chamando uma propriedade ou um método usando o nome de uma cadeia de caracteres (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: e267c0c4d1d3e8f986348863d933c984f686b33b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842636"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Chamando uma propriedade ou um método usando o nome de uma cadeia de caracteres (Visual Basic)
Na maioria dos casos, você pode descobrir as propriedades e métodos de um objeto em tempo de design e escrever código para lidar com eles. No entanto, em alguns casos você pode não saber sobre as propriedades e métodos de um objeto com antecedência, ou apenas que a flexibilidade de habilitação de um usuário final especificar propriedades ou métodos de execução em tempo de execução.  
  
## <a name="callbyname-function"></a>Função CallByName  
 Considere, por exemplo, um aplicativo cliente que avalia as expressões inseridas pelo usuário, passando um operador para um componente COM. Suponha que você está constantemente adicionando novas funções ao componente que exigem novos operadores. Quando você usa técnicas de acesso a objeto padrão, você deve recompilar e redistribuir o aplicativo cliente antes que ele poderia usar os novos operadores. Para evitar isso, você pode usar o `CallByName` função para passar os novos operadores como cadeias de caracteres, sem alterar o aplicativo.  
  
 O `CallByName` função permite que você use uma cadeia de caracteres para especificar uma propriedade ou método em tempo de execução. A assinatura para o `CallByName` função tem esta aparência:  
  
 *Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())  
  
 O primeiro argumento, *objeto*, utiliza o nome do objeto que você deseja agir. O *ProcedureName* argumento leva a uma cadeia de caracteres que contém o nome do procedimento de método ou propriedade a ser invocado. O *CallType* argumento leva uma constante que representa o tipo de procedimento para chamar: um método (`Microsoft.VisualBasic.CallType.Method`), uma propriedade de leitura (`Microsoft.VisualBasic.CallType.Get`), ou um conjunto de propriedades (`Microsoft.VisualBasic.CallType.Set`). O *argumentos* argumento, que é opcional, leva uma matriz do tipo `Object` que contém quaisquer argumentos para o procedimento.  
  
 Você pode usar `CallByName` com as classes em sua solução atual, mas geralmente é usado para acessar objetos COM ou objetos de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.  
  
 Suponha que você adicione uma referência a um assembly que contém uma classe chamada `MathClass`, que tem uma nova função chamada `SquareRoot`, conforme mostrado no código a seguir:  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 Seu aplicativo pode usar controles de caixa de texto ao controle de qual método será chamado e seus argumentos. Por exemplo, se `TextBox1` contém a expressão a ser avaliada, e `TextBox2` é usado para inserir o nome da função, você pode usar o código a seguir para invocar o `SquareRoot` função na expressão no `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 Se você inserir "64" no `TextBox1`, "SquareRoot" no `TextBox2`e, em seguida, chame o `CallMath` procedimento, a raiz quadrada do número em `TextBox1` é avaliada. O código de exemplo invoca o `SquareRoot` (que usa uma cadeia de caracteres que contém a expressão seja avaliada como um argumento necessário) de função e retorna "8" `TextBox1` (a raiz quadrada de 64). Obviamente, se o usuário insere uma cadeia de caracteres inválida no `TextBox2`, se a cadeia de caracteres contém o nome de uma propriedade em vez de um método, ou se o método tinha um argumento adicional necessário, ocorrerá um erro de tempo de execução. Você precisa adicionar o código de tratamento de erros robusto ao usar `CallByName` para prever essas ou quaisquer outros erros.  
  
> [!NOTE]
>  Enquanto o `CallByName` função pode ser útil em alguns casos, você deve avaliar sua utilidade contra as implicações de desempenho — usando `CallByName` invocar um procedimento é ligeiramente mais lenta do que uma chamada de associação tardia. Se você estiver chamando uma função que é chamada repetidamente, tal como dentro de um loop, `CallByName` pode ter um efeito grave no desempenho.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Determinando o Tipo de Objeto](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
