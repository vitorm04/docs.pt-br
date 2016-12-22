---
title: "Instru&#231;&#245;es passo a passo: definindo classes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "módulos de classe, explicações passo a passo"
  - "classes [Visual Basic], explicações passo a passo"
  - "código, saindo"
  - "execução, terminando"
  - "execução, parando"
  - "Arquivos , fechamento"
  - "Evento Initialize"
  - "objetos [Visual Basic], criando"
  - "objetos [Visual Basic], inicializando"
  - "encerramento do programa"
  - "programas, saindo"
  - "Evento Terminate"
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: definindo classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Essa explicação passo a passo demonstra como definir classes, que você pode usar para criar objetos.  Ele também mostra como adicionar propriedades e métodos à nova classe e demonstra como inicializar um objeto.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para definir uma classe  
  
1.  Crie um projeto, clicando em **Novo Projeto** no menu **Arquivo**.  A caixa de diálogo **New Project** será exibida.  
  
2.  Selecione aplicativos do Windows na lista de modelos de projetos [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para exibir o novo projeto.  
  
3.  Adicione uma nova classe ao projeto, clicando em **Adicionar Classe** no menu de **Projeto**.  O  **Add New Item** caixa de diálogo aparece.  
  
4.  Selecione o modelo **Classe**.  
  
5.  Nomeie a nova classe `UserNameInfo.vb` e, em seguida, clique em **Adicionar** para exibir o código para a nova classe.  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Você pode usar o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Editor de Códigos** para adicionar uma classe ao seu formulário de inicialização, digitando a palavra\-chave `Class` seguida do nome da nova classe.  O **Editor de Códigos** fornece uma instrução `End Class` correspondente para você.  
  
6.  Defina um campo particular para a classe adicionando o seguinte código entre as instruções `Class` e `End Class`:  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Declarar o campo como `Private` significa que ele pode ser usado somente dentro da classe.  Você pode disponibilizar campos de fora de uma classe usando modificadores de acesso, como `Public`, que fornecem mias acesso.  Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Defina uma propriedade para a classe adicionando o seguinte código:  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Defina um método para a classe adicionando o seguinte código:  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Defina um construtor com parâmetros para a nova classe adicionando um procedimento denominado `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     O construtor `Sub New` é chamado automaticamente quando um objeto baseado nessa classe é criado.  Esse construtor define o valor do campo que contém o nome de usuário.  
  
### Para criar um botão para testar a classe  
  
1.  Altere o formulário de inicialização para o modo de design clicando com o botão direito em seu nome no **Gerenciador de Soluções** e, em seguida, clicando em **Designer de Modo de Exibição**.  Por padrão, o formulário de inicialização para projetos de aplicativos Windows é chamado Form1.vb.  O formulário principal, em seguida, será exibido.  
  
2.  Adicione um botão ao formulário principal e clique duas vezes nele para exibir o código para o manipulador de eventos `Button1_Click`.  Adicione o seguinte código para chamar o procedimento de teste:  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### Para executar seu aplicativo  
  
1.  Execute o aplicativo pressionando F5.  Clique no botão do formulário para chamar o procedimento de teste.  Ele exibe uma mensagem informando que o `UserName` original é "MOORE, BOBBY", porque o procedimento chama o método `Capitalize` do objeto.  
  
2.  Clique **OK** para descartar a caixa de mensagem.  O procedimento `Button1 Click` altera o valor da propriedade `UserName` e exibe uma mensagem informando que o novo valor de `UserName` é "Worden, Joe".  
  
## Consulte também  
 [Programação orientada a objeto](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)