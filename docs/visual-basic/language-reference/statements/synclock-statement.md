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
ms.openlocfilehash: e981ee727b66ecda392014fd3ee8ca6f1526cd2e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578895"
---
# <a name="synclock-statement"></a>Instrução SyncLock
Adquire um bloqueio exclusivo para um bloco de instrução antes de executar o bloco.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Partes  
 `lockobject`  
 Necessário. Expressão que é avaliada como uma referência de objeto.  
  
 `block`  
 Opcional. Bloco de instruções que devem ser executadas quando o bloqueio é adquirido.  
  
 `End SyncLock`  
 Encerra um bloco de `SyncLock`.  
  
## <a name="remarks"></a>Comentários  
 A instrução `SyncLock` garante que vários threads não executem o bloco de instruções ao mesmo tempo. `SyncLock` impede que cada thread entre no bloco até que nenhum outro thread o execute.  
  
 O uso mais comum de `SyncLock` é proteger os dados de serem atualizados por mais de um thread simultaneamente. Se as instruções que manipulam os dados devem ir para conclusão sem interrupção, coloque-as dentro de um bloco de `SyncLock`.  
  
 Um bloco de instruções protegido por um bloqueio exclusivo às vezes é chamado de *seção crítica*.  
  
## <a name="rules"></a>Regras  
  
- Ramificação. Não é possível ramificar em um bloco de `SyncLock` de fora do bloco.  
  
- Bloquear valor do objeto. O valor de `lockobject` não pode ser `Nothing`. Você deve criar o objeto de bloqueio antes de usá-lo em uma instrução `SyncLock`.  
  
     Você não pode alterar o valor de `lockobject` ao executar um bloco de `SyncLock`. O mecanismo requer que o objeto de bloqueio permaneça inalterado.  
  
- Você não pode usar o operador [Await](../../../visual-basic/language-reference/operators/await-operator.md) em um bloco de `SyncLock`.  
  
## <a name="behavior"></a>Comportamento  
  
- Mecanismo. Quando um thread alcança a instrução `SyncLock`, ele avalia a expressão de `lockobject` e suspende a execução até que adquira um bloqueio exclusivo no objeto retornado pela expressão. Quando outro thread alcança a instrução `SyncLock`, ele não adquire um bloqueio até que o primeiro thread execute a instrução `End SyncLock`.  
  
- Dados protegidos. Se `lockobject` for uma variável `Shared`, o bloqueio exclusivo impedirá que um thread em qualquer instância da classe execute o bloco de `SyncLock` enquanto qualquer outro thread estiver executando-o. Isso protege os dados compartilhados entre todas as instâncias.  
  
     Se `lockobject` for uma variável de instância (não `Shared`), o bloqueio impedirá que um thread em execução na instância atual execute o bloco de `SyncLock` ao mesmo tempo que outro thread na mesma instância. Isso protege os dados mantidos pela instância individual.  
  
- Aquisição e versão. Um bloco de `SyncLock` se comporta como uma construção de `Try...Finally` na qual o bloco de `Try` adquire um bloqueio exclusivo em `lockobject` e o bloco de `Finally` o libera. Por isso, o bloqueio de `SyncLock` garante a liberação do bloqueio, independentemente de como você sai do bloco. Isso é verdadeiro mesmo no caso de uma exceção sem tratamento.  
  
- Chamadas à estrutura. O bloco de `SyncLock` adquire e libera o bloqueio exclusivo chamando os métodos `Enter` e `Exit` da classe `Monitor` no namespace <xref:System.Threading>.  
  
## <a name="programming-practices"></a>Práticas de programação  
 A expressão de `lockobject` sempre deve ser avaliada como um objeto que pertence exclusivamente à sua classe. Você deve declarar uma variável de objeto `Private` para proteger os dados pertencentes à instância atual ou uma variável de objeto `Private Shared` para proteger os dados comuns a todas as instâncias.  
  
 Você não deve usar a palavra-chave `Me` para fornecer um objeto de bloqueio para dados de instância. Se o código externo à sua classe tiver uma referência a uma instância da sua classe, ele poderá usar essa referência como um objeto de bloqueio para um bloco de `SyncLock` completamente diferente do seu, protegendo dados diferentes. Dessa forma, sua classe e a outra classe podem impedir que uma da outra execute seus blocos de `SyncLock` não relacionados. De maneira semelhante, o bloqueio em uma cadeia de caracteres pode ser problemático, pois qualquer outro código no processo que usa a mesma cadeia de caracteres compartilhará o mesmo bloqueio.  
  
 Você também não deve usar o método `Me.GetType` para fornecer um objeto de bloqueio para dados compartilhados. Isso ocorre porque `GetType` sempre retorna o mesmo objeto `Type` para um determinado nome de classe. O código externo pode chamar `GetType` em sua classe e obter o mesmo objeto de bloqueio que você está usando. Isso resultaria em duas classes bloqueando-as a partir de seus blocos de `SyncLock`.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma classe que mantém uma lista simples de mensagens. Ele contém as mensagens em uma matriz e o último elemento usado dessa matriz em uma variável. O procedimento `addAnotherMessage` incrementa o último elemento e armazena a nova mensagem. Essas duas operações são protegidas pelas instruções `SyncLock` e `End SyncLock`, porque depois que o último elemento for incrementado, a nova mensagem deverá ser armazenada antes que qualquer outro thread possa incrementar o último elemento novamente.  
  
 Se a classe `simpleMessageList` compartilhada uma lista de mensagens entre todas as suas instâncias, as variáveis `messagesList` e `messagesLast` seriam declaradas como `Shared`. Nesse caso, a variável `messagesLock` também deve ser `Shared`, para que haja um único objeto de bloqueio usado por cada instância.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir usa threads e `SyncLock`. Contanto que a instrução de `SyncLock` esteja presente, o bloco de instrução é uma seção crítica e `balance` nunca se torna um número negativo. Você pode comentar as instruções `SyncLock` e `End SyncLock` para ver o efeito de sair da palavra-chave `SyncLock`.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Comentários  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Visão geral dos primitivos de sincronização](../../../standard/threading/overview-of-synchronization-primitives.md)
