---
title: Criando e implementando Interfaces (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 7a5694826e0fff82aceb8ad18f75f96f308e724c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680381"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Passo a passo: Criando e implementando Interfaces (Visual Basic)

Interfaces descrevem as características de propriedades, métodos e eventos, mas deixe os detalhes de implementação até classes ou estruturas.  
  
 Este passo a passo demonstra como declarar e implementar uma interface.  
  
> [!NOTE]
>  Este passo a passo não fornece informações sobre como criar uma interface do usuário.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Para definir uma interface
  
1.  Abra um novo projeto de aplicativo do Windows Visual Basic.  
  
2.  Adicionar um novo módulo ao projeto clicando **Adicionar módulo** sobre o **projeto** menu.  
  
3.  Nomeie o novo módulo `Module1.vb` e clique em **Add**. O código para o novo módulo é exibido.  
  
4.  Definir uma interface denominada `TestInterface` dentro de `Module1` digitando `Interface TestInterface` entre as `Module` e `End Module` instruções e, em seguida, pressionando ENTER. O **Editor de códigos** recuos a `Interface` palavra-chave e adiciona um `End Interface` instrução para formar um bloco de código.  
  
5.  Definir uma propriedade, método e evento para a interface, colocando o seguinte código entre o `Interface` e `End Interface` instruções:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implementação

 Você notará que a sintaxe usada para declarar membros de interface é diferente da sintaxe usada para declarar membros de classe. Essa diferença reflete o fato de que interfaces não podem conter código de implementação.  
  
### <a name="to-implement-the-interface"></a>Para implementar a interface
  
1.  Adicione uma classe chamada `ImplementationClass` adicionando a seguinte instrução para `Module1`após o `End Interface` instrução, mas antes de `End Module` instrução e, em seguida, pressionando ENTER:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Se você estiver trabalhando dentro do ambiente de desenvolvimento integrado, o **Editor de códigos** fornece uma correspondência `End Class` instrução quando você pressiona ENTER.  
  
2.  Adicione o seguinte `Implements` instrução para `ImplementationClass`, que chama a interface a classe implementa:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Quando listados separadamente de outros itens na parte superior de uma classe ou estrutura, o `Implements` instrução indica que a classe ou estrutura implementa uma interface.  
  
     Se você estiver trabalhando dentro do ambiente de desenvolvimento integrado, o **Editor de códigos** implementa os membros de classe exigidos pelo `TestInterface` quando você pressiona ENTER, e você poderá ignorar a próxima etapa.  
  
3.  Se você não estiver trabalhando dentro do ambiente de desenvolvimento integrado, você deve implementar todos os membros da interface `MyInterface`. Adicione o seguinte código ao `ImplementationClass` implementar `Event1`, `Method1`, e `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     O `Implements` instrução nomeia a interface e o membro de interface que está sendo implementado.  
  
4.  Concluir a definição de `Prop1` adicionando um campo particular à classe que o valor de propriedade armazenado:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Retornar o valor da `pval` da propriedade de acessador get.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Defina o valor de `pval` na propriedade de acessador set.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  Concluir a definição de `Method1` adicionando o código a seguir.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Para testar a implementação da interface
  
1.  Clique com botão direito do formulário de inicialização para seu projeto na **Gerenciador de soluções**e clique em **Exibir código**. O editor exibe a classe para seu formulário de inicialização. Por padrão, o formulário de inicialização é chamado `Form1`.  
  
2.  Adicione o seguinte `testInstance` campo para o `Form1` classe:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Declarando `testInstance` como `WithEvents`, o `Form1` classe pode manipular seus eventos.  
  
3.  Adicione o seguinte manipulador de eventos para o `Form1` classe para manipular eventos acionados por `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  Adicionar uma sub-rotina chamada `Test` para o `Form1` classe para testar a classe de implementação:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     O `Test` procedimento cria uma instância da classe que implementa `MyInterface`, atribui a essa instância para o `testInstance` define uma propriedade de campo e executa um método por meio da interface.  
  
5.  Adicione código para chamar o `Test` procedimento do `Form1 Load` procedimento do seu formulário de inicialização:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  Execute o `Test` procedimento pressionando F5. A mensagem "Prop1 foi definida para 9" é exibida. Depois de clicar em Okey, a mensagem "o parâmetro X Method1 é 5" é exibida. Clique em Okey, e a mensagem "o manipulador de eventos detectada o evento" é exibida.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Implements](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Instrução Interface](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Event](../../../../visual-basic/language-reference/statements/event-statement.md)
