---
title: Definindo Classes (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Instruções passo a passo: definindo classes (Visual Basic)
Este passo a passo demonstra como definir classes, que você pode usar para criar objetos. Ele também mostra como adicionar propriedades e métodos para a nova classe e demonstra como inicializar um objeto.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a>Para definir uma classe  
  
1.  Criar um projeto, clicando em **novo projeto** no **arquivo** menu. A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Selecione o aplicativo do Windows na lista de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] modelos para exibir o novo projeto do projeto.  
  
3.  Adicionar uma nova classe ao projeto clicando **Adicionar classe** no **projeto** menu. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
4.  Selecione o **classe** modelo.  
  
5.  Nomeie a nova classe `UserNameInfo.vb`e, em seguida, clique em **adicionar** para exibir o código para a nova classe.  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Você pode usar o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Editor de códigos** para adicionar uma classe ao seu formulário de inicialização, digitando o `Class` palavra-chave seguido do nome da nova classe. O **Editor de códigos** fornece correspondente `End Class` instrução para você.  
  
6.  Defina um campo particular para a classe adicionando o seguinte código entre as `Class` e `End Class` instruções:  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Declarar o campo como `Private` significa que ele pode ser usado somente dentro da classe. Você pode disponibilizar campos de fora de uma classe usando modificadores de acesso, como `Public` que fornecem mais acesso. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Defina uma propriedade para a classe adicionando o código a seguir:  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Defina um método para a classe adicionando o seguinte código:  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Definir um construtor com parâmetros para a nova classe adicionando um procedimento denominado `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     O `Sub New` construtor é chamado automaticamente quando um objeto com base nessa classe é criado. Este construtor define o valor do campo que contém o nome de usuário.  
  
### <a name="to-create-a-button-to-test-the-class"></a>Para criar um botão para testar a classe  
  
1.  Alterar o formulário de inicialização para o modo de design clicando com o seu nome na **Solution Explorer** e, em seguida, clicando em **Designer de exibição**. Por padrão, o formulário de inicialização para projetos de aplicativo do Windows é chamado Form1. vb. Formulário principal será exibida.  
  
2.  Adicione um botão ao formulário principal e clique duas vezes nele para exibir o código para o `Button1_Click` manipulador de eventos. Adicione o seguinte código para chamar o procedimento de teste:  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>Executar seu aplicativo  
  
1.  Execute o aplicativo pressionando F5. Clique no botão no formulário para chamar o procedimento de teste. Ele exibe uma mensagem informando que o original `UserName` é "MOORE, BOBBY", porque o procedimento chama o `Capitalize` método do objeto.  
  
2.  Clique em **Okey** para fechar a caixa de mensagem. O `Button1 Click` procedimento altera o valor da `UserName` propriedade e exibe uma mensagem informando que o novo valor de `UserName` é "Worden, Joe".  
  
## <a name="see-also"></a>Consulte também  
 [Programação Orientada a Objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
