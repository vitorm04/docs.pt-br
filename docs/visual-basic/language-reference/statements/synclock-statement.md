---
title: "Instru&#231;&#227;o SyncLock | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.SyncLock"
  - "SyncLock"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "bloqueios, threads"
  - "Instrução SyncLock"
  - "threading [Visual Basic], bloqueios"
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o SyncLock
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Obtém um bloqueio exclusivo para um bloco de declaração antes de executar o bloco.  
  
## Sintaxe  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## Partes  
 `lockobject`  
 Obrigatório.  Expressão que avalia como uma referência de objeto.  
  
 `block`  
 Opcional.  Bloco de instruções a serem executadas quando o bloqueio é adquirido.  
  
 `End SyncLock`  
 Finaliza um bloco `SyncLock`.  
  
## Comentários  
 A declaração de `SyncLock` garante que vários segmentos não executem o bloco de declaração ao mesmo tempo.  `SyncLock` impede cada segmento insira o bloco até que nenhum outro segmento o executar.  
  
 O uso mais comum de `SyncLock` é para proteger dados de serem atualizados por mais de um segmento simultaneamente.  Se as instruções que manipulam os dados devem ir para a conclusão sem interrupção, coloque\-as dentro de um bloco `SyncLock`.  
  
 Um bloco de declaração protegido por um bloqueio exclusivo às vezes é chamado de *seção crítica*.  
  
## Regras.  
  
-   Ramificação.  Você não pode ramificar em um bloco `SyncLock` de fora do bloco.  
  
-   Bloquear Valor do Objeto.  O valor de `lockobject` não pode ser `Nothing`.  Você deve criar o objeto de bloqueio antes de usá\-lo em uma instrução `SyncLock`.  
  
     Não é possível alterar o valor de `lockobject` durante a execução de um bloco `SyncLock`.  O mecanismo requer que o objeto de bloqueio permaneça inalterado.  
  
-   Você não pode usar o operador de [espere](../../../visual-basic/language-reference/operators/await-operator.md) em um bloco de `SyncLock` .  
  
## Comportamento  
  
-   Mecanismo.  Quando um segmento atinge a instrução `SyncLock`, ele avalia a expressão `lockobject` e suspende a execução até que ele obtenha um bloqueio exclusivo no objeto retornado pela expressão.  Quando outro segmento alcança a instrução `SyncLock`, ele não consegue um bloqueio até que o primeiro segmento execute a instrução `End SyncLock`.  
  
-   Dados protegidos.  Se `lockobject` for uma variável `Shared`, o bloqueio exclusivo impede um segmento em qualquer instância da classe de executar o bloco `SyncLock` enquanto qualquer outro segmento o estiver executando.  Isso protege os dados que são compartilhados entre todas as instâncias.  
  
     Se `lockobject` é uma instância de variável \(não `Shared`\), o bloqueio impede que um segmento em execução na instância atual execute o bloco `SyncLock` ao mesmo tempo que outro segmento na mesma instância.  Isso protege os dados mantidos pela instância individual.  
  
-   Obtenção e liberação.  Um bloco `SyncLock` se comporta como uma construção `Try...Finally` na qual o bloco `Try` obtém um bloqueio exclusivo no `lockobject` e o bloco `Finally` o libera.  Devido a isso, o bloco `SyncLock` garante a liberação do bloqueio, não importando como você sai do bloco.  Isto é verdadeiro mesmo no caso de uma exceção não manipulada.  
  
-   Chamadas de Estrutura.  O bloco `SyncLock` obtém e libera o bloqueio exclusivo chamando os métodos `Enter` e `Exit` da classe `Monitor` no namespace <xref:System.Threading>.  
  
## Práticas de programação  
 A expressão `lockobject` sempre deve avaliar a um objeto que pertence à sua classe exclusivamente.  Você deve declarar uma variável de objeto `Private` para proteger dados pertencentes à instância atual, ou uma variável de objeto `Private Shared` para proteger dados comuns a todas as instâncias.  
  
 Você não deve usar a palavra\-chave `Me` para fornecer um objeto de bloqueio para dados da instância.  Se códigos externos a sua classe têm uma referência a uma instância de sua classe, eles podem usar essa referência como um objeto de bloqueio para um bloco `SyncLock` bloco completamente diferente do seu, protegendo dados diferentes.  Dessa maneira, sua classe e a outra classe podem impedir ma a outra de executar seus blocos `SyncLock` não relacionados.  Da mesma forma, o bloqueio em uma cadeia de caracteres pode ser problemático porque qualquer outro código no processo usando a mesma cadeia de caracteres irá compartilhar o mesmo bloqueio.  
  
 Você também não deve usar o método `Me.GetType` para fornecer um objeto de bloqueio para dados compartilhados.  Isso ocorre porque `GetType` sempre retorna o mesmo objeto `Type` para um determinado nome de classe.  O código externo pode chamar `GetType` em sua classe e obter o mesmo objeto de bloqueio que você está usando.  Isso resultaria nas duas classes impedindo uma a outra de acessar seus blocos `SyncLock`.  
  
## Exemplos  
  
### Descrição  
 O exemplo a seguir mostra uma classe que mantém uma lista simples de mensagens.  Ela armazena as mensagens em uma matriz e o último elemento usado da matriz em uma variável.  O procedimento `addAnotherMessage` incrementa o último elemento e armazena a nova mensagem.  Essas duas operações são protegidas pelas instruções `SyncLock` e `End SyncLock`, porque depois que o último elemento foi incrementado, a nova mensagem deve ser armazenada antes que qualquer outro segmento possa incrementar o último elemento novamente.  
  
 Se a classe de `simpleMessageList` uma lista de mensagens compartilhado entre todas as instâncias, variáveis `messagesList` e `messagesLast` seriam declaradas como `Shared`.  Nesse caso, a variável `messagesLock` também deve ser `Shared`, para que haja um único objeto de bloqueio usado por cada instância.  
  
### Código  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### Descrição  
 O exemplo a seguir usa segmentos e `SyncLock`.  Como a instrução de `SyncLock` estiverem presentes, o bloco de declaração é uma seção crítica e `balance` nunca torna\-se um número negativo.  Você pode comentário para fora as instruções de `SyncLock` e de `End SyncLock` para ver o efeito de deixar sem a palavra\-chave de `SyncLock` .  
  
### Código  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### Comentários  
  
## Consulte também  
 <xref:System.Threading>   
 <xref:System.Threading.Monitor>   
 [Sincronização de thread](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)   
 [Threading](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)