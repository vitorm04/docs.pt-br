---
title: Subprocedimentos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: b70594e002bbf08f0890586e78df901ccb26c7ce
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843096"
---
# <a name="sub-procedures-visual-basic"></a>Subprocedimentos (Visual Basic)
Um `Sub` procedimento é uma série de instruções do Visual Basic entre o `Sub` e `End Sub` instruções. O `Sub` procedimento executa uma tarefa e, em seguida, retorna o controle para o código de chamada, mas não retorna um valor para o código de chamada.  
  
 Cada vez que é chamada de procedimento, suas declarações são executadas, começando com a primeira instrução executável após o `Sub` instrução e terminando com a primeira `End Sub`, `Exit Sub`, ou `Return` instrução encontrado.  
  
 Você pode definir um `Sub` procedimento em módulos, classes e estruturas. Por padrão, ele é `Public`, que significa que você pode chamá-lo de qualquer lugar em seu aplicativo que tem acesso para o módulo, classe ou estrutura na qual você a definiu. O termo *método*, descreve uma `Sub` ou `Function` procedimento que é acessado de fora de sua definição de módulo, classe ou estrutura. Para obter mais informações, consulte [Procedimentos](./index.md).  
  
 Um `Sub` procedimento pode receber argumentos, como constantes, variáveis ou expressões que são passadas a ele pelo código de chamada.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 A sintaxe para declarar um `Sub` procedimento é o seguinte:  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 O `modifiers` pode especificar o nível de acesso e informações sobre sobrecarregamento, substituição, compartilhamento e sombreamento. Para obter mais informações, consulte [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Declaração de parâmetro  
 Você declarar cada parâmetro de procedimento da mesma forma como você declara uma variável, especificando o tipo de dados e o nome do parâmetro. Você também pode especificar o mecanismo de passagem e se o parâmetro é opcional ou uma matriz de parâmetros.  
  
 A sintaxe para cada parâmetro na lista de parâmetros é da seguinte maneira:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*  
  
 Se o parâmetro é opcional, você também deve fornecer um valor padrão como parte de sua declaração. A sintaxe para especificar um valor padrão é da seguinte maneira:  
  
 `Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>Parâmetros como variáveis locais  
 Quando o controle passa para o procedimento, cada parâmetro é tratado como uma variável local. Isso significa que seu tempo de vida é o mesmo que o procedimento e seu escopo é todo o procedimento.  
  
## <a name="calling-syntax"></a>Sintaxe de chamada  
 Você invoca um `Sub` procedimento explicitamente com uma instrução de chamada autônoma. Você não pode chamá-lo usando seu nome em uma expressão. Você deve fornecer valores para todos os argumentos que não são opcionais e você deve colocar a lista de argumentos entre parênteses. Se nenhum argumento for fornecido, você pode, opcionalmente, omitir os parênteses. O uso do `Call` palavra-chave é opcional, mas não é recomendado.  
  
 A sintaxe para chamar um `Sub` procedimento é o seguinte:  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 Você pode chamar um `Sub` método de fora da classe que o define. Primeiro, você precisa usar o `New` palavra-chave para criar uma instância da classe, ou chamar um método que retorna uma instância da classe. Para obter mais informações, consulte [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md). Em seguida, você pode usar a seguinte sintaxe para chamar o `Sub` método no objeto de exemplo:  
  
 *Objeto*. *MethodName*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 O seguinte `Sub` procedimento informa o operador do computador qual tarefa o aplicativo está prestes a executar e também exibe um carimbo de data / hora. Em vez de duplicar esse código no início de cada tarefa, o aplicativo apenas chama `tellOperator` de vários locais. Cada chamada passa uma cadeia de caracteres a `task` argumento que identifica a tarefa que está sendo iniciada.  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 O exemplo a seguir mostra uma chamada típica para `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Como: Chamar um procedimento que não retorna um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Como: Chamar um manipulador de eventos no Visual Basic](./how-to-call-an-event-handler.md)
