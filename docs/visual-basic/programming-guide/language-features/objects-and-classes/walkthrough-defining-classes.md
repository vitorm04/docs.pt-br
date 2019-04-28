---
title: Definindo Classes (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: 3129824f6e4047420c422503cc366a1c8d28b7e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61865282"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Passo a passo: Definindo Classes (Visual Basic)

Este passo a passo demonstra como definir classes, que você pode usar para criar objetos. Ele também mostra como adicionar propriedades e métodos para a nova classe e demonstra como inicializar um objeto.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Para definir uma classe
  
1. Criar um projeto, clicando em **novo projeto** sobre o **arquivo** menu. A caixa de diálogo **Novo Projeto** é exibida.  
  
2. Selecione o aplicativo do Windows na lista de modelos de projeto do Visual Basic para exibir o novo projeto.  
  
3. Adicione uma nova classe ao projeto clicando **Adicionar classe** sobre o **projeto** menu. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
4. Selecione o **classe** modelo.  
  
5. Nomeie a nova classe `UserNameInfo.vb`e, em seguida, clique em **Add** para exibir o código para a nova classe.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Você pode usar o Visual Basic **Editor de códigos** para adicionar uma classe ao seu formulário de inicialização, digitando o `Class` seguido do nome da nova classe de palavra-chave. O **Editor de códigos** fornece um correspondente `End Class` instrução para você.  
  
6. Defina um campo particular para a classe adicionando o seguinte código entre o `Class` e `End Class` instruções:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Declarar o campo como `Private` significa que ele pode ser usado somente dentro da classe. Você pode disponibilizar campos de fora de uma classe usando os modificadores de acesso, como `Public` que fornecem mais acesso. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Defina uma propriedade para a classe adicionando o seguinte código:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Defina um método para a classe adicionando o seguinte código:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Definir um construtor com parâmetros para a nova classe adicionando um procedimento denominado `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     O `Sub New` construtor é chamado automaticamente quando um objeto com base nessa classe é criado. Este construtor define o valor do campo que contém o nome de usuário.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Para criar um botão para testar a classe
  
1. Alterar o formulário de inicialização para o modo de design clicando com o seu nome na **Gerenciador de soluções** e, em seguida, clicando em **View Designer**. Por padrão, o formulário de inicialização para projetos de aplicativos do Windows chamado Form1.vb. O formulário principal, em seguida, será exibida.  
  
2. Adicione um botão ao formulário principal e clique duas vezes nele para exibir o código para o `Button1_Click` manipulador de eventos. Adicione o seguinte código para chamar o procedimento de teste:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Executar seu aplicativo
  
1. Execute o aplicativo pressionando F5. Clique no botão no formulário para chamar o procedimento de teste. Ele exibe uma mensagem informando que o original `UserName` é "MOORE, BOBBY", porque o procedimento chama o `Capitalize` método do objeto.  
  
2. Clique em **OK** para descartar a caixa de mensagem. O `Button1 Click` procedimento altera o valor da `UserName` propriedade e exibe uma mensagem informando que o novo valor de `UserName` é "Worden, Joe".  
  
## <a name="see-also"></a>Consulte também

- [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
