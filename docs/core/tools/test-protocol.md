---
title: "Protocolo de comunicação de teste da CLI do .NET Core | Microsoft Docs"
description: "Protocolo de comunicação de teste da CLI do .NET Core"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88cba792-3640-41de-b55d-00f575e9d5e2
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 83555650a5a3ce9ed28d329aa82f5ead75e2d9cb

---

#<a name="net-core-cli-test-communication-protocol"></a>Protocolo de comunicação de teste da CLI do .NET Core

> [!WARNING]
> Este tópico se aplica à Visualização 2 das Ferramentas do .NET Core. Para a documentação de Ferramentas do .NET Core RC4, consulte a seção [Ferramentas de interface de linha de comando do .NET Core (Ferramentas do .NET Core RC4)](../preview3/tools/index.md).

## <a name="introduction"></a>Introdução
Sempre que você passar uma porta para o teste dotnet, o comando será executado no tempo de design. Isso significa que `dotnet test` conectará a essa porta usando TCP e trocará um conjunto de mensagens estabelecido com qualquer outra coisa que estiver conectada a essa porta. Quando isso acontece, o executor também recebe uma nova porta que `dotnet test` usará para se comunicar com ele. O motivo pelo qual o executor também usa TCP para se comunicar com `dotnet test` é porque no modo de design não é suficiente apenas gerar os resultados para o console. O comando precisa enviar as mensagens de estrutura do adaptador que contém os resultados da execução do teste.

### <a name="communication-protocol-at-design-time"></a>Protocolo de comunicação no tempo de design.

1. Como no tempo de design o `dotnet test` se conecta a uma porta quando é iniciado, o adaptador precisa estar escutando essa porta, caso contrário o `dotnet test` falhará. Deixamos isso desta forma para que o adaptador possa reservar todas as portas necessárias associando e escutando-as antes que o `dotnet test` fosse executado e tentasse obter portas para o executor.
2. Uma vez iniciado o `dotnet test`, ele envia uma mensagem TestSession.Connected ao adaptador indicando que ele está pronto para receber mensagens.
3. É possível enviar uma mensagem de [verificação de versão](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/ProtocolVersionMessage.cs) opcional com a versão do adaptador do protocolo nela. O `dotnet test` enviará de volta a versão do protocolo à qual ele dá suporte.

Todas as mensagens têm o formato descrito aqui: [Message.cs](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/Message.cs). Os formatos de carga para cada mensagem são descritos em links para as classes usadas para serializar/desserializar as informações na descrição do protocolo.

#### <a name="test-execution"></a>Execução de Teste
![Execução de Teste](./media/test-protocol/dotnet-test-execute.png)

1. Após a verificação de versão opcional, o adaptador enviará um TestExecution.GetTestRunnerProcessStartInfo com os [testes](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs) que deseja executar dentro dele. O `dotnet test` envia de volta um FileName e Arguments dentro de uma carga [TestStartInfo](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/dotnet/commands/dotnet-test/TestStartInfo.cs) que o adaptador pode usar para iniciar o executor. No passado, podíamos enviar a lista de testes a serem executados como parte do argumento, mas a verdade é que com isso ultrapassávamos o limite de tamanho da linha de comando para alguns projetos de teste.
  1. Como parte dos argumentos, enviaremos uma porta à qual o executor deve se conectar e para executar testes,um sinalizador --wait-command, que indica que o executor deve se conectar à porta e aguardar os comandos em vez de prosseguir e executar os testes.
2. Neste ponto, o adaptador pode iniciar o executor (e anexar a ele para depuração se optar por fazer isso).
3. Uma vez iniciado o executor, ele envia uma mensagem TestRunner.WaitCommand para o `dotnet test` que indica que ele está pronto para receber comandos, quando então o `dotnet test` envia um TestRunner.Execute com a lista de [testes](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs) que serão executados. Isso ignora o limite de tamanho da linha de comando descrito acima.
4. O executor envia (e transmite para o adaptador) um TestExecution.TestStarted ao `dotnet test` para cada teste, pois eles começam com as informações de [teste](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Test.cs) dentro dele.
5. O executor também envia para o `dotnet test` (e encaminha para o adaptador) um TestExecution.TestResult para cada teste com o [resultado individual](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/TestResult.cs) do teste.
6. Depois de concluir todos os testes, o executor envia uma mensagem TestRunner.Completed para o teste dotnet, o qual o `dotnet test` envia como TestExecution.Completed para o adaptador.
7. Quando o adaptador tiver concluído, ele envia para o `dotnet test` um TestSession.Terminate que fará com que o `dotnet test` seja desligado.

#### <a name="test-discovery"></a>Descoberta de teste
![Descoberta de teste](./media/test-protocol/dotnet-test-discover.png)

1. Após a verificação de versão opcional, o adaptador envia uma mensagem TestDiscovery.Start. Como nesse caso o adaptador não precisa anexar ao processo, o `dotnet test` iniciará o próprio executor. Além disso, visto que não há nenhuma lista longa de argumentos a serem passados para o executor, nenhum sinalizador --wait-command é necessário para ser passado para o executor. O `dotnet test` apenas passa um argumento --list para o executor, o que significa que o executor não deve executar os testes, apenas listá-los.
2. O executor envia para o `dotnet test` (e transmite para o adaptador) um TestDiscovery.TestFound para cada [teste](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Test.cs) encontrado.
3. Depois que todos os testes foram descobertos, o executor envia uma mensagem TestRunner.Completed para o teste dotnet, o qual o `dotnet test` envia como TestDiscovery.Completed para o adaptador.
4. Quando o adaptador tiver concluído, ele envia para o `dotnet test` um TestSession.Terminate que fará com que o `dotnet test` seja desligado.



<!--HONumber=Feb17_HO2-->


