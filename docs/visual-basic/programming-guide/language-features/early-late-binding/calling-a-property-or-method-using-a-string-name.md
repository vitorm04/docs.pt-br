---
title: "Chamando uma propriedade ou um m&#233;todo usando o nome de uma cadeia de caracteres (Visual Basic) | Microsoft Docs"
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
  - "Função CallByName"
  - "chamando métodos, nomes de cadeia de caracteres"
  - "chamadas de método, cadeias de caracteres"
  - "métodos [Visual Basic], chamando com nomes de cadeia de caracteres"
  - "objetos [Visual Basic], configurando propriedades"
  - "transmitindo os operadores"
  - "propriedades [Visual Basic], definindo em tempo de execução"
  - "configurando propriedades, propriedades do objeto em tempo de execução"
  - "cadeias de caracteres {Visual Basic], transmitindo novos operadores como"
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Chamando uma propriedade ou um m&#233;todo usando o nome de uma cadeia de caracteres (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Na maioria dos casos, você pode descobrir as propriedades e métodos de um objeto em tempo de design e gravar código para manipulá\-los.  No entanto, em alguns casos você pode não saber sobre propriedades e métodos de um objeto com antecedência, ou você pode apenas querer a flexibilidade de ativar um usuário final para especificar propriedades ou executar métodos em tempo de execução.  
  
## Função CallByName  
 Considere, por exemplo, um aplicativo cliente que avalia as expressões inseridas pelo usuário, passando um operador para um componente COM.  Suponha que você está constantemente adicionando novas funções ao componente que exigem novos operadores.  Quando você usa técnicas de acesso padrão de objeto, você deve recompilar e redistribuir o aplicativo cliente antes ele pudesse usar os novos operadores.  Para evitar isso, você pode usar a função `CallByName` para passar os novos operadores como sequências de caracteres, sem alterar o aplicativo.  
  
 A função `CallByName` permite que você use uma sequência de caracteres para especificar uma propriedade ou método no tempo de execução.  A assinatura para a função `CallByName` possui aparência como esta:  
  
 *Resultado*  \= `CallByName` \(  *Objeto*  *NomedoProcedimento*   *Tipode Chamada* ,  *Argumentos*  \(\)\)  
  
 O primeiro argumento, *Objeto*, leva o nome do objeto em que você deseja atuar.  O argumento *ProcedureName* leva uma sequência de caracteres que contém o nome do método ou procedimento de propriedade a ser chamado.  O argumento *TipodeChamada* leva uma constante que representa o tipo de procedimento para chamar: um método \(`Microsoft.VisualBasic.CallType.Method`\), uma propriedade leitura \(`Microsoft.VisualBasic.CallType.Get`\) ou um conjunto de propriedades \(`Microsoft.VisualBasic.CallType.Set`\).  O argumento *Argumentos*, que é opcional, leva uma matriz do tipo `Object` que contém quaisquer argumentos para o procedimento.  
  
 Você pode usar `CallByName` com classes em sua solução atual, mas ele é mais frequentemente usado para acessar objetos COM ou de assemblies [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] .  
  
 Suponha que você adicione uma referência a um assembly que contém uma classe denominada `MathClass`, a qual possui uma nova função chamada `SquareRoot`, conforme mostrado no código o seguir:  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Seu aplicativo pode usar controles caixa de texto para controlar qual método será chamado e seus argumentos.  Por exemplo, se `TextBox1` contém a expressão a ser avaliada, e `TextBox2` for usado para digitar o nome da função, você pode usar o código a seguir para chamar a função `SquareRoot` na expressão em `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 Se você inserir "64" no `TextBox1`,"SquareRoot" no `TextBox2` e em seguida chamar o procedimento `CallMath`, a raiz quadrada do número em `TextBox1` é avaliada.  O código no exemplo chama a função `SquareRoot` \(que usa uma sequência de caracteres que contém a expressão a ser avaliada como um argumento necessário\) e retorna "8" em `TextBox1` \(a raiz quadrada de 64\).  Obviamente, se o usuário inserir uma sequência inválida na `TextBox2`, se a sequência contiver o nome de uma propriedade em vez de um método, ou se o método teve um argumento adicional necessário, ocorrerá um erro de tempo de execução.  Você precisa adicionar o código de tratamento de erros robusto ao usar `CallByName` para prever essas ou quaisquer outros erros.  
  
> [!NOTE]
>  Enquanto a função `CallByName` pode ser útil em alguns casos, você deve avaliar sua utilidade contra as implicações de desempenho — usando `CallByName` para chamar um procedimento é um pouco mais lento do que uma chamada recém\-vinculada.  Se você estiver chamando uma função que é chamada repetidamente, como como em um loop, `CallByName` pode ter um grave efeito no desempenho.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [Determinando o tipo de objeto](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)