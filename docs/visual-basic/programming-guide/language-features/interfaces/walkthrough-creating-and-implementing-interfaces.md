---
title: Criando e implementando Interfaces (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08bf6dc7344d4f83c8ab1908fdeb29eb4a53e142
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Instruções passo a passo: criando e implementando interfaces (Visual Basic)
Interfaces descrevem as características de propriedades, métodos e eventos, mas deixam os detalhes de implementação até classes ou estruturas.  
  
 Este passo a passo demonstra como declarar e implementar uma interface.  
  
> [!NOTE]
>  Este passo a passo não fornece informações sobre como criar uma interface do usuário.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-an-interface"></a>Para definir uma interface  
  
1.  Abra um novo projeto de aplicativos do Windows [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
2.  Adicionar um novo módulo ao projeto clicando **Adicionar módulo** no **projeto** menu.  
  
3.  Nomeie o novo módulo `Module1.vb` e clique em **adicionar**. O código para o novo módulo é exibido.  
  
4.  Definir uma interface denominada `TestInterface` em `Module1` digitando `Interface TestInterface` entre o `Module` e `End Module` instruções e, em seguida, pressionando ENTER. O **Editor de códigos** recuos o `Interface` palavra-chave e adiciona um `End Interface` instrução para formar um bloco de código.  
  
5.  Definir uma propriedade, método e evento para a interface, colocando o código a seguir entre a `Interface` e `End Interface` instruções:  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>Implementação  
 Você pode perceber que a sintaxe usada para declarar membros de interface é diferente da sintaxe usada para declarar membros de classe. Essa diferença reflete o fato de que interfaces não podem conter código de implementação.  
  
#### <a name="to-implement-the-interface"></a>Para implementar a interface  
  
1.  Adicione uma classe denominada `ImplementationClass` adicionando a seguinte instrução para `Module1`, depois o `End Interface` instrução mas antes de `End Module` instrução e, em seguida, pressionando ENTER:  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     Se você estiver trabalhando no ambiente de desenvolvimento integrado, a **Editor de códigos** fornece uma correspondência `End Class` instrução quando você pressiona ENTER.  
  
2.  Adicione o seguinte `Implements` instrução `ImplementationClass`, que chama a interface a classe implementa:  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     Quando listados separadamente de outros itens na parte superior de uma classe ou estrutura, o `Implements` instrução indica que a classe ou estrutura implementa uma interface.  
  
     Se você estiver trabalhando no ambiente de desenvolvimento integrado, a **Editor de códigos** implementa os membros de classe exigidos pelo `TestInterface` quando você pressiona ENTER, e você pode ignorar a próxima etapa.  
  
3.  Se você não estiver trabalhando no ambiente de desenvolvimento integrado, você deve implementar todos os membros da interface `MyInterface`. Adicione o seguinte código para `ImplementationClass` implementar `Event1`, `Method1`, e `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     O `Implements` instrução nomeia a interface e o membro de interface que está sendo implementada.  
  
4.  Conclua a definição de `Prop1` adicionando um campo particular para a classe que o valor da propriedade de armazenados:  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     O valor de retorno de `pval` da propriedade de acessador get.  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     Defina o valor de `pval` na propriedade de acessador set.  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  Conclua a definição de `Method1` adicionando o código a seguir.  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>Para testar a implementação da interface  
  
1.  Clique o formulário de inicialização para seu projeto no **Solution Explorer**e clique em **Exibir código**. O editor exibe a classe para o formulário de inicialização. Por padrão, o formulário de inicialização é chamado `Form1`.  
  
2.  Adicione o seguinte `testInstance` campo para o `Form1` classe:  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     Declarando `testInstance` como `WithEvents`, o `Form1` classe pode manipular seus eventos.  
  
3.  Adicionar manipulador de eventos para o `Form1` classe para manipular eventos gerados por `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  Adicionar uma sub-rotina chamada `Test` para o `Form1` classe para testar a classe de implementação:  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     O `Test` procedimento cria uma instância da classe que implementa `MyInterface`, atribui essa instância para o `testInstance` define uma propriedade de campo e executa um método por meio da interface.  
  
5.  Adicione código para chamar o `Test` procedimento o `Form1 Load` procedimento do formulário de inicialização:  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  Execute o `Test` procedimento pressionando F5. A mensagem "Prop1 foi definido como 9" é exibida. Depois que você clicar em Okey, a mensagem "o parâmetro X Method1 é 5" é exibida. Clique em Okey e a mensagem "o manipulador de eventos capturou o evento" é exibida.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Instrução Interface](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrução Event](../../../../visual-basic/language-reference/statements/event-statement.md)
