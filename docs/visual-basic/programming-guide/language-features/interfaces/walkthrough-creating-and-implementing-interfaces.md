---
title: "Instru&#231;&#245;es passo a passo: criando e implementando interfaces (Visual Basic) | Microsoft Docs"
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
  - "implementação de interface, passo a passo"
  - "interfaces, criando"
  - "interfaces, testando"
  - "interfaces, explicações passo a passo"
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: criando e implementando interfaces (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Interfaces descrevem as características das propriedades, métodos e eventos, mas deixe os detalhes de implementação para classes ou estruturas.  
  
 Esta explicação passo a passo demonstra como declarar e implementar uma interface.  
  
> [!NOTE]
>  Esta explicação passo a passo não fornece informações sobre como criar uma interface de usuário.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para definir uma interface  
  
1.  Abra um novo projeto de Aplicativo do Windows [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
2.  Adicionar um novo módulo ao projeto clicando em  **Adicionar módulo** sobre o  **projeto** menu.  
  
3.  Nomeie o novo módulo de `Module1.vb` e clique em  **Add**.  O código para o novo módulo é exibido.  
  
4.  Definir uma interface denominada `TestInterface` em `Module1` digitando `Interface TestInterface` entre o `Module` e `End Module` instruções e pressionando ENTER.  O  **Editor de código** recuos de `Interface` palavra\-chave e adiciona um `End Interface` instrução para formar um bloco de código.  
  
5.  Definir uma propriedade, método e evento para a interface, colocando o seguinte código entre o `Interface` e `End Interface` instruções:  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## Implementação  
 Você pode perceber que a sintaxe usada para declarar membros de interface é diferente da sintaxe usada para declarar membros de classe.  Essa diferença reflete o fato de que interfaces não podem conter código de implementação.  
  
#### Para implementar a interface  
  
1.  Adicionar uma classe chamada `ImplementationClass` adicionando a instrução a seguir para `Module1`, após o `End Interface` instrução, mas antes de `End Module` instrução e pressionando ENTER:  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     Se você estiver trabalhando no ambiente de desenvolvimento integrado, o  **Editor de código** fornece uma correspondência `End Class` instrução quando você pressiona ENTER.  
  
2.  Adicione o seguinte `Implements` instrução para `ImplementationClass`, que nomeia a interface de classe implementa:  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     Quando listado separadamente de outros itens na parte superior de uma classe ou estrutura, a `Implements` declaração indica que a classe ou estrutura implementa uma interface.  
  
     Se você estiver trabalhando no ambiente de desenvolvimento integrado, o  **Editor de código** implementa os membros de classe necessários para `TestInterface` quando você pressionar ENTER e ignore a próxima etapa.  
  
3.  Se você não estiver trabalhando dentro do ambiente de desenvolvimento integrado, você deve implementar todos os membros da interface `MyInterface`.  Adicione o seguinte código para `ImplementationClass` para implementar `Event1`, `Method1`, e `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     O `Implements` instrução nomeia a interface e um membro de interface que está sendo implementado.  
  
4.  Conclua a definição de `Prop1` , adicionando um campo privado para a classe armazenado o valor da propriedade:  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     Retornar o valor de `pval` da propriedade acessador get.  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     Definir o valor de `pval` na propriedade definir acessador.  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  Conclua a definição de `Method1` , adicionando o seguinte código.  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### Para testar a implementação da interface  
  
1.  O formulário de inicialização para seu projeto com o botão direito do  **Solution Explorer**e clique em  **Exibir código**.  O editor exibe a classe para o formulário de inicialização.  Por padrão, o formulário de inicialização é chamado `Form1`.  
  
2.  Adicione o seguinte `testInstance` campo para o `Form1` classe:  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     Declarando `testInstance` como `WithEvents`, o `Form1` classe pode manipular seus eventos.  
  
3.  Adiciona manipulador de eventos para o `Form1` classe para manipular eventos gerados por `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  Adicionar um sub\-rotina nomeada `Test` para o `Form1` classe para testar a classe de implementação:  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     O `Test` procedimento cria uma instância da classe que implementa `MyInterface`, atribui essa instância para o `testInstance` campo, define uma propriedade e executa um método por meio da interface.  
  
5.  Adicione código para chamar o `Test` procedimento a partir de `Form1 Load` procedimento do seu formulário de inicialização:  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  Execute o `Test` procedimento pressionando F5.  A mensagem "Prop1 foi definida como 9" é exibida.  Após você clicar em OK, a mensagem "O parâmetro x para Method1 é 5" é exibida.  Clique em OK e a mensagem "O manipulador de eventos pego o evento" é exibida.  
  
## Consulte também  
 [Instrução Implements](../../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Instrução Interface](../../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Event](../../../../visual-basic/language-reference/statements/event-statement.md)