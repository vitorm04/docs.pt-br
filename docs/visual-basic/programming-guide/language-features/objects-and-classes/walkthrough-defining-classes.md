---
title: Definindo Classes (Visual Basic) | Documentos do Microsoft
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
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
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
ms.openlocfilehash: aeaa5c2bb85c1a642da15c6a29546cf065380e27
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a>Instruções passo a passo: definindo classes (Visual Basic)
Este passo a passo demonstra como definir classes, que você pode usar para criar objetos. Ele também mostra como adicionar propriedades e métodos para a nova classe e demonstra como inicializar um objeto.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a>Para definir uma classe  
  
1.  Criar um projeto, clicando em **novo projeto** sobre o **arquivo** menu. A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Selecione o aplicativo do Windows na lista de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modelos para exibir o novo projeto de projeto.  
  
3.  Adicione uma nova classe ao projeto, clicando em **Add Class** sobre o **projeto** menu. O **Adicionar Novo Item** caixa de diálogo é exibida.  
  
4.  Selecione o **classe** modelo.  
  
5.  Nomeie a nova classe `UserNameInfo.vb`e, em seguida, clique em **adicionar** para exibir o código para a nova classe.  
  
     [!code-vb[VbVbalrOOP n º&5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Você pode usar o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Editor de códigos** para adicionar uma classe ao seu formulário de inicialização, digitando a `Class` palavra-chave seguido do nome da nova classe. O **Editor de códigos** fornece um correspondente `End Class` instrução para você.  
  
6.  Defina um campo particular para a classe adicionando o seguinte código entre o `Class` e `End Class` instruções:  
  
     [!code-vb[VbVbalrOOP&#7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Declarar o campo como `Private` significa que ele pode ser usado somente dentro da classe. Você pode disponibilizar campos de fora de uma classe usando modificadores de acesso, como `Public` que fornecem mais acesso. Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Defina uma propriedade para a classe adicionando o seguinte código:  
  
     [!code-vb[VbVbalrOOP n º&8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Defina um método para a classe adicionando o seguinte código:  
  
     [!code-vb[VbVbalrOOP n º&9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Defina um construtor com parâmetros para a nova classe adicionando um procedimento denominado `Sub New`:  
  
     [!code-vb[VbVbalrOOP n º&10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     O `Sub New` construtor é chamado automaticamente quando um objeto baseado nessa classe é criado. Esse construtor define o valor do campo que contém o nome de usuário.  
  
### <a name="to-create-a-button-to-test-the-class"></a>Para criar um botão para testar a classe  
  
1.  Alterar o formulário de inicialização para o modo design clicando em seu nome na **Solution Explorer** e, em seguida, clicando em **View Designer**. Por padrão, o formulário de inicialização para projetos de aplicativos do Windows é chamado Form1. vb. O formulário principal será exibida.  
  
2.  Adicione um botão ao formulário principal e clique duas vezes nele para exibir o código para o `Button1_Click` manipulador de eventos. Adicione o seguinte código para chamar o procedimento de teste:  
  
     [!code-vb[VbVbalrOOP&#12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>Executar seu aplicativo  
  
1.  Execute o aplicativo pressionando F5. Clique no botão no formulário para chamar o procedimento de teste. Exibe uma mensagem informando que o original `UserName` é "MOORE, BOBBY", porque o procedimento chama o `Capitalize` método do objeto.  
  
2.  Clique em **Okey** para descartar a caixa de mensagem. O `Button1 Click` procedimento altera o valor da `UserName` propriedade e exibe uma mensagem informando que o novo valor de `UserName` é "Worden, Joe".  
  
## <a name="see-also"></a>Consulte também  
 [Programação orientada a objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)   
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

