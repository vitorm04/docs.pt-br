---
title: Acesso a arquivos assíncronos (C#)
description: Saiba como usar o recurso assíncrono para acessar arquivos em C#. Você pode chamar métodos assíncronos sem usar retornos de chamada ou dividir seu código entre os métodos.
ms.date: 08/19/2020
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 9a8db6004e8fff2cb39f0c350b403b56ea619e54
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812036"
---
# <a name="asynchronous-file-access-c"></a>Acesso a arquivos assíncronos (C#)

Você pode usar o recurso async para acessar arquivos. Usando o recurso async, você pode chamar os métodos assíncronos sem usar retornos de chamada ou dividir seu código em vários métodos ou expressões lambda. Para tornar síncrono um código assíncrono, basta chamar um método assíncrono em vez de um método síncrono e adicionar algumas palavras-chave ao código.

Você pode considerar seguintes motivos para adicionar a assincronia às chamadas de acesso ao arquivo:

> [!div class="checklist"]
>
> - A assincronia torna os aplicativos de interface do usuário mais responsivos porque o thread de interface do usuário que inicia a operação pode executar outro trabalho. Se o thread de interface do usuário precisar executar o código que leva muito tempo (por exemplo, mais de 50 milissegundos), a interface do usuário poderá congelar até que a E/S seja concluída e o thread da interface do usuário possa processar entradas do mouse e do teclado e outros eventos.
> - A assincronia melhora a escalabilidade do ASP.NET e outros aplicativos baseados em servidor reduzindo a necessidade de threads. Se o aplicativo usar um thread dedicado por resposta e mil solicitações forem tratadas simultaneamente, serão necessários mil threads. As operações assíncronas geralmente não precisam usar um thread durante a espera. Elas podem usar o thread de conclusão de E/S existente rapidamente no final.
> - A latência de uma operação de acesso de arquivo pode ser muito baixa nas condições atuais, mas a latência pode aumentar consideravelmente no futuro. Por exemplo, um arquivo pode ser movido para um servidor que está do outro lado do mundo.
> - A sobrecarga adicional de usar o recurso async é pequena.
> - As tarefas assíncronas podem facilmente ser executadas em paralelo.

## <a name="use-appropriate-classes"></a>Usar classes apropriadas

Os exemplos simples neste tópico demonstram <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> e <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType> . Para controle finito sobre as operações de e/s de arquivo, use a <xref:System.IO.FileStream> classe, que tem uma opção que faz com que a e/s assíncrona ocorra no nível do sistema operacional. Usando essa opção, você pode evitar o bloqueio de um thread de pool de threads em muitos casos. Para habilitar essa opção, você deve especificar o argumento `useAsync=true` ou `options=FileOptions.Asynchronous` na chamada do construtor.

Você não pode usar essa opção com <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> se as abrir diretamente, especificando um caminho de arquivo. No entanto, você poderá usar essa opção se fornecer um <xref:System.IO.Stream> que a classe <xref:System.IO.FileStream> abriu. As chamadas assíncronas são mais rápidas em aplicativos de interface do usuário, mesmo que um thread do pool de threads seja bloqueado, pois o thread da interface do usuário não é bloqueado durante

## <a name="write-text"></a>Gravar texto

Os exemplos a seguir gravam o texto em um arquivo. A cada instrução await, o método sai imediatamente. Quando o arquivo de E/S for concluído, o método continuará na instrução após a instrução await. O modificador assíncrono está na definição de métodos que usam a instrução Await.

### <a name="simple-example"></a>Exemplo simples

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleWrite":::

### <a name="finite-control-example"></a>Exemplo de controle finito

:::code language="csharp" source="snippets/file-access/Program.cs" id="WriteText":::

O exemplo original tem a instrução `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, que é uma contração das duas instruções a seguir:

```csharp
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
await theTask;
```

A primeira instrução retorna uma tarefa e faz com que o processamento do arquivo seja iniciado. A segunda instrução com o await faz com que o método saia imediatamente e retorne uma tarefa diferente. Quando o processamento do arquivo é concluído posteriormente, a execução retorna para a instrução após a await.

## <a name="read-text"></a>Ler texto

Os exemplos a seguir lêem o texto de um arquivo.

### <a name="simple-example"></a>Exemplo simples

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleRead":::

### <a name="finite-control-example"></a>Exemplo de controle finito

O texto é armazenado em buffer e, nesse caso, colocado em um <xref:System.Text.StringBuilder>. Diferentemente do exemplo anterior, a avaliação de await produz um valor. O <xref:System.IO.Stream.ReadAsync%2A> método retorna um <xref:System.Threading.Tasks.Task> \<<xref:System.Int32>>, de modo que a avaliação do Await produz um `Int32` valor `numRead` após a conclusão da operação. Para obter mais informações, consulte [Tipos de retorno assíncronos (C#)](async-return-types.md).

:::code language="csharp" source="snippets/file-access/Program.cs" id="ReadText":::

## <a name="parallel-asynchronous-io"></a>E/s assíncrona paralela

Os exemplos a seguir demonstram o processamento paralelo com a gravação de 10 arquivos de texto.

### <a name="simple-example"></a>Exemplo simples

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleParallelWrite":::

### <a name="finite-control-example"></a>Exemplo de controle finito

Para cada arquivo, o método <xref:System.IO.Stream.WriteAsync%2A> retorna uma tarefa que é então adicionada a uma lista de tarefas. A instrução `await Task.WhenAll(tasks);` sai do método e retoma no método quando o processamento do arquivo é concluído para todas as tarefas.

O exemplo fecha todas as instâncias de <xref:System.IO.FileStream> em um bloco `finally` após as tarefas serem concluídas. Se cada `FileStream` foi criado em uma instrução `using`, o `FileStream` pode ter sido descartado antes de a tarefa ter sido concluída.

Qualquer aumento de desempenho é quase totalmente o processamento paralelo e não o processamento assíncrono. As vantagens da assincronia são que ele não liga vários threads e que ele não vincula o thread da interface do usuário.

:::code language="csharp" source="snippets/file-access/Program.cs" id="ParallelWriteText":::

Ao usar os métodos <xref:System.IO.Stream.WriteAsync%2A> e <xref:System.IO.Stream.ReadAsync%2A>, você pode especificar um <xref:System.Threading.CancellationToken>, que pode ser usado para cancelar o fluxo intermediário da operação. Para saber mais, confira [Cancelamento em threads gerenciados](../../../../standard/threading/cancellation-in-managed-threads.md).

## <a name="see-also"></a>Confira também

- [Programação assíncrona com async e await (C#)](index.md)
- [Tipos de retorno assíncrono (C#)](async-return-types.md)
