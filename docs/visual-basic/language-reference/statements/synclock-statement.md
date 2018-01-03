---
title: "Instrução SyncLock"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c363b41bb7a409c490a6e07d4a1a4f1bb44c1438
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="synclock-statement"></a>Instrução SyncLock
Obtém um bloqueio exclusivo para um bloco de instruções antes de executar o bloco.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Partes  
 `lockobject`  
 Necessário. Expressão que é avaliada como uma referência de objeto.  
  
 `block`  
 Opcional. Bloco de instruções a serem executadas quando o bloqueio é adquirido.  
  
 `End SyncLock`  
 Encerra um `SyncLock` bloco.  
  
## <a name="remarks"></a>Comentários  
 O `SyncLock` instrução garante que vários threads não executem o bloco de instrução ao mesmo tempo. `SyncLock`impede cada segmento de entrar no bloco até que nenhum outro thread está executando.  
  
 O uso mais comum de `SyncLock` é para proteger dados de serem atualizados por mais de um segmento simultaneamente. Se as instruções que manipulam os dados devem ir até a conclusão sem interrupção, coloque-as em um `SyncLock` bloco.  
  
 Um bloco de instrução protegido por um bloqueio exclusivo às vezes é chamado um *seção crítica*.  
  
## <a name="rules"></a>Regras  
  
-   A ramificação. Você não pode se ramificar em um `SyncLock` bloco de fora do bloco.  
  
-   Valor de objeto de bloqueio. O valor de `lockobject` não pode ser `Nothing`. Você deve criar o objeto de bloqueio antes de você usá-lo em um `SyncLock` instrução.  
  
     Você não pode alterar o valor de `lockobject` durante a execução de um `SyncLock` bloco. O mecanismo requer que o objeto de bloqueio permaneça inalterado.  
  
-   Não é possível usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador em uma `SyncLock` bloco.  
  
## <a name="behavior"></a>Comportamento  
  
-   Mecanismo. Quando um segmento atinge o `SyncLock` instrução, ela avalia o `lockobject` expressão e suspende a execução até que ele adquire um bloqueio exclusivo no objeto retornado pela expressão. Quando outro segmento alcança o `SyncLock` instrução, ele não adquirir um bloqueio até que o primeiro segmento execute o `End SyncLock` instrução.  
  
-   Dados protegidos. Se `lockobject` é um `Shared` variável, o bloqueio exclusivo impede um segmento em qualquer instância da classe de executar o `SyncLock` bloquear enquanto qualquer outro segmento é executá-lo. Isso protege os dados que são compartilhados entre todas as instâncias.  
  
     Se `lockobject` é uma variável de instância (não `Shared`), o bloqueio impede que um thread em execução na instância atual execute o `SyncLock` bloco ao mesmo tempo que outro segmento na mesma instância. Isso protege os dados mantidos pela instância individual.  
  
-   Aquisição e liberação. Um `SyncLock` bloco se comporta como uma `Try...Finally` em que o `Try` bloco adquire um bloqueio exclusivo no `lockobject` e `Finally` bloco solta. Por isso, o `SyncLock` bloco garante a liberação do bloqueio, independentemente de como você sai do bloco. Isso é verdadeiro mesmo no caso de uma exceção sem tratamento.  
  
-   Chamadas de estrutura. O `SyncLock` bloco adquire e libera o bloqueio exclusivo chamando o `Enter` e `Exit` métodos do `Monitor` classe no <xref:System.Threading> namespace.  
  
## <a name="programming-practices"></a>Práticas recomendadas de programação  
 O `lockobject` expressão sempre deve ser avaliada como um objeto que pertence à sua classe exclusivamente. Você deve declarar um `Private` variável de objeto para proteger dados pertencentes à instância atual, ou um `Private Shared` variável de objeto para proteger dados comuns a todas as instâncias.  
  
 Você não deve usar o `Me` palavra-chave para fornecer um bloqueio de dados do objeto para a instância. Se o código externo à sua classe tem uma referência a uma instância de sua classe, ele poderia usar essa referência como um objeto de bloqueio para um `SyncLock` bloco completamente diferente do seu, protegendo dados diferentes. Dessa forma, sua classe e a outra classe podem impedir entre si de executar suas relacionados `SyncLock` blocos. Da mesma forma, o bloqueio em uma cadeia de caracteres pode ser problemático porque qualquer outro código no processo usando a mesma cadeia de caracteres irá compartilhar o mesmo bloqueio.  
  
 Você também não deve usar o `Me.GetType` compartilhado de método para fornecer um objeto de bloqueio para dados. Isso ocorre porque `GetType` sempre retorna o mesmo `Type` objeto para um determinado nome de classe. Código externo poderia chamar `GetType` em sua classe e obter o mesmo objeto de bloqueio que você está usando. Isso resulta em duas classes de bloqueio do seu `SyncLock` blocos.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma classe que mantém uma lista simple de mensagens. Ele armazena as mensagens em uma matriz e o último elemento dessa matriz usado em uma variável. O `addAnotherMessage` procedimento incrementa o último elemento e armazena a nova mensagem. Essas duas operações são protegidas pelo `SyncLock` e `End SyncLock` instruções, porque depois que o último elemento foi incrementado, a nova mensagem deve ser armazenada antes que qualquer outro segmento possa incrementar o último elemento novamente.  
  
 Se o `simpleMessageList` classe compartilhado de uma lista de mensagens entre todas as instâncias, as variáveis `messagesList` e `messagesLast` deve ser declarado como `Shared`. Nesse caso, a variável `messagesLock` também deve ser `Shared`, para que haja um único objeto de bloqueio usado por cada instância.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir usa threads e `SyncLock`. Enquanto o `SyncLock` instrução estiver presente, o bloco de instrução é uma seção crítica e `balance` nunca se torne um número negativo. Você pode comentar o `SyncLock` e `End SyncLock` instruções para ver o efeito de omitindo o `SyncLock` palavra-chave.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [Sincronização de Thread ](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [Threading](../../programming-guide/concepts/threading/index.md)
