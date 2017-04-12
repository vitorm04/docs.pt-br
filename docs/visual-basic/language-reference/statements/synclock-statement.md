---
title: "Instrução SyncLock | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
dev_langs:
- VB
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: 17
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
ms.openlocfilehash: 58189f5cc216c2a7c044e6133057a51b3a97c75c
ms.lasthandoff: 03/13/2017

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
 Finaliza uma `SyncLock` bloco.  
  
## <a name="remarks"></a>Comentários  
 O `SyncLock` instrução garante que vários segmentos não executem o bloco de declaração ao mesmo tempo. `SyncLock`impede cada segmento de entrar no bloco até que nenhum outro segmento está executando.  
  
 O uso mais comum de `SyncLock` é para proteger dados de serem atualizados por mais de um segmento simultaneamente. Se as instruções que manipulam os dados devem ir até a conclusão sem interrupção, colocá-los dentro de um `SyncLock` bloco.  
  
 Um bloco de declaração protegido por um bloqueio exclusivo às vezes é chamado um *seção crítica*.  
  
## <a name="rules"></a>Regras  
  
-   A ramificação. Você não pode ramificar em um `SyncLock` bloco de fora do bloco.  
  
-   Valor de objeto de bloqueio. O valor de `lockobject` não pode ser `Nothing`. Você deve criar o objeto de bloqueio antes de você usá-lo em um `SyncLock` instrução.  
  
     Você não pode alterar o valor de `lockobject` durante a execução de um `SyncLock` bloco. O mecanismo requer que o objeto de bloqueio permaneça inalterado.  
  
-   Não é possível usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador em uma `SyncLock` bloco.  
  
## <a name="behavior"></a>Comportamento  
  
-   Mecanismo. Quando um segmento atinge o `SyncLock` instrução, ele avalia o `lockobject` expressão e suspende a execução até que ele obtenha um bloqueio exclusivo no objeto retornado pela expressão. Quando outro segmento alcança o `SyncLock` instrução, ele não consegue um bloqueio até que o primeiro segmento execute a `End SyncLock` instrução.  
  
-   Dados protegidos. Se `lockobject` é um `Shared` variável, o bloqueio exclusivo impede um segmento em qualquer instância da classe de executar o `SyncLock` bloquear enquanto qualquer outro segmento o estiver executando. Isso protege os dados que são compartilhados entre todas as instâncias.  
  
     Se `lockobject` é uma variável de instância (não `Shared`), o bloqueio impede que um thread em execução na instância atual execute o `SyncLock` bloco ao mesmo tempo que outro segmento na mesma instância. Isso protege os dados mantidos pela instância individual.  
  
-   Aquisição e liberação. A `SyncLock` bloco se comporta como um `Try...Finally` em que o `Try` bloco adquire um bloqueio exclusivo no `lockobject` e `Finally` bloco libera. Por isso, o `SyncLock` bloco garante a liberação do bloqueio, não importa como você sai do bloco. Isso é verdadeiro mesmo no caso de uma exceção não tratada.  
  
-   Chamadas de estrutura. O `SyncLock` bloco adquire e libera o bloqueio exclusivo chamando o `Enter` e `Exit` métodos do `Monitor` classe o <xref:System.Threading>namespace.</xref:System.Threading>  
  
## <a name="programming-practices"></a>Práticas de programação  
 O `lockobject` expressão sempre deve avaliar a um objeto que pertence à sua classe exclusivamente. Você deve declarar uma `Private` variável de objeto para proteger dados pertencentes à instância atual, ou um `Private Shared` variável de objeto para proteger dados comuns a todas as instâncias.  
  
 Você não deve usar o `Me` palavra-chave para fornecer um bloqueio de objeto, por exemplo, dados. Se o código externo à sua classe tem uma referência a uma instância de sua classe, eles podem usar essa referência como um objeto de bloqueio para um `SyncLock` bloco completamente diferente do seu, protegendo dados diferentes. Dessa maneira, sua classe e a outra classe podem impedir entre si de executar seus relacionado `SyncLock` blocos. Da mesma forma, o bloqueio em uma cadeia de caracteres pode ser problemático porque qualquer outro código no processo usando a mesma cadeia de caracteres irá compartilhar o mesmo bloqueio.  
  
 Você também não deve usar o `Me.GetType` método para fornecer um objeto de bloqueio para dados compartilhados. Isso ocorre porque `GetType` sempre retorna a mesma `Type` objeto para um determinado nome de classe. O código externo pode chamar `GetType` em sua classe e obter o mesmo objeto de bloqueio que você está usando. Isso resultaria nas duas classes impedindo uma a outra de suas `SyncLock` blocos.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma classe que mantém uma lista simple de mensagens. Ela armazena as mensagens em uma matriz e o último elemento da matriz usado em uma variável. O `addAnotherMessage` procedimento incrementa o último elemento e armazena a nova mensagem. Essas duas operações são protegidas pelo `SyncLock` e `End SyncLock` instruções, porque depois que o último elemento foi incrementado, a nova mensagem deve ser armazenada antes que qualquer outro segmento possa incrementar o último elemento novamente.  
  
 Se o `simpleMessageList` classe compartilhados uma lista de mensagens entre todas as suas instâncias, as variáveis `messagesList` e `messagesLast` deve ser declarado como `Shared`. Nesse caso, a variável `messagesLock` também deve ser `Shared`, para que haja um único objeto de bloqueio usado por cada instância.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading n º&1;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir usa threads e `SyncLock`. Enquanto o `SyncLock` declaração estiver presente, o bloco de instrução é uma seção crítica e `balance` nunca se torne um número negativo. Você pode comentar o `SyncLock` e `End SyncLock` instruções para ver o efeito de omitindo o `SyncLock` palavra-chave.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading&#21;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.Monitor></xref:System.Threading.Monitor>   
 [Sincronização de thread](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)   
 [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)
