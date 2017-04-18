---
title: Criando e implementando Interfaces (Visual Basic) | Documentos do Microsoft
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
- interfaces, walkthroughs
- interfaces, testing
- interface implementation, walkthrough
- interfaces, creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
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
ms.openlocfilehash: 076bc8d33e97286c31f27a2016e39a25e9cec22c
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Instruções passo a passo: criando e implementando interfaces (Visual Basic)
Interfaces descrevem as características de propriedades, métodos e eventos, mas deixe os detalhes de implementação para classes ou estruturas.  
  
 Este passo a passo demonstra como declarar e implementar uma interface.  
  
> [!NOTE]
>  Este passo a passo não fornece informações sobre como criar uma interface do usuário.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a>Para definir uma interface  
  
1.  Abra um novo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto aplicativo do Windows.  
  
2.  Adicionar um novo módulo para o projeto clicando em **Adicionar módulo** sobre o **projeto** menu.  
  
3.  Nomeie o novo módulo `Module1.vb` e clique em **adicionar**. O código para o novo módulo é exibido.  
  
4.  Definir uma interface denominada `TestInterface` na `Module1` digitando `Interface TestInterface` entre o `Module` e `End Module` instruções e pressionando ENTER. O **Editor de códigos** recua o `Interface` palavra-chave e adiciona um `End Interface` instrução para formar um bloco de código.  
  
5.  Definir uma propriedade, método e evento para a interface, colocando o código a seguir entre o `Interface` e `End Interface` instruções:  
  
     [!code-vb[VbVbalrOOP&#98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>Implementação  
 Você notará que a sintaxe usada para declarar membros de interface é diferente da sintaxe usada para declarar membros de classe. Essa diferença reflete o fato de que interfaces não podem conter código de implementação.  
  
#### <a name="to-implement-the-interface"></a>Para implementar a interface  
  
1.  Adicione uma classe chamada `ImplementationClass` adicionando a seguinte instrução para `Module1`, após o `End Interface` instrução mas antes de `End Module` instrução e pressione ENTER:  
  
     [!code-vb[VbVbalrOOP&#99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     Se você estiver trabalhando no ambiente de desenvolvimento integrado, o **Editor de códigos** fornece uma correspondência `End Class` instrução quando você pressiona ENTER.  
  
2.  Adicione o seguinte `Implements` instrução `ImplementationClass`, que chama a interface a classe implementa:  
  
     [!code-vb[VbVbalrOOP&#100;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     Quando listados separadamente de outros itens na parte superior de uma classe ou estrutura, o `Implements` instrução indica que a classe ou estrutura implementa uma interface.  
  
     Se você estiver trabalhando no ambiente de desenvolvimento integrado, o **Editor de códigos** implementa os membros de classe exigidos pelo `TestInterface` quando você pressiona ENTER, e você pode ignorar a próxima etapa.  
  
3.  Se você não estiver trabalhando no ambiente de desenvolvimento integrado, você deve implementar todos os membros da interface `MyInterface`. Adicione o seguinte código para `ImplementationClass` implementar `Event1`, `Method1`, e `Prop1`:  
  
     [!code-vb[VbVbalrOOP&#101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     O `Implements` instrução nomeia a interface e o membro de interface que está sendo implementado.  
  
4.  Concluir a definição de `Prop1` adicionando um campo particular para a classe que armazenado o valor da propriedade:  
  
     [!code-vb[VbVbalrOOP&#102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     Retornar o valor de `pval` da propriedade de acessador get.  
  
     [!code-vb[VbVbalrOOP&#103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     Defina o valor de `pval` na propriedade de acessador set.  
  
     [!code-vb[VbVbalrOOP&#104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  Concluir a definição de `Method1` adicionando o código a seguir.  
  
     [!code-vb[VbVbalrOOP&#105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>Para testar a implementação da interface  
  
1.  Clique com botão direito do formulário de inicialização para seu projeto no **Solution Explorer**e clique em **Exibir código**. O editor exibe a classe para o formulário de inicialização. Por padrão, o formulário de inicialização é chamado `Form1`.  
  
2.  Adicione o seguinte `testInstance` campo para o `Form1` classe:  
  
     [!code-vb[VbVbalrOOP&#120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     Declarando `testInstance` como `WithEvents`, a `Form1` classe pode manipular seus eventos.  
  
3.  Adicione o seguinte manipulador de eventos para o `Form1` classe para manipular eventos acionados por `testInstance`:  
  
     [!code-vb[VbVbalrOOP&#106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  Adicionar uma sub-rotina chamada `Test` para o `Form1` classe para testar a classe de implementação:  
  
     [!code-vb[VbVbalrOOP&#107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     O `Test` procedimento cria uma instância da classe que implementa `MyInterface`, atribui essa instância para o `testInstance` define uma propriedade de campo e executa um método por meio da interface.  
  
5.  Adicionar código para chamar o `Test` procedimento o `Form1 Load` procedimento de seu formulário de inicialização:  
  
     [!code-vb[VbVbalrOOP&#108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  Execute o `Test` procedimento pressionando F5. A mensagem "Prop1 foi definido como 9" é exibida. Depois de clicar em Okey, a mensagem "o parâmetro X Method1 é 5" é exibida. Clique em Okey e a mensagem "detectada ao manipulador de eventos do evento" é exibida.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](../../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Instrução interface](../../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Event](../../../../visual-basic/language-reference/statements/event-statement.md)

