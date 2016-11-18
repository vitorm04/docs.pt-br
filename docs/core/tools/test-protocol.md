---
title: "Protocolo de comunicação de teste da CLI do .NET Core"
description: "Protocolo de comunicação de teste da CLI do .NET Core"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 88cba792-3640-41de-b55d-00f575e9d5e2
translationtype: Human Translation
ms.sourcegitcommit: 81e7604f0a646e5de9c2ed35ff3b6ef6d7fb2e71
ms.openlocfilehash: beab195d283fcfcdc454a29498d27bcd290b66c1

---

#<a name="net-core-cli-test-communication-protocol"></a>Protocolo de comunicação de teste da CLI do .NET Core

## <a name="introduction"></a>Introdução
Sempre que você passar uma porta para o teste dotnet, o comando será executado no tempo de design. Isso significa que esse teste dotnet conectará a essa porta usando TCP e trocará um conjunto de mensagens estabelecida com qualquer outra coisa que estiver conectada a essa porta. Quando isso acontece, o executor também recebe uma nova porta que o teste dotnet usará para se comunicar com ele. O motivo pelo qual o executor também usa TCP para se comunicar com o teste dotnet é porque no modo design não é suficiente apenas gerar os resultados para o console. O comando precisa enviar as mensagens de estrutura do adaptador que contém os resultados da execução do teste.

### <a name="communication-protocol-at-design-time"></a>Protocolo de comunicação no tempo de design.

1. Como no tempo de design o teste dotnet se conecta a uma porta quando é iniciado, o adaptador precisa estar escutando essa porta, caso contrário o teste dotnet falhará. Deixamos isso desta forma para que o adaptador possa reservar todas as portas necessárias associando e escutando-as antes que o teste dotnet fosse executado e tentasse obter portas para o executor.
2. Uma vez iniciado o teste dotnet, ele envia uma mensagem TestSession.Connected ao adaptador indicando que ele está pronto para receber mensagens.
3. É possível enviar uma mensagem de [verificação de versão](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/ProtocolVersionMessage.cs) opcional com a versão do adaptador do protocolo nela. O teste dotnet enviará de volta a versão do protocolo à qual ele dá suporte.

Todas as mensagens têm o formato descrito aqui: [Message.cs](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/Message.cs). Os formatos de carga para cada mensagem são descritos em links para as classes usadas para serializar/desserializar as informações na descrição do protocolo.

#### <a name="test-execution"></a>Execução de Teste
![Execução de Teste](./media/test-protocol/dotnet-test-execute.png)

1. Após a verificação de versão opcional, o adaptador enviará um TestExecution.GetTestRunnerProcessStartInfo com os [testes](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs) que deseja executar dentro dele. O teste dotnet envia de volta um FileName e Arguments dentro de uma carga [TestStartInfo](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.DotNet.Tools.Test/TestStartInfo.cs) que o adaptador pode usar para iniciar o executor. No passado, podíamos enviar a lista de testes a serem executados como parte do argumento, mas a verdade é que com isso ultrapassávamos o limite de tamanho da linha de comando para alguns projetos de teste.
  1. Como parte dos argumentos, enviaremos uma porta à qual o executor deve se conectar e para executar testes,um sinalizador --wait-command, que indica que o executor deve se conectar à porta e aguardar os comandos em vez de prosseguir e executar os testes.
2. Neste ponto, o adaptador pode iniciar o executor (e anexar a ele para depuração se optar por fazer isso).
3. Uma vez iniciado o executor, ele envia uma mensagem TestRunner.WaitCommand para o teste dotnet que indica que ele está pronto para receber comandos, quando então o teste dotnet envia um TestRunner.Execute com a lista de [testes](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs) a ser executados. Isso ignora o limite de tamanho da linha de comando descrito acima.
4. O executor de teste dotnet envia (e transmite para o adaptador) um TestExecution.TestStarted para cada teste, pois eles começam com as informações de [teste](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Test.cs) dentro dele.
5. O executor também envia para o teste dotnet (e encaminha para o adaptador) um TestExecution.TestResult para cada teste com o [resultado individual](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/TestResult.cs) do teste.
6. Depois de concluir todos os testes, o executor envia uma mensagem TestRunner.Completed para o teste dotnet, a qual o teste dotnet envia como TestExecution.Completed para o adaptador.
7. Quando o adaptador tiver concluído, ele envia para o teste dotnet um TestSession.Terminate que fará com que o teste dotnet seja desligado.

#### <a name="test-discovery"></a>Descoberta de teste
![Descoberta de teste](./media/test-protocol/dotnet-test-discover.png)

1. Após a verificação de versão opcional, o adaptador envia uma mensagem TestDiscovery.Start. Como nesse caso o adaptador não precisa anexar ao processo, o teste dotnet iniciará o próprio executor. Além disso, visto que não há nenhuma lista longa de argumentos a serem passados para o executor, nenhum sinalizador --wait-command é necessário para ser passado para o executor. O teste dotnet apenas passa um argumento --list para o executor, o que significa que o executor não deve executar os testes, apenas listá-los.
2. O executor envia para o teste dotnet (e transmite para o adaptador) um TestDiscovery.TestFound para cada [teste](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Test.cs) encontrado.
3. Depois que todos os testes foram descobertos, o executor envia uma mensagem TestRunner.Completed para o teste dotnet, a qual o teste dotnet envia como TestDiscovery.Completed para o adaptador.
4. Quando o adaptador tiver concluído, ele envia para o teste dotnet um TestSession.Terminate que fará com que o teste dotnet seja desligado.


<!--HONumber=Nov16_HO3-->


