---
title: Instrução SyncLock (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 6f5a89ebe359ca2fdae1d5545192dc2dcecca6a2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401369"
---
# <a name="synclock-statement"></a>Instrução SyncLock
Adquire um bloqueio exclusivo para um bloco de instrução antes de executar o bloco.  
  
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
 Opcional. Bloco de instruções que estão ser executado quando o bloqueio é adquirido.  
  
 `End SyncLock`  
 Encerra um `SyncLock` bloco.  
  
## <a name="remarks"></a>Comentários  
 O `SyncLock` instrução garante que vários threads não executem o bloco de instrução ao mesmo tempo. `SyncLock` impede que cada thread de entrar no bloco até que nenhum outro thread está executando.  
  
 O uso mais comum de `SyncLock` é para proteger os dados sejam atualizados por mais de um thread simultaneamente. Se as instruções que manipulam os dados devem ir até a conclusão sem interrupção, coloque-os dentro de um `SyncLock` bloco.  
  
 Um bloco de instrução protegido por um bloqueio exclusivo é chamado, às vezes, uma *seção crítica*.  
  
## <a name="rules"></a>Regras  
  
-   A ramificação. Você não pode ramificar em uma `SyncLock` bloquear de fora do bloco.  
  
-   Valor do objeto de bloqueio. O valor de `lockobject` não pode ser `Nothing`. Você deve criar o objeto de bloqueio antes de você usá-lo em um `SyncLock` instrução.  
  
     Você não pode alterar o valor de `lockobject` durante a execução de um `SyncLock` bloco. O mecanismo requer que o objeto de bloqueio permaneça inalterado.  
  
-   Não é possível usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador em uma `SyncLock` bloco.  
  
## <a name="behavior"></a>Comportamento  
  
-   Mecanismo. Quando um segmento atinge a `SyncLock` instrução, ele avalia o `lockobject` expressão e suspende a execução até que ele adquire um bloqueio exclusivo no objeto retornado pela expressão. Quando outro thread atinge a `SyncLock` instrução, ele não adquirir um bloqueio até que o primeiro thread executa o `End SyncLock` instrução.  
  
-   Dados protegidos. Se `lockobject` é um `Shared` variável, o bloqueio exclusivo impede um segmento em qualquer instância da classe de executar o `SyncLock` bloquear enquanto ele está em execução por qualquer outro thread. Isso protege os dados que são compartilhados entre todas as instâncias.  
  
     Se `lockobject` é uma variável de instância (não `Shared`), o bloqueio impede que um thread em execução na instância atual da execução de `SyncLock` bloco ao mesmo tempo que outro segmento na mesma instância. Isso protege os dados mantidos pela instância individual.  
  
-   Aquisição e liberação. Um `SyncLock` bloco se comporta como uma `Try...Finally` construção na qual o `Try` bloco adquire um bloqueio exclusivo na `lockobject` e o `Finally` bloco o libera. Por isso, o `SyncLock` bloco garante a liberação do bloqueio, não importa como você sai do bloco. Isso é verdadeiro mesmo no caso de uma exceção sem tratamento.  
  
-   Chamadas de estrutura. O `SyncLock` bloco adquire e libera o bloqueio exclusivo chamando o `Enter` e `Exit` métodos da `Monitor` classe o <xref:System.Threading> namespace.  
  
## <a name="programming-practices"></a>Práticas recomendadas de programação  
 O `lockobject` expressão sempre deve ser avaliada como um objeto que pertence à sua classe exclusivamente. Você deve declarar uma `Private` variável de objeto para proteger dados pertencentes à instância atual, ou um `Private Shared` variável de objeto para proteger dados comuns a todas as instâncias.  
  
 Você não deve usar o `Me` palavra-chave para fornecer um bloqueio de objeto, por exemplo, dados. Se o código externo à sua classe tem uma referência a uma instância de sua classe, eles podem usar essa referência como um objeto de bloqueio para um `SyncLock` bloco completamente diferente do seu, protegendo dados diferentes. Dessa forma, sua classe e a outra classe poderia bloquear uns aos outros de executar seus relacionada `SyncLock` blocos. Da mesma forma, o bloqueio em uma cadeia de caracteres pode ser problemático porque qualquer outro código no processo usando a mesma cadeia de caracteres irá compartilhar o mesmo bloqueio.  
  
 Você também não deve usar o `Me.GetType` compartilhado de método para fornecer um objeto de bloqueio para dados. Isso ocorre porque `GetType` sempre retorna o mesmo `Type` objeto para um determinado nome de classe. Código externo poderia chamar `GetType` em sua classe e obter o mesmo objeto de bloqueio que você está usando. Isso resultaria em duas classes impedindo uns aos outros de seus `SyncLock` blocos.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma classe que mantém uma lista simple de mensagens. Ele armazena as mensagens em uma matriz e o último elemento da matriz de usado em uma variável. O `addAnotherMessage` procedimento incrementa o último elemento e armazena a nova mensagem. Essas duas operações são protegidas pela `SyncLock` e `End SyncLock` instruções, porque depois que o último elemento foi incrementado, a nova mensagem deve ser armazenada antes que qualquer outro thread pode incrementar o último elemento novamente.  
  
 Se o `simpleMessageList` classe compartilhada de uma lista de mensagens entre todas as suas instâncias, as variáveis `messagesList` e `messagesLast` deve ser declarado como `Shared`. Nesse caso, a variável `messagesLock` também deve ser `Shared`, de modo que seria um único objeto de bloqueio usado por cada instância.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir usa threads e `SyncLock`. Desde que o `SyncLock` declaração estiver presente, o bloco de instrução é uma seção crítica e `balance` nunca se torna um número negativo. Você pode comentar a `SyncLock` e `End SyncLock` instruções para ver o efeito de omitindo o `SyncLock` palavra-chave.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [Sincronização de Thread ](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [Threading](../../programming-guide/concepts/threading/index.md)
